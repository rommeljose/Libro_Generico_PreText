---
markdown: kramdown
theme: minima
---

## 🚀 PreTeXt:

El lenguaje de marcado y el sistema de preparación de documentos para crear la próxima generación de libros de texto. Y la generación posterior a esta.

### 📚 **Proyecto Genérico para PreTeXt-CLI 🚀✨**

Esta es una propuesta y ejemplo base con los requerimientos necesarios para editar un libro, publicación o algún documento genérico, con [**PreTeXt**](https://pretextbook.org/). Usando [**Codespace de GitHub**](https://docs.github.com/en/codespaces) y asociándolo a este repositorio, permite tener en la nube de GitHub todo lo necesario para la edición y publicación en diversos formatos: **LaTeX**, **PDF**, **HTML**, **EPUB**, **Jupyter Notebook**, **Braille**, entre otros.

👉 **Ejemplo en producción:** [Libro Web](https://rommeljose.github.io/Libro_Generico_PreText/titulo-libro.html)

<a href="https://rommeljose.github.io/Libro_Generico_PreText/titulo-libro.html">
    <img src="assets/imagenes/caratula.png" alt="Ejemplo de la salida genérica de las fuentes suministradas" width="200"/>
</a>


## 🚀 **¿Qué es PreTeXt?**

[**PreTeXt**](https://pretextbook.org/) es un lenguaje de marcado semántico que permite estructurar documentos académicos y técnicos de manera lógica. Captura la estructura de libros de texto y trabajos de investigación y facilita su conversión a múltiples formatos.

- **Formato de archivo:** `.ptx` o `.xml`.
- **Editor recomendado:** [**Visual Studio Code**](https://code.visualstudio.com/) con complementos para PreTeXt.

---

## 🛠️ **Instalación de PreTeXt en Ubuntu, WSL o Codespaces**

### 0️⃣ **Actualiza el índice de paquetes:**

```bash
sudo apt update
sudo apt install python3.12-venv
python3 -m venv --help
```

### 1️⃣ **Entorno Virtual Python (opcional pero recomendado)**

```bash
python3 -m venv editorial
source ./editorial/bin/activate
```

> ⚠️ **Verifique si tiene Python instalado:**  
> `$ python --version` o `$ python3 --version`

---

### 2️⃣ **Instalar PreTeXt-CLI**

Al momento (21/3/2025), la versión oficial de Pretext es: 2.15.0

```bash
pip install pretext
```

---

### 3️⃣ **Configuración Adicional (Opcional)**

Modifique para castellanizar el resultado PDF. EPUB, KINDLE y WEB.

Desde la raíz del repositorio:

```bash
cp ./otros_necesarios/es-ES.xml ~/.ptx/2.10.1/core/xsl/localizations/
```

---

## ⚙️ **Ajustes Opcionales para personalizar los Iconos en la parte inferior de la página Web**

Puedes personalizar los logos modificando la plantilla `pretext-html` en la instalación local `~\.ptx\2.10.1\core\xsl`:


### Personaliza con tu logo personal, comenta las siguientes secciones y sustituye con el código adecuado:

```xml
<!-- Comentado por RJCG -->
<!-- <xsl:template name="runestone-link">
    <a class="runestone-link" href="https://runestone.academy" title="Runestone Academy">
        <img class="logo" src="https://runestone.academy/runestone/static/images/RAIcon_cropped.png" alt="Runstone Academy logo"/>
    </a>
</xsl:template> -->


<xsl:template name="runestone-link">
    <a class="runestone-link" href="https://efemeridescumana.blogspot.com/" title="Academia de GeoHistoria del Estado Sucre">        
	<img class="logo" src="https://upload.wikimedia.org/wikipedia/commons/6/61/Logo_3_AGHES.jpg"  />  
	</a>

</xsl:template>

```
### Personaliza con el logo de tu Institución:
```xml
<!-- <xsl:template name="mathjax-link">
    <a class="mathjax-link" href="https://www.mathjax.org" title="MathJax">
        <img class="logo" src="https://www.mathjax.org/badge/badge-square-2.png" alt="MathJax logo"/>
    </a>
</xsl:template> -->

<xsl:template name="mathjax-link">
    <a class="mathjax-link" href="https://bit.ly/m/rommelcontreras" title="Pagina del Autor">
    <img class="logo" src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgdLU0qim6ueyYXDBgN5FRxXwoJKswnW41aeXSUDbPpUDGOlo7kmlzOYNreYGPsX_fMRhXiAV-fwfy0zJUySgyXOP9QrEPI83CkvCejk6DhhBm2k5C_FxKv1pHpKYC0ResNGR5sQJ1mUiZC/s800/que_puede_hacer_un_fisico_trasparente.png"  />
	</a>
</xsl:template>
```

---

## 📂 **Estructura del Proyecto**

```plaintext
📦 libro-pretext-generico
.
├── .devcontainer.json
├── .git
├── .github
├── .gitignore
├── .vscode
├── README.md
├── project.ptx
├── requirements.txt
├── codechat_config.yaml
├── assets
├── output
├── publication
└── source
```

---

## 📝 **Comandos Básicos de PreTeXt**

### ➡️ **Construir el libro en formato HTML:**
```bash
pretext build web
```

### ➡️ **Ver el libro en el navegador:**
```bash
pretext view web
```

### ➡️ **Desplegar en GitHub Pages:**
```bash
pretext deploy
```

📌 Nota:
Para generar salidas en otros formatos, en el manifiesto del proyecto [`project.ptx`](https://pretextbook.org/doc/guide/html/epub-5.html#epub-5-4) deben declararse las referencias sobre cómo y con qué construir esos formatos, a partir de Pretext 2.14.0. Verifique que el archivo `publication.ptx`, tenga la estructura recomendada
Ejemplo del archivo `project.ptx`:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- This  file was automatically generated by PreTeXt 2.13.4. -->
<!-- If you modify this file, PreTeXt will no longer automatically update it.-->

<!-- This file, the project manifest, provides the overall configuration for your PreTeXt project. To edit the content of your document, open `source/main.ptx`. See https://pretextbook.org/doc/guide/html/processing-CLI.html#cli-project-manifest. -->
<project ptx-version="2">
  <targets>
    <target name="web" format="html" />
    <target name="print" format="pdf"  latex-engine = "xelatex" />
    <target name="print2" format="pdf" latex-engine = "pdflatex" output-filename= "main2.pdf"/>
    <target name="latex" format="latex" />
    <target name="epub" format="epub" />
    <target name="kindle" format="kindle" />
    <target name="braille" format="braille" />

  </targets>
</project>
```
EPUB es el formato estándar para libros electrónicos. Los libros en formato EPUB se pueden leer mediante aplicaciones en una variedad de plataformas. Los dispositivos Kindle de Amazon utilizan un formato propietario que se deriva de EPUB.

---

## 📊 **Dependencias Adicionales para LaTeX**

### Instalar Paquetes Básicos:
```bash
sudo apt-get install texlive-latex-base
sudo apt-get install texlive-fonts-recommended
sudo apt-get install texlive-fonts-extra
sudo apt-get install texlive-science
sudo apt-get install texlive-latex-extra
```

## 📊 **Actualizando a nuevas versiones de Pretext**

### Siempre es conveniente mantener el sistema operativo actualizado, mantener `Actualiza el índice de paquetes`:

```bash
sudo apt update
```
### Actualiza la nueva versión, desde el entorno Virtual Python:

```bash
pip install pretext --upgrade
```

### Si no tiene `pip`, instalar con:

```bash
sudo apt install python3-pip
```

### Verificar la nueva instalación con:

```bash
pretext --version
```

> ⚠ **Recordatorio:**  
> No olvidar realizar nuevamente los Ajustes Opcionales para personaliza Pretext.


🛑 **Hasta aquí se explica la configuración funcional de [**PreTeXt**](https://pretextbook.org/)**, lo necesario para trabajar, por ejemplo, un libro de texto.

---


# Configuración de `XeLaTeX` en PreTeXt para el idioma español

## Introducción

Para que `XeLaTeX` maneje correctamente el **idioma español** en **PreTeXt**, es necesario asegurarse de que el paquete `polyglossia` esté correctamente configurado y de que se utilicen fuentes compatibles. 

`Polyglossia` es la alternativa a babel para `XeLaTeX` y maneja correctamente la separación de palabras en español
Para usar `XeLaTeX` es necesario instalar además de los Paquetes Básicos:

```bash
sudo apt install texlive-xetex
sudo apt install texlive-xetex texlive-lang-spanish
```

Verifica que `polyglossia` esté instalado ejecutando el siguiente comando:

```bash
kpsewhich polyglossia.sty
```

Luego de instalar `polyglossia`, se utiliza añadiendo las siguientes configuraciones en **`main.ptx`**, específicamente dentro de la sección `<docinfo>`. 


```bash
    
<!-- Para usar estas fuentes, ejecuta "pretext build print" para compilar con XeLaTeX -->

<latex-image-preamble>

    <!-- Cargar TikZ para gráficos -->
    \usepackage{tikz}

    <!-- Configuración de idioma con polyglossia -->
    \usepackage{polyglossia}
    \setmainlanguage{spanish}
    \setotherlanguage{english}

    <!-- Uso de fontspec para definir fuentes -->
    \usepackage{fontspec}

    <!-- Configurar la fuente principal (serif) -->
    \setmainfont[
        Path=/usr/share/fonts/opentype/cabin/,
        Extension=.otf,
        UprightFont=*-Regular,
        BoldFont=*-Bold,
        ItalicFont=*-Italic,
        BoldItalicFont=*-BoldItalic
    ]{Cabin}

    <!-- Configurar la fuente para títulos y secciones -->
    \setsansfont[
        Path=/usr/share/fonts/truetype/lato/,
        Extension=.ttf,
        UprightFont=Lato-Medium,
        BoldFont=Lato-Bold,
        ItalicFont=Lato-Italic,
        BoldItalicFont=Lato-BoldItalic
    ]{Lato}

    <!-- Configurar la fuente monoespaciada correctamente -->
    \setmonofont[
        Path=/usr/share/fonts/truetype/dejavu/,
        Extension=.ttf,
        UprightFont=DejaVuSansMono,
        BoldFont=DejaVuSansMono-Bold,
        ItalicFont=DejaVuSansMono-Oblique,
        BoldItalicFont=DejaVuSansMono-BoldOblique
    ]{DejaVu Sans Mono}

    <!-- Asegurar codificación UTF-8 -->
    \defaultfontfeatures{Ligatures=TeX,Mapping=tex-text}

    <!-- Corrección de nombres de capítulos y secciones en español -->
    \renewcommand{\chaptername}{Capítulo}
    \renewcommand{\contentsname}{Índice}
    \renewcommand{\figurename}{Figura}
    \renewcommand{\tablename}{Tabla}

</latex-image-preamble>
```

> ⚠ **Advertencia**  
> Antes de compilar con `XeLaTeX`, verifica que las fuentes necesarias (de tu preferencia) están instaladas en tu sistema ejecutando los siguientes comandos:
>
> ```bash
> fc-list | grep "Cabin"
> fc-list | grep "Lato"
> fc-list | grep "DejaVu"
> ```
>
> Si alguna de estas fuentes no aparece en la lista, es posible que necesites instalarlas manualmente o especificar una ruta correcta en la configuración de `fontspec`.

> 📌 Nota: El uso de otros fones de los muchos disponibles en `XeLaTeX`, se puede hacer quitando el comentario del ejemplo sugerido en el archivo `main.ptx`.

### Recursos Útiles:
- [**How To Install "texlive-latex-base" Package on Ubuntu**](https://zoomadmin.com/HowToInstall/UbuntuPackage/texlive-latex-base)  
- [**LaTeX: instalación TeXLive + Texmaker (Ubuntu)**](https://mecatronicauaslp.wordpress.com/2013/07/25/latex-instalacion-texlive-texmaker-ubuntu/)

---

## 📖 RELAX NG y PreTeXt
### El vocabulario de PreTeXt se define mediante un esquema [**RELAX NG**](https://pretextbook.org/doc/guide/html/schema-relaxng.html), un lenguaje de validación para XML.

Un esquema es un conjunto de patrones que describen cómo se pueden combinar los elementos de un lenguaje.

- ✅ **Especifica** la estructura y contenido del documento.
- 🔍 **Permite la validación** de documentos XML.
- ✍️ **Facilita la edición y conversión**, proporcionando una guía clara sobre elementos y atributos permitidos.



## 📚 **Principios de PreTeXt**

- Legible y escribible por humanos.  
- Compatible con múltiples formatos.  
- Respetuoso de las buenas prácticas editoriales.  
- Gratuito y de código abierto.  
- Enfocado en la accesibilidad y la experiencia del usuario.  
- Capacidad de exportación a formatos como LaTeX, HTML, PDF, EPUB, entre otros.

---

## 🎓 **Documentación Oficial**

- [Documentación de PreTeXt](https://pretextbook.org/doc/guide/html/index.html)
- [Repositorio de PreTeXt en GitHub](https://github.com/PreTeXtBook)
- [RELAX NG: A Simpler Schema Language for XML](https://books.xmlschemata.org/relaxng/relax-CHP-2.html)
---

## 🤝 **Contribuciones**

¡Las contribuciones son bienvenidas! Puedes abrir un **issue** o enviar un **pull request**.

---

## 📝 **Licencia**

Este proyecto está bajo la licencia **MIT**. Consulta el archivo `LICENSE` para más detalles.

---

## 🚀 **¡Únete a la Comunidad PreTeXt!**

- [Foro de PreTeXt](https://groups.google.com/forum/#!forum/pretext-support)
- [Chat en Zulip](https://pretext.zulipchat.com/)

---

