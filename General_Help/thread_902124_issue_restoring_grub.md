---
title: "issue restoring grub"
date: 2008-08-27
forum: General Help
---

### Post by themostunoriginalname on 2008-08-27
Currently running a 64-bit 7.10 disk to restore 32-bit 8.04 drive.

$sudo fdisk -l
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       31199   250605936    7  HPFS/NTFS
/dev/sda2           31200       38913    61962705    f  W95 Ext'd (LBA)
/dev/sda5           31200       36335    41254888+   7  HPFS/NTFS
/dev/sda6           38671       38913     1951866   82  Linux swap / Solaris
/dev/sda7           36336       38670    18755856   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007224e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10199    81923436   83  Linux
/dev/sdb2           10200       59526   396219127+  83  Linux


(sda7 is the root drive)
$sudo grub
$root (hd0,6)

root (hd0,6)

Error 25: Disk read error

grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found



This better not be another dead drive because this will be my 3rd of 4 drives that have died on me recently and all 4 are Seagates, so if it is, I'm going WD next time. So, any ideas?

thanks in advance

---

### Post by themostunoriginalname on 2008-08-27
Loaded up fail-safe boot and restarted and it works again... Strange... I wonder why. I see that 10 people, so thanks for looking at least.

---

