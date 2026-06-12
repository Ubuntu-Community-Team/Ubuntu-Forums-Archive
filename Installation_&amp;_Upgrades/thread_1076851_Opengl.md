---
title: "Opengl"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by anayisse on 2009-02-21
Hi!

If I can visualize videos properly, doest it mean that I have OPenGL installed in my linux, I'm using ubuntu 8.04 LTS ?

Thank you

---

### Post by cariboo on 2009-02-21
Open a Applications-->Accessories-->termianl and type:

```
glxgears
```

If you see three spinning gears you have opengl installed.

Jim

---

### Post by anayisse on 2009-02-21
thank you very much I can see them, but I have a question please :

if am compiling software from source, do I need development libraries too for openGL ? how should I recognize the good ones ?

for example I got this error message :

/usr/bin/ld: cannot find -lXmu
.........
include/G4OpenGLXViewer.hh:43:29: error: X11/Xmu/StdCmap.h: No such file or directory
Making dependency for file src/G4OpenGLStoredXmViewer.cc ...
........
g++ -shared -Wl,-soname,libGX11.so -m32 -O2 -o lib/libGX11.so x11/src/GX11Gui.o x11/src/Rotated.o x11/src/TGX11.o x11/src/gifdecode.o x11/src/gifencode.o x11/src/gifquantize.o x11/src/G__X11.o -lXpm -lXext -lX11 -lXft
/usr/bin/ld: cannot find -lXft
collect2: ld returned 1 exit status
make: *** [lib/libGX11.so] Error 1
.....

what librairies should I unstall to get my software compiled ? thank you very much ?

---

