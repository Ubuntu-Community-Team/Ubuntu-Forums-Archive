---
title: "can't boot windows after Ubuntu install / messed up part. table"
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by rene_est on 2009-10-08
Hello,
have searched the INet for the whole night for fix - nothing

1 physical HDD

I had previosly:
C: 2GB FAT32 (that has nothing useful on it (empty Dell recovery drive)
E: Windows XP Home (~147GB)

Now there should be:
C: 2GB FAT32
E: 132GB NTFS Windows XP Home
F: ~12GB Ubuntu
G: ~3GB SWAP

Made 15GB empty NTFS partition with a 3rd party software
Installed Ubuntu to that new F: drive. Ubuntu works, can't boot into Windows:
**a)** root>system32\hal.dll error. 
Tried fixing it in Windows disk recovery console:
D:\WINDOWS>SYSTEM32 **(ok)**
D:\WINDOWS>SYSTEM32\map **(ok)**
D:\WINDOWS>SYSTEM32\expand d:\i386\hal.dl_ **(ok)**
D:\WINDOWS>SYSTEM32\exit **(ok)**
Then:
attrib -h -r -s D:\Boot.ini **(parameter invalid)**
Del D:\Boot.ini **(file doesn't exist)**
Bootcfg /Rebuild **(operation failed)**
**b)** CHKDSK found one or more errors

During Ubuntu install used 'last' option - **Specify partitions manually**

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         262     2104483+   b  W95 FAT32
/dev/sda2             263       17902   141693300    f  W95 Ext'd (LBA)
/dev/sda3           17903       19457    12490537+  83  Linux
/dev/sda5             263       17537   138761406    7  HPFS/NTFS
/dev/sda6           17538       17902     2931831   82  Linux swap / Solaris
rene@rene-laptop:~$

Something is messed up, to be modest.
I'd be grateful for any help!

PS: I can get into files that are on the Windows drive from Ubuntu

---

### Post by Duke.Augustine on 2009-10-08
Did you try the steps below?
1. Insert Windows system CD
2. Reboot your system
3. Run shell as administator
4. Execute 'fixmbr'
5. Reboot your system again.

---

### Post by rene_est on 2009-10-08
now I lost the Ubuntu, too. 
There were a warning when I tried to use the fixmbr command for the first time. Then I backed down, not this time. GRUB is gone and I still can't boot into XP. I repeated everything written in the 1st post - still no luck.

---

