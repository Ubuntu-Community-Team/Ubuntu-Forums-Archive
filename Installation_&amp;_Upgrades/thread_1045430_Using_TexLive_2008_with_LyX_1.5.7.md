---
title: "Using TexLive 2008 with LyX 1.5.7"
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by gmjs on 2009-01-20
Hi,

I've installed Qt4.3 from the Ubuntu repositories and have compiled LyX 1.5.7, in order to avoid the tex installation as I have already downloaded texlive.

Although LyX's "Tex Information" option lists all the LaTeX class files, LyX cannot produce any output as all classes are unavailable.

Also, the LaTeX command in a terminal window appears not to do anything:

```
[B]graham@asus:~$ latex
graham@asus:~$[/B] 

```

TexLive is installed and the binary path added to the PATH env variable.

Does anyone know what I am doing wrong?

Many thanks,

Graham

---

### Post by gmjs on 2009-01-20
Apologies for answering my own post.

I've reinstalled texlive and the latex command actually does something now!

I was installing it originally from an ISO file, mounted to /mnt.

This time, I copied all the files from the 'CD' to a folder and installed from there.

Yay.

---

