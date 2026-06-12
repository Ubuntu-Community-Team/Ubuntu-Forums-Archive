---
title: "Reinstalling Hardy from CD, but no sight of ext3 or swap partitions"
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by raynevandunem on 2009-05-23
I installed Hardy from CD+Wubi last year as a dual-boot with WinXP, and then I downloaded+upgraded to Intrepid when it came out, then to Jaunty last week. But Jaunty won't start up correctly, only giving me a tty1 login rather than the normal graphical login. 

So I'm trying to reinstall Hardy and try upgrading to Jaunty, but don't want to lose the Wubi dual boot, so I'm going for Manual partition.

But when I try to find the correct partition, I only see three partitions: sda1 (ntfs), free space (only 8 MB), sda2 (fat32) and sda3 (ntfs). There's no ext3 or swap like in other tutorials.

So if I only have three sda partitions, which one should I format and partition with a reinstalled Ubuntu?

---

### Post by lindsay7 on 2009-05-23
If you used wubi to install Ubuntu. It is under windows. You will not have or see a partition for it.  You can uninstall your old Ubuntu from the add/remove programs in the control panel. Then you can install what you want with wubi.  Be sure to save and valuable befor you delete you old Ubuntu.

---

