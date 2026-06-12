---
title: "bit level copy of a flash drive"
date: 2007-10-31
forum: Hardware &amp; Laptops
---

### Post by fusionisthefuture on 2007-10-31
hi, i was wondering if it's possible with ubuntu to create an exact duplicate image of a usb flash drive, using cp.  i dont really know what all the options i can use mean, all i know is that i want the computer to think it has two exactly identical thumb drives in it.  

any ideas?  
thanks
-arne

---

### Post by tgalati4 on 2007-11-01
I've successfully created copies of 4 GB Emphase, IDE Flash drives using the following:

sudo cp /dev/hda /dev/hdb

This was using Damn Small Linux which uses the 2.4.26 kernel.  Don't see why this wouldn't work in Ubuntu.

Make sure you get your device labels correct or you could screw something up.

The device copy also created 4 partitions (including swap) without formatting or partitioning ahead of time.  You gotta love Linux.  I had 10 copies that I needed to make, and each one booted correctly.

---

