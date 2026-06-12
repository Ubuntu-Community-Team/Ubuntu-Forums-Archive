---
title: "external hard drive problem"
date: 2008-10-16
forum: Hardware
---

### Post by gerreth on 2008-10-16
Hi,

A few hours ago I installed ubuntu server 8.04.
Because of the few gigabytes remaining on my laptop, i decided to install it on my external hard drive.
The installation was a succes and i am able to boot from my external HD.

One problem. when I launch windows and connect the HD (usb), my computer doesnt recognize the HD. Is their a way to change this?


Thx,

Gerreth

---

### Post by az on 2008-10-16
Microsoft is unwilling to provide support for ext2/3 filesystems.  Fortunately, you can install a driver in windows which will allow Windows to see linux file systems:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

