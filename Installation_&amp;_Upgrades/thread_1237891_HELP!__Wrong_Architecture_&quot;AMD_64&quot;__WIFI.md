---
title: "HELP!  Wrong Architecture &quot;AMD 64&quot;  WIFI not Working"
date: 2009-08-11
forum: Installation &amp; Upgrades
---

### Post by brhokla on 2009-08-11
Hi,
I have a Gateway LT3103u series netbook that runs 2 gigs ram and a 250 gig HD.  It uses an AMD Athlon64 and has the Atheros AR9285 wireless network adapter.  

I installed ubuntu on the computer and like all other users I can't get the WiFi to work.  I am sure I installed the 64 bit version of the OS as the computer is a 64 bit processor and it is running great.  I have tried installing the packets as recommended but when I try it tells me WRONG ARCHITECTURE "AMD64"  and I can't install the packets like I need to in order to get the wifi to work.  How do I tell which version 32 bit or 64 bit I have installed so I can verify that I am using a 64bit version of jaunty, my version of Jaunty is 9.04, Kernel 2.6.28-11-generic but I don't see anything saying its 64bit.  I have tried installing

linux-image-2.6.28-13-generic
linux-backports-modules-2.6.28-13-generic
linux-backports-modules-jaunty-generic
linux-backports-modules-jaunty

All these are showing to be the amd64 download version...


I am having to do this off a USB drive as I can only access the web on the computer booted in windows vista.  Thanks for any help....

---

### Post by Moop on 2009-08-11
You can run ```
uname -a
``` in a terminal and if it says x86_64 you have 64 bit. 

It might be that the driver you're trying to install is 32 bit and you would need some libs to make it work.

---

### Post by brhokla on 2009-08-11
It says linux ubuntu 2.6.28-11-generic #42 - ubuntu smp utc 2009 i686

---

### Post by Moop on 2009-08-11
You have 32 bit installed.

---

