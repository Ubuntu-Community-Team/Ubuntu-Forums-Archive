---
title: "Laptop Installation Problem"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by HOMERZA on 2009-01-14
Hi All,

I am attempting a 8.10 install on a Fujitsu Siemens Amilo 1818.

It seems that it is possible to get Ubuntu installed on this laptop as searches in this forum show it has been done with 8.04.

I already have Vista installed and want to dual boot, but I can't even get that far. In fact I can't even get a Ubuntu Live to work.

It just seems to hang when starting either the Live or install options as well as the CD check facility.

The only thing that works is the memory test .

Is there a way to check that the CD is fine from inside Vista?

And has anybody experienced, and hopefully fixed, this type of problem?

When I tried to put XP on the machine a while ago, the sata drivers were missing. Could that be the problem?

Ta

---

### Post by Tim Sharitt on 2009-01-14
There may be a problem with the CD. First check the MD5 sum of the iso image (link:[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)) to make sure the image is good. If that checks out, try re-burning the CD at the lowest speed possible (usually 4x).

The reason for burning at low speed is because higher speed burning can cause slight errors. While undetectable on an audio cd, these small errors can play havoc on an install cd.

---

### Post by jojo21 on 2009-01-15
I have the exact same laptop. 8.04 works fine, but you'll have to use ndswrapper to get wireless working. I've upgraded to 8.10 a couple of days ago and I'm having some sound issues, eg when you plug in headphones, sound still comes from the speakers.

There's a comprehensive wiki on this laptop.

---

### Post by albinootje on 2009-01-15
> **HOMERZA said:**
> 
Is there a way to check that the CD is fine from inside Vista?


Check the md5sum of your cdrom (and cdrom image) with some md5sum check program.

The mdsums for Ubuntu 8.10 are here :
[http://releases.ubuntu.com/8.10/MD5SUMS](http://releases.ubuntu.com/8.10/MD5SUMS)

Also, burn the cdrom at a low cd burn speed!

---

