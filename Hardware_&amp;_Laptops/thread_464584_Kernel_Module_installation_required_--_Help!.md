---
title: "Kernel Module installation required -- Help!"
date: 2007-06-04
forum: Hardware &amp; Laptops
---

### Post by Pypasaur on 2007-06-04
Installed Ubuntu Feisty on my [COLOR="black"]** Pepper Pad 3 **[/COLOR] ( [http://www.pepper.com/](http://www.pepper.com/) ). 

The PepperPad3's split keyboard requires a special driver that must be **compiled and installed** as a kernel module (.ko file).

This opensource (GPL'd) driver has been compiled and deployed in [**Pepper Linux**]("http://www.pepper.com/software/") (Fedora Core 4 / kernel 2.6.12), but I'd like to compile it on Ubuntu Feisty. 

The driver source files reside in the Pepper Linux kernel source tree at  /kernel-2.6.12/drivers/input/keyboard/


[B]pad3_kypd.c
Kconfig
Makefile[/B]


1. How to compile these source files on Ubuntu ?

2. How to plug the finished (.ko) module into the Ubuntu Kernel ? 



I'd love to keep using Ubuntu on my PepperPad3. 
Thanks in Advance!

P.S. I've attached the driver source files from the Pepper Linux source tree at /kernel-2.6.12/drivers/input/keyboard/

Thank you! :KS

---

### Post by Pypasaur on 2007-06-05
Does anyone know a good step-by-step guide to compile kernel modules in Ubuntu ?

I'm trying to setup a kernel module development environment on my Feisty installation.
Please help!

---

