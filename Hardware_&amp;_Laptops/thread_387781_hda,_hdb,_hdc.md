---
title: "hda, hdb, hdc"
date: 2007-03-18
forum: Hardware &amp; Laptops
---

### Post by kramerkeller on 2007-03-18
fdisk -l gives the following output

I set this up a while ago when I installed linux.  If I physically remove my one harddrive (hda) my system won't boot.  I can't mount it because it does't appear to be formatted.  Is there a way I can make hdb hda and then add two hard drives hdb and hdc.  I have added drives on another system, but the way this is set up is giving me some trouble.  Isn't it odd to have the boot sector on hdb?  Any help would be great.

Disk /dev/hda: 13.7 GB, 13701316608 bytes
16 heads, 63 sectors/track, 26548 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4725    37953531   83  Linux
/dev/hdb2            4726        4865     1124550    5  Extended
/dev/hdb5            4726        4865     1124518+  82  Linux swap / Solaris

---

### Post by Xenogis on 2007-03-20
check your bios setup

---

