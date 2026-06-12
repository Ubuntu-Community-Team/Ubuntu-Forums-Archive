---
title: "Sony Vaio PCG GRT100"
date: 2007-11-04
forum: Hardware &amp; Laptops
---

### Post by bjjsperez on 2007-11-04
After successfully installing UBUNTU 7.10, I get the screen to choose OS (Ubuntu 7.10 generic, Ubuntu 7.10 Recov. mode, etc, WIndows XP), I choose Ubuntu 7.10 Generic.

It starts loading and the screen completely goes black and and does not do anything else.

Please help!!, does it have something to do with the NVIDIA Geoforce4 420 Go (sony) drivers?

Specs. for the laptop are:

2.66 Mhz Pentium 4
512 RAM
Microsoft WIndows XP Home Edition Version 2002
Service Pack 2.

I am new to Linux so tell me whats going on.

---

### Post by K.Mandla on 2008-07-11
Yup, you need to add this line to your xorg.conf, in the Monitor or Driver sections.
```
Option "UseDisplayDevice" "DFP"
```
The Nvidia 96xx drivers ignore the flat panel by default. That line redirects the output to the laptop screen. This works on the 440 too.

[http://kmandla.wordpress.com/2008/05/16/ubuntu-804-on-vaio-pcg-grt100/](http://kmandla.wordpress.com/2008/05/16/ubuntu-804-on-vaio-pcg-grt100/)

---

