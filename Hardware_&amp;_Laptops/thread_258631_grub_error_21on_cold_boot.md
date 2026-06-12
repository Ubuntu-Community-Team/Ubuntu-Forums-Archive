---
title: "grub error 21on cold boot"
date: 2006-09-16
forum: Hardware &amp; Laptops
---

### Post by nutcracker23 on 2006-09-16
Hi. I have a problem which is an irritation rather than a major headache. I have successfully installed Ubuntu Dapper in a partition on my second hard disk (hdb2). Windows XP is on hda1. When I cold boot the computer grub always gives error 21 which relates to not being able to find the partition. If I reboot then grub boots perfectly normally into Ubuntu. By scrutinising the screen when BIOS is booting I noticed that hdb is not detected by the bios on a cold boot but is on a reboot. This presumably explains the grub message. I am guessing that the spin up time for the disc means that it is not ready when the Bios is detecting discs initially but that is just my explanation. Can anyone suggest something I can do to correct this?

If it is of any relevance my motherboard is a MSI KM3M (K7) with sempron 2400 cpu. hda is 115Gb Hitachi Deskstar, hdb is 250GB Maxtor.

---

### Post by tagra123 on 2006-09-16
Did you try changing BIOS settings to show the disk? Maybe remove auto settings for the drive and manually enter?

Good link:

[http://linuxfromscratch.org/pipermail/lfs-support/2005-March/026476.html](http://linuxfromscratch.org/pipermail/lfs-support/2005-March/026476.html)

---

