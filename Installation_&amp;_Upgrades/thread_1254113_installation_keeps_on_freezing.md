---
title: "installation keeps on freezing"
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by zaydius1729 on 2009-08-30
im having trouble with the installation of Ubuntu. i have windows vista 32 bit on my laptop and im trying to boot up ubuntu 64 bit along with it because i have 4 GB ram. a 32 bit does not recognize all 4 GBs. so i downloaded ubuntu from the website and burned it on a CD and have tried to install it 3 times. all 3 times it gets to the installation bar and then stops at 69 percent... i would really appretiate help. i have a ton of HD space so i know that cannot be a problem

---

### Post by zaydius1729 on 2009-08-30
ok so i just tested the CD for any errors and it found one error... did not tell me much else about it... but i dont understand what to do... i just burnt this CD about 2 hours ago.

---

### Post by tal007 on 2009-08-30
If installation is freezing, the Hard disk space could be a problem. Using Live Ubuntu CD check how much unused space you have on your drive. Make sure that you have enough hard drive space unused, unpartitioned, unoccupied not belong to any other OS. You need at 8 GB of hard drive space. Be mindful also, allocating a size bigger than your BIOS's capability also causes problem.

---

### Post by presence1960 on 2009-08-31
> **tal007 said:**
> If installation is freezing, the Hard disk space could be a problem. Using Live Ubuntu CD check how much unused space you have on your drive. Make sure that you have enough hard drive space unused, unpartitioned, unoccupied not belong to any other OS. You need at 8 GB of hard drive space. Be mindful also, allocating a size bigger than your BIOS's capability also causes problem.

The hard disk space does not have to be unpartitioned or unformatted. You can shrink Vista to make room for Ubuntu then create your Ubuntu partitions from the unallocated space from Ubuntu Live CD using gparted (System > Administration > Partition Editor) or using the [gparted Live CD]("http://gparted.sourceforge.net/livecd.php")
You would then choose a manual install when you get to the partitioner when installing Ubuntu.

---

### Post by presence1960 on 2009-08-31
> **zaydius1729 said:**
> ok so i just tested the CD for any errors and it found one error... did not tell me much else about it... but i dont understand what to do... i just burnt this CD about 2 hours ago.
Did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the iso you burned the CD from? All hashes must match exactly or your iso is corrupted. if corrupted try downloading from a torrent- stay away from direct downloads.

Did you burn the iso as an image to CD-R at the slowest possible speed. if your burning software does not allow you to choose burn speed see [here]("https://help.ubuntu.com/9.04/switching/installing-burning.html") for InfraRecorder. Burning an image is not like burning a data CD. It is best to use something in the range of 4x-8x for burning speed to eliminate the chance for errors.

Then boot the Ubuntu Live Cd and check disk for errors again before trying to install

Another reason it is freezing could be this: did you shrink vista's partition with it's disk management utility to create room for Ubuntu? There is a known issue and a reported bug with no fix yet when using any outside partitioning utility to resize Vista's partition. Also defrag Vista once or twice before shrinking it's partition.

---

