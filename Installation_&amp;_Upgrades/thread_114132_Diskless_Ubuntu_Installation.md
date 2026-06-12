---
title: "Diskless Ubuntu Installation"
date: 2006-01-07
forum: Installation &amp; Upgrades
---

### Post by zappa86 on 2006-01-07
Hi. Does anyone know if its possible to have a diskless installation of ubuntu. The reason that I ask is that when I go back to school. I'm going to need to help my prof install ubuntu on many computers. And to configure each one the exact same many times would take lots of time. Therefore I ask if anyone knows how to do a diskless install. I've heard names such as PXE thrown around but i'm not sure what I need to do. Thanks.

---

### Post by aysiu on 2006-01-07
Do all these computers have the same specifications (i.e., the hardware is the same)?

---

### Post by zappa86 on 2006-01-07
yeah. all the hardware will be the same. (dont know what exactly but I know it is all the same)

---

### Post by aysiu on 2006-01-07
Try [PartImage](http://www.partimage.org/)

Install Ubuntu exactly as you want it on one computer.
Use a live CD, PartImage, and an external hard drive, and copy that partition image over to each of the other computers...

---

### Post by zappa86 on 2006-01-08
thats a good idea. I will remember that. But I really would like to know how to do some PXE booting of ubuntu. I found an old tutorial for debian however many things arnt the same and what i was able to hack up did not work.

---

### Post by McLogic on 2006-01-13
A friend of mine has a cheap hotel in Columbia. He has a bunch of P-2 & P-3 computers but not enough hard drives. They all have the minmum RAM for Ubuntu (128 mb or more). Most will be on the 100/T network, but some may have to be on the 802.11g network. 

If the main computer for the hotel is a fast Athlon with a 350GB disk (enough space for a lot of images), could I get them to all network boot?

This is the only thing I have found for network booting Ubuntu:
[http://www.mythtv.org/docs/mythtv-HOWTO-24.html#ss24.4]("http://www.mythtv.org/docs/mythtv-HOWTO-24.html#ss24.4")

---

