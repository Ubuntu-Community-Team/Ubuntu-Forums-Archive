---
title: "Deleting partition caused GRUB error 17"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by Thelatinprodigy on 2009-07-15
For a while, I had a multi-boot of windows, ubuntu, and about 3 other useless partitions of the same ubuntu. I used parted magic to delete one, and that caused me to see the error 17 message on startup. Please help.

---

### Post by dstew on 2009-07-15
When you add, delete, or move partitions, grub will often fail, because the grub stage1 and stage1.5 files have no ability to search for the grub stage2 and menu. When installed, grub is targeted to a particular partition by number, and if the partition is moved, grub has no way to find it.

You need to re-install grub. [Here]("http://ubuntuforums.org/showthread.php?t=224351") are the instructions. Post back if you have any problems.

---

### Post by carml on 2009-07-15
Maybe editing /boot/grub/menu.lst can help,recently I deleted the hidden partition of Vista,edited the file and I don't have issues (note: that partition wasn't bootable,at least after the installation of Ubuntu).

---

### Post by Thelatinprodigy on 2009-07-15
> **dstew said:**
> When you add, delete, or move partitions, grub will often fail, because the grub stage1 and stage1.5 files have no ability to search for the grub stage2 and menu. When installed, grub is targeted to a particular partition by number, and if the partition is moved, grub has no way to find it.

You need to re-install grub. [Here]("http://ubuntuforums.org/showthread.php?t=224351") are the instructions. Post back if you have any problems.

Thank you, those instructions worked flawlessly.

---

