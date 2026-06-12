---
title: "Installing Visual Paradigm"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by DesignerX on 2009-06-23
I downloaded the free version of Visual Paradigm but when I try to run the installation file I get an error : "Lock assertion failed" on the libX11.so.6 file and the installation window won't work.

what can I do ?

thx

---

### Post by Mark Phelps on 2009-06-23
Are you running the installation as root?

If so, it may be that it can't run inside XWindows and you need to shell out to a console (Ctl-Alt-F2) and run it from there as root.

---

