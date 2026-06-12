---
title: "Can't boot XP after Ubuntu install"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by linsol on 2009-03-19
Hi all, I installed 10.1 yesterday on my Desktop computer. I had Windows 2000 on the 1st partition, 10 gigs, and XP on the second 20 gigs. I did the manual partitioning, told Ubuntu to format the 10 gig partition and to set it as /
It did format the 1st partition, shows as boot, but installed ubuntu in the windows partition. Now XP doesn't show up on grub at boot.
Here's the output from sudo fdisk -l

Disk /dev/sda: 30.7 GB, 30735581184 bytes
255 heads, 63 sectors/track, 3736 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5e9d292f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10236208+  83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2            1276        3731    19727820    f  W95 Ext'd (LBA)
/dev/sda5            1276        3731    19727788+   7  HPFS/NTFS


All my XP folders and files seam to be there but now there's an ubuntu folder also.
How do I get ubuntu onto sda1 and how do I get xp back?

Thanks
Bill

---

### Post by sahabcse on 2009-03-19
Hi

Try to fix the grub. Follow below url

=============================
[http://sahabm.blogspot.com/2009/01/grub-fix-windows.html](http://sahabm.blogspot.com/2009/01/grub-fix-windows.html)
[http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html](http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html)
=============================

---

### Post by mikewhatever on 2009-03-19
> **linsol said:**
> 
How do I get ubuntu onto sda1 and how do I get xp back?


Ubuntu is on sda1 according to fdisk. As for XP, it seems to be on sda5, but the problem is likely its bootloader. Windows can't boot, unless it's bootloader is on a primary partition (usually the first one). In your case, the bootloader files mist have been on what used to be Windows 2000 partition, but you deleted them when installing Ubuntu. 
The most obvious solution is to backup your files and reinstall XP on a primary partition. If reinstalling isn't an option, you could try resizing sda1 and creating a small primary partition in the beginning, and then trying to restore Windows' boot loader.

---

