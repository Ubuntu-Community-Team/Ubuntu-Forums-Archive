---
title: "xdvi looks bad, hyperlinks don't work."
date: 2005-12-04
forum: General Help
---

### Post by shreevatsa on 2005-12-04
Whenever I start xdvi, it is displayed with black characters on a grey/dusty background, which looks very bad. I *can* get it to look better by invoking it as "xdvi -bg white <filename>", but that changes only the actual region where the file is displayed, the menu area still looks bad. Does anyone know how I can fix this? It's probably something simple, like adding some lines in .Xdefaults or something, but I don't know. I've tried "apt-get install --reinstall xdvi", but it has no effect.

Also, when I include hyperlinks in my LaTeX file (with hyperref) and convert it to a dvi file, I don't see any hyperlinks. I read somewhere that xdvi supports hyperlinks, so why is this? I can get the links to work fine if I use pdflatex instead, or even first convert it to dvi and then use dvipdf on it.

---

### Post by Leif on 2005-12-04
I don't know the source of your problems, but I can recommend that you use kdvi instead, which is pretty good.

---

