---
title: "Compiling a GTK program"
date: 2008-07-21
forum: General Help
---

### Post by dacium on 2008-07-21
I have programmed all my programs in GTK+ so I can switch operating systems easily.

On Windows XP I use msys with mingw and gtk+-bundle-2.12.9 installed to build my programs with the command line:

gcc -Wall foo.c -o foo.exe `pkg-config --cflags gtk+-2.0` `pkg-config --libs gtk+-2.0` -mwindows

What is the eqivalent command line in Ubuntu and do I have to setup a GTK+ package first and how? Thanks for any help. I can't seem to get gcc to link/join/use GTK libraries etc.

---

### Post by SilkMonster0 on 2008-07-21
```
gcc `pkg-config --libs --cflags gtk+-2.0` file.c -o program
```

Hope this helps you

---

