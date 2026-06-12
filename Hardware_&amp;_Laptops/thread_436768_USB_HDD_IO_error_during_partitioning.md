---
title: "USB HDD I/O error during partitioning"
date: 2007-05-08
forum: Hardware &amp; Laptops
---

### Post by kcdimgba on 2007-05-08
I have tried installing Ubuntu on a USB HDD from a live CD. It goes well until I try partitioning disk for the installation. It comes up with the error cannot read/write to disk. Input/output failure.
I take the USB HDD to a Linux OS to try partiton there and it asks me to set disklabel on /dev/sdb. when i try to do this it comes with another error. Error while setting new disklabel.
I take it to an XP system and partition it but bringing back to Ubuntu Linux, the partition is not recognized. it appears as a new unpartitioned disk and can’t be partitioned in Linux. I tried the dd command and it comes up with read/write error. Need some help pls. 
The dmesg command gives buffer I/O error on device sdb, SCSI error.
The drive works well on windows O/S after partitioning and formating but still can't get to wipe off from Linux and partition.

---

### Post by kidders on 2007-05-09
Hi there,

Your description makes this sound an awful lot like a hardware problem ... but if that were the case, surely your hard disk wouldn't work with *any* OS. Have you considered filing a bug report? You seem to have good knowledge of how Linux handles block devices, so the bug database might be the best place for you to get concrete answers quickly.

---

### Post by kcdimgba on 2007-05-10
Thanks Kiddies. Where do I file a bug report? I am new to this forum.

---

### Post by kidders on 2007-05-10
This forum doesn't handle bugs reports. Try here ... [https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs)

---

