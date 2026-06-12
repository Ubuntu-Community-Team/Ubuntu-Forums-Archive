---
title: "[SOLVED] Help need with latex and pgf"
date: 2008-11-24
forum: General Help
---

### Post by Despot Despondency on 2008-11-24
Hi, I've got texlive installed on my computer and I want to install pgf so I can do some graphics. I've managed to install pgf using aptitude but there seem to be library's missing. For example, if I have 

```

\usepackage{tikz}
\usetikzlibrary{arrows}

```

and everything is fine, but when I try 

```

\usepackage{tikz}
\usetikzlibrary{arrows, fit}

```

I get the error

```

[LaTeX] assignment1_answers.tex => assignment1_answers.dvi (/usr/localtexlive/2007/bin/latex)
[LaTeX] finished with exit status 127
./assignment1_answers.tex:5:I can't find file `pgflibrarytikzfit.code.tex'. \usetikzlibrary{arrows,fit}
/usr/local/texlive/2007/texmf-dist/tex/latex/tools/x.tex:33:. \batchmode \errmessage{}
[LaTeX] 2 errors, 0 warnings, 0 badboxes

```

Having a look around the files it seems that the fit library is missing. Does anyone know why this is the case? I'm assuming that it is because the version in the repositories is out of date?

I've tried installing from source, but without much luck. Apparently I just put the downloaded folder into /usr/local/share/texmf/tex/generic/pgf, which I've done but it doesn't work.

Does anyone use pgf? I would really appreciate some pointers on how to get it to work properly.

---

### Post by Despot Despondency on 2008-11-25
I managed to sort it out. It turns out that my version of texlive was out of date. I removed the 2007 version and installed the 2008 version  and everything seems to be working fine. It turns out that pgf comes with texlive so I didn't have install it separately.

---

### Post by wateenellende on 2008-12-18
How did you install the 2008 version ? Are there packages somewhere ?

---

