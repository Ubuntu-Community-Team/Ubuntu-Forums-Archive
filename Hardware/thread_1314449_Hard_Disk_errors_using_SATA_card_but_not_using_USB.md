---
title: "Hard Disk errors using SATA card but not using USB interface"
date: 2009-11-04
forum: Hardware
---

### Post by TooTechy on 2009-11-04
An external Seagate Barracuda ST31000340AS SATA HD about one year old is starting to generate media errors. This normally implies an impending failure of the drive.

But, if I use 'hdparm --read-sector xxx' to read the reported bad sector it says "success" which should indicate the drive is fine. 

The driver indicates (in the kernel log) that the drive was unable to reallocate the sector in question. A jfs_fsck of the drive fails.

If I connect the drive via an external USB chassis, it behaves perfectly.

I have switched SATA power supplies, external SATA chassis and even the SATA card and cable.

This drive/chassis/SATA card combination has been working for some time without error. I have other drives hanging off the cards. Silicon Image Sil 3114.

My question is:- What behavioral difference is there between the SATA and USB interfaces which would allow the drive to "apparently" behave perfectly under the USB and produce errors under the SATA.

Ubuntu amd64 8.04 LTS with all patches up to date. Although I am now running a previous kernel 2.6.20-15 in the hope of removing the errors.

Any ideas on what is going on? Thanks.

---

