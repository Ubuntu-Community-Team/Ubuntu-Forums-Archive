---
title: "Dual booting with WinXP on IDE drive and Ubuntu on SATA drive"
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by raora on 2008-12-11
Hello,

I have a computer with 4 hard drives with Win XP installed as the only OS:

IDE master - Win XP
IDE slave
SATA 1
SATA 2

I want to install Ubuntu on SATA 2.  What is the best way to do this?  What are the partitions required for Ubuntu?  The drive is about 200GB and I would like to create a FAT32 partition on it also.

Thanks.

---

### Post by cariboo on 2008-12-11
I have a similar setup, with Windows Vista and Intrepid on an IDE drive and Jaunty on a SATA drive, plus two eSATA drives for storage. You should have no problem getting things setup. 

I would suggest if it is a blank hard drive to partiton just what you need for Ubuntu, you will need at minimum 2 partitions a main partition called / and a swap partition. You can create and format your fat32 partition after you have installed Ubuntu.

Jim

---

### Post by Pumalite on 2008-12-11
Read this:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

