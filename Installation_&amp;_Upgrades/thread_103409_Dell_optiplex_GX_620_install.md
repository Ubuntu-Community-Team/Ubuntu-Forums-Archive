---
title: "Dell optiplex GX 620 install"
date: 2005-12-14
forum: Installation &amp; Upgrades
---

### Post by oswald-p on 2005-12-14
hi there,
For my work, I am trying to install ubuntu 5.10 on a DELL optiplex GX 620 computer.
the install process stop at the beginning of the "loading additionnal component" step... (12%, libc6-udeb). The error message says that there is a problem with de CD... BUT I performed a md5sum after downloading the iso (ok), burned the CD at low speed (4x) and tested the install process on my personnal computer (ok)... I burned the image on 3 different PC.... and I always have the same error...
It is the stanger bug I have ever seen... don't you?
is there a solution somwhere?

thanks

O-p

---

### Post by oswald-p on 2005-12-14
solved entering the install in expert mode and adding "-d1" in hdparm configuration.

O-p

---

