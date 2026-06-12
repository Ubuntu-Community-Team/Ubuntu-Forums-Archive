---
title: "Format Read-Only USB"
date: 2012-07-21
forum: Hardware
---

### Post by larsdouglas on 2012-07-21
Ive got a USB-drive from my brother that he cannot use because its protected w a PIN and noone at the company remembers what it is.
So Id like to format it and use it as a regular USB, but I cant. It is only mounted as read-only and I cant for the life of me change that.

I've looked inside and there is no switch so the read-only has to be software governed. When running sudo fdisk I can see the device but only a partition of 1Mb where the PIN-application resides. There are a few other partitions as well but these are broken.

I've tried using testdisk to write a new partition table to it. No go.
I've tried "sudo dd if=/dev/zero of=/dev/sdb" and the same w "bs=512 count=1". But no go.
I've tried to load it unto a windows machine and format it there but, no go.

Any ideas? I just want to wipe it clean and get it to work like a normal device. Possible?

---

### Post by ranger1021994 on 2012-07-21
If the drive's encrypted with a PIN...
I dont think anything is left to happen..its useless
I encrypted my drive once...it showed me 512kb space where the PIN application was stored...
Hope you didnt delete that app in 1MB space...

---

### Post by dpharo on 2012-07-21
Before throwing it out try this.

Get to a windows machine. Insert key drive. Right click and select properties. Select error checking. Allow it to correct errors. Dismount and try it again. It should work.

Good luck :)

---

