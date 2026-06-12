---
title: "force Mesa instead of DRI R300...?"
date: 2009-11-01
forum: Hardware
---

### Post by jinny on 2009-11-01
Hi, does anyone know how I can force Ubuntu to use **Mesa** as **OpenGL vendor string** instead of DRI R300?

The problem is that if I boot with **Ubuntu 9.10, kernel 2.6.31-14** flash works very slowly since I think my graphic card doesn't use the appropriate drivers... while if I boot with **Ubuntu 9.10, kernel 2.6.28-16** it works much better.
This is what I get if I use **glxinfo** :
**---kernel 2.6.31-14---**
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: DRI R300 Project
**---kernel 2.6.28-16---**
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa

Thanks!!

---

### Post by jinny on 2009-11-01
ok...i was able to change it by tweeking the xorg.conf but flash is still running slow... any suggestions? :(

---

