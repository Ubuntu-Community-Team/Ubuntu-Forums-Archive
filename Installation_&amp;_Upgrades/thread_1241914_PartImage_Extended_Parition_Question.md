---
title: "PartImage Extended Parition Question"
date: 2009-08-16
forum: Installation &amp; Upgrades
---

### Post by nmaster on 2009-08-16
Here is just some background information:


I looked at these links:
[INDENT][http://ubuntuforums.org/showthread.php?t=287522](http://ubuntuforums.org/showthread.php?t=287522)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)


[/INDENT]Output of sudo fstab -l

```

neal@neal-laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x149f149f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17957   144239571    5  Extended
/dev/sda2           17958       19457    12048750    7  HPFS/NTFS
/dev/sda5               1       17507   140624914+  83  Linux
/dev/sda6           17508       17957     3614593+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    c  W95 FAT32 (LBA)


```

I've also attached a screenshot from GParted.



My question(s):  When using PartImage, should I choose to make an image of sda1?  Will this make an image of both sda5 and sda6?  I'll be reformatting the external hard drive (sdc1) from FAT32 to NTFS to avoid having 4GB as the maximum file size.


Thanks for the advice.

---

### Post by louieb on 2009-08-16
Although listed and you can select sda1 (extended partition) or  sda6 (Linux swap) - after you press F5 to continue - partimage will give you a message about not supported format and the only option you have is to cancel..

---

### Post by nmaster on 2009-08-16
so i guess i have to choose sda5...does it matter that sda1 has the asterisk denoting it as the boot partition? if i had an image of sda5, after restoring would i not be able to boot from it?

---

### Post by louieb on 2009-08-16
Linux does not care if the boot flag is set or not. It will boot with it set or not.

 It does not make sense to set the boot flag on an extended partition - it  only a container for logical partitions. Does not hurt anything to leave it as is - you can turn it off with Gparted.

---

### Post by nmaster on 2009-08-16
cool.  thanks.

---

