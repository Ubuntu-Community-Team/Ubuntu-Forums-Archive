---
title: "Dual Boot Partition help"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by yobnoc on 2009-04-26
I partitioned  my disk just fine but when I was installing 8.10 I had a "read disk" error pop up. No problem I checked the disk for errors. Its fine. I try to redownload but it wants to partition my disk again. How can I download for dual boot on the original partition?

---

### Post by yobnoc on 2009-04-26
Should I try to undo the original partition in the partition editor and start over?

---

### Post by Bucky Ball on 2009-04-26
When you get to the partitioner during install, select 'manual partitioning', delete all partitions except the windows install which should be on first partition of a drive, manually partition the rest how you want and you're done.

Bit confused, you mean 'disk read error' on the CD, not the hard drive, right?

---

### Post by lisati on 2009-04-26
The installation disk has a "Check CD for errors" option - presumably this is what the original poster has done. On the rare occasion I've had "disk read error" pop up, it has usually been because of a dirty disk: recently it was because a bit of the night before's dinner had somehow got stuck to the disk! 

Please forgive me if this seems obvious: if you're manually tinkering with partitions, remember to keep an eye open for Windows recovery partitions as well as the main partition. And don't be scared to arrange backups of your important data. As much as we hate to admit it, things sometimes go wrong.

---

### Post by yobnoc on 2009-04-26
Sorry, yes my disk. Clicking manual was the first thing i tried but it says 100%. So doing that will not wipe my entire drive just the orginal partition I set a side for Ubuntu?

---

### Post by yobnoc on 2009-04-26
I deleted the non-windows partitions and created a new partition but I am getting this error message:  No root file system is defined.

Please correct this from the partitioning menu.

---

### Post by mikemikejomike11 on 2009-04-26
> **yobnoc said:**
> I partitioned  my disk just fine but when I was installing 8.10 I had a "read disk" error pop up. No problem I checked the disk for errors. Its fine. I try to redownload but it wants to partition my disk again. How can I download for dual boot on the original partition?
what operating sys? partition with fdisk will remove all info off disk then format ea partition .                    then install windows first before linux.ubuntu loses grub boot some times when the two on same disk if you can put each on separate hard drives change hard drives each time .windows or ubuntu or any linux because boot grub always messes up unless you know how to fix best though is two pc`c with wdos or linux.

---

### Post by theozzlives on 2009-04-26
Click edit on your Ubuntu partition, you'll see mount point, choose / which is symbolic for root.

---

