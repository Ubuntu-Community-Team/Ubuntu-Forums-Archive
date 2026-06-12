---
title: "elfclass"
date: 2008-11-22
forum: General Help
---

### Post by anv on 2008-11-22
I don't know what an earth this means, before I have used NVU webeditor without problems. now while using it under new 8.10 it gives error :

(nvu-bin:24530): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64


and becomes unstable. This is bit more serious problem because I use the software in my work.

---

### Post by Nepherte on 2008-11-22
It means you have a 64bit Ubuntu installation, while the program you want to use is a 32bit version and expects 32bit libraries.

---

### Post by anv on 2008-11-22
the software which I used were original bin package from old nvu website which works under 32/64 bit as earlier with, 64 bit 7.04-8.04. Even now it starts and works some but some functions not. but without causing more work it's partially resolved because I founded from the repositories the software "KompoZer" which is actually the same software.

[edit] after testing the repo version it does exactly same hmm...

---

