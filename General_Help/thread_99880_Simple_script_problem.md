---
title: "Simple script problem"
date: 2005-12-06
forum: General Help
---

### Post by WebDrake on 2005-12-06
I have a simple script set up on my system to make easier the LaTeX commands necessary to compile a document into a PDF.  Here it is:

```

rm *.aux
rm *.bbl
rm *.blg
rm *.log
rm *.toc
rm *.idx
latex PhD.tex
bibtex bu1
bibtex bu2
bibtex bu3
bibtex bu4
bibtex bu5
bibtex bu6
bibtex bu7
latex PhD.tex
latex PhD.tex
dvips -t a4 PhD.dvi
ps2pdf PhD.ps
acroread PhD.pdf &

```

However, not all the commands in the script work: the rm commands, the dvips command and the ps2pdf command all fail to find the files they are supposed to operate on.  But this is only within the script: if typed directly by me into the command line, each of these commands works.

:confused:

---

