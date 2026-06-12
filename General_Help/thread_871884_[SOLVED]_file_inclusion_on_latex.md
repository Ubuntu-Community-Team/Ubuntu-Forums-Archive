---
title: "[SOLVED] file inclusion on latex"
date: 2008-07-27
forum: General Help
---

### Post by arkara on 2008-07-27
I am writing a latex document, but i need to include another pdf in it which is about 9 pages. does anyone know how to do that?

---

### Post by Azguz Bloodfist on 2008-07-27
Do you have the LaTeX source for this PDF? Otherwise I you can include a PDF in the same way as you include an image,  \includegraphics{file}. You will need the graphics or graphicx package for this: \usepackage{graphicx}

---

### Post by arkara on 2008-07-27
> **Azguz Bloodfist said:**
> Do you have the LaTeX source for this PDF? Otherwise I you can include a PDF in the same way as you include an image,  \includegraphics{file}. You will need the graphics or graphicx package for this: \usepackage{graphicx}

No i don't have the source, 
but i when i did that include graphics, i got only the first page and not
all the 9 pages.

---

### Post by hugmenot on 2008-07-27
The package you need is pdfpages.
[http://www.ctan.org/tex-archive/macros/latex/contrib/pdfpages/](http://www.ctan.org/tex-archive/macros/latex/contrib/pdfpages/)

---

### Post by arkara on 2008-07-27
> **hugmenot said:**
> The package you need is pdfpages.
[http://www.ctan.org/tex-archive/macros/latex/contrib/pdfpages/](http://www.ctan.org/tex-archive/macros/latex/contrib/pdfpages/)

thanks man.
I had found that package before, but i did not read the documentation
and therefore not use it right.

the command is for example..
```
\includepdf[pages={1-3}]{/path/to/file.pdf}
```

---

