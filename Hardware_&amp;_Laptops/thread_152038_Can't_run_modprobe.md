---
title: "Can't run modprobe"
date: 2006-03-29
forum: Hardware &amp; Laptops
---

### Post by muu on 2006-03-29
I am trying to run modprobe to add a kernel module

> sudo /sbin/modprobe usbnet

Kernel requires old modprobe, but couldn't run /sbin/modprobe.modutils: no such file or directory

I have loaded the module-init-tools package for ubuntu, but no change.

Please help!

---

### Post by Titus A Duxass on 2006-03-29
Try:
sudo modprobe usbnet

I never use /sbin/modprobe only modprobe

---

