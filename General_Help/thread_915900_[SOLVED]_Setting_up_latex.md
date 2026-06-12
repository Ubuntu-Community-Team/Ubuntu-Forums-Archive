---
title: "[SOLVED] Setting up latex"
date: 2008-09-10
forum: General Help
---

### Post by achelis on 2008-09-10
Hi

I've recently come to the conclusion that I'll benefit from starting to use Latex.

What I'd like to know is what I need to install in order to "compile" a latex document to i.e. pdf? (I'm not really bothered about which editor I'm using but will probably end up in emacs or texmaker.)

Any help appreciated.

---

### Post by unutbu on 2008-09-10
Start by installing texlive.
You may also want to install texlive-extra
To make a pdf file from a tex file try
```

pdftex file.tex
```

Or from emacs, just open file.tex and type C-c C-c  (two control-c's in a row).

---

