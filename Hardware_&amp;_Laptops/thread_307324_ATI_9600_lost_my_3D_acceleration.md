---
title: "ATI 9600 lost my 3D acceleration"
date: 2006-11-26
forum: Hardware &amp; Laptops
---

### Post by Arepie on 2006-11-26
Hello..

After i install edgy, my 3D and OpenGL is working automaticaly, and after i restart my pc, both of them dissapeared. At first, both of them aren't working i mean the "direct randering" and "3D acceleration" but, after added 

> Option		"BusType"	"PCI"

my OpenGL is running again. The problem is the 3D acceleration is not working. My xorg.conf can be found [here]("http://h3lp.madpage.com/Ubuntu/xorg.txt")

Please show me a good guide.. and this is some information
> 
:~$ glxinfo | grep vendor
libGL warning: 3D driver claims to not support visual 0x4b
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.
:~$ glxinfo | grep direct
libGL warning: 3D driver claims to not support visual 0x4b
direct rendering: Yes


Thanks..

---

### Post by happy-and-lost on 2006-11-26
The link in my sig tells you how to set up ATi cards in Edgy.

---

### Post by Arepie on 2006-11-26
im trying not to use fglrx driver..
im trying to use "ati", using aiglx..
i've tried both.. and aiglx is smoother than fglrx..
plese help

---

