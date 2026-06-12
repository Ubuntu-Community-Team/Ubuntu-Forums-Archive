---
title: "Installation on Shuttle K4500"
date: 2008-12-06
forum: Installation &amp; Upgrades
---

### Post by dkirsche on 2008-12-06
I am trying to install ubuntu 8.10 on a shuttle k4500. It can boot from a usb drive, but does not have a cdrom drive. I downloaded the 8.10 ISO, and used UNetbootin for windows to write all of the data to my usb flash drive. The system successfully booted to my flash drive and successfully installed Ubuntu. 

However, when I restarted my computer after the installation I get an error "DISK BOOT FAILURE, INSTERT SYSTEM DISK AND PRESS ENTER." This is my third time attempting to install ubuntu. and this happens everytime. I've made sure that the HD has three partitions: one is bootable and mounted with "/", the other is mounted with "/home" and the other is a swap drive.

Does anyone know what I am doing wrong? Is it possible that it is installing ubuntu on my flash drive instead of my HD somehow?

---

### Post by adaptr on 2008-12-06
It probably decided to install the boot loader (GRUB) on the USB stick - which you then removed...
You need to power up the USB stick again, open a terminal, and install GRUB on the HD instead.
There's plenty of documentation on how to do that.

---

