---
title: "LogiTech Quickcam pro 5000"
date: 2006-05-08
forum: Hardware &amp; Laptops
---

### Post by hakune on 2006-05-08
Hello all i'm trying to get my webcam working with breezy
i'm using the uvc cvs driver but when i do a make i get the following
```
hakune@Hakune:~/logi$ make
Building USB Video Class driver...
make[1]: Entering directory `/lib/modules/2.6.12-10-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.12-10-386/build'
make: *** [uvcvideo] Error 2

```
and it has me stumped 
anyone have a idea ?

---

### Post by silentb on 2006-05-09
what are the contents of /lib/modules/2.6.12-10-386/build/Makefile ?

for a tutorial for "make" look here:
[http://www.ijon.de/comp/tutorials/makefile.html](http://www.ijon.de/comp/tutorials/makefile.html)

this might give you a rough idea of compilation.

---

### Post by hakune on 2006-05-10
currently /lib/modules/2.6.12-10-386/build is empty
i have the latest kernel-headers installed but still no go

---

### Post by hakune on 2006-05-10
nobody ?

---

### Post by Sef on 2006-05-11
Here's one site:

[http://linux-uvc.berlios.de/]("http://linux-uvc.berlios.de/")

It has a link to here:

[http://developer.berlios.de/projects/linux-uvc]("http://developer.berlios.de/projects/linux-uvc")

Note: The driver is still alpha, i.e., it is not stable.  You may or may not experience problems.

---

### Post by hakune on 2006-05-11
Those are the drivers i'm currently trying to build >_<
and that's the make error i get 
i have all the deps installed 
just don't get it

---

### Post by hakune on 2006-05-12
never mind fixed

---

