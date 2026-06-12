---
title: "compile newmat c++"
date: 2009-03-11
forum: Installation &amp; Upgrades
---

### Post by yo_misma5 on 2009-03-11
Hi:
i am new, and i have downloaded the package newmat to be able to multiply matrix, from the authors site [http://www.robertnz.net/nm10.htm](http://www.robertnz.net/nm10.htm), and i follow the instructions and i do  make -f nm_cc.mak, but is says
rm -f tmt.cxx
ln tmt.cpp tmt.cxx  
CC -O2 -c tmt.cxx
make: CC: No se encontró el programa
so how should i do to compile all and then use it in my program?thank you!

---

### Post by Partyboi2 on 2009-03-11
Have you got the build-essential package installed?
```
sudo apt-get install build-essential
```

---

### Post by yo_misma5 on 2009-03-11
HI:
i have tried but i get this message,and i haveno here my linux cd installation(i am in belgium and i have it in spain)

Cambio de medio: Por favor inserte el disco etiquetado
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
en la unidad '/cdrom/' y presione Intro
what should i do?

---

### Post by Partyboi2 on 2009-03-11
If your computer is connected to the Internet then open Software Sources (System>Admin>Software Sources) and on the first tab untick  the cdrom box under "Installable from CD-ROM/DVD" then close Software Sources and try installing build-essential again.

---

### Post by yo_misma5 on 2009-03-13
HI again!
i have done that succesfully, but i keep getting the same error when trying to compile newmat
ana@ana-laptop:~/newmat10_original$ make -f nm_cc.mak
rm -f tmt.cxx
ln tmt.cpp tmt.cxx  
CC -O2 -c tmt.cxx
make: CC: No se encontró el programa
make: *** [tmt.o] Error 127

---

### Post by Partyboi2 on 2009-03-14
Try editing the /newmat10/nm_cc.mak file and remove the first line

```
CXX = CC
``` then try 
```
make -f nm_cc.mak
```

---

