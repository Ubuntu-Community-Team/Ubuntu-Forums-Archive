---
title: "Recover data from WD MyBookworld Hard Drive"
date: 2013-11-09
forum: Hardware
---

### Post by neilcallaway on 2013-11-09
Hi
My MyBookworld enclosure died, i have removed the hard drive from the housing and managed to mount it in my PC.  I looked at it with Partition Assistant and it says it is ext3.
I have created a USB with Ubuntu 13.10 on it and booted the PC, when i look at in the Disks it states it is Linux Raid FAT 12.

I have tried to mount it as stated in some other forums, but am having no luck, I was hoping some one may be able to help me.

If i run fdisk -l this is the result:


root@ubuntu:/home/ubuntu# fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      224909      112423+  de  Dell Utility
/dev/sda2   *      225280    18489343     9132032    7  HPFS/NTFS/exFAT
/dev/sda3        18489344  1465145343   723328000    7  HPFS/NTFS/exFAT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00007c00

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           48195     5927984     2939895    1  FAT12
/dev/sdb2         5927985     6136829      104422+   1  FAT12
/dev/sdb3         6136830     8112824      987997+   1  FAT12
/dev/sdb4         8112825  1953520064   972703620    1  FAT12

Disk /dev/sdc: 16.0 GB, 16043212800 bytes
64 heads, 32 sectors/track, 15300 cylinders, total 31334400 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x20ac7dda

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?  3224498923  3657370039   216435558+   7  HPFS/NTFS/exFAT
/dev/sdc2   ?  3272020941   930513678   976730017   16  Hidden FAT16
/dev/sdc3   ?           0           0           0   6f  Unknown
/dev/sdc4        50200576   974536369   462167897    0  Empty

Partition table entries are not in disk order

I have made a directory /media/abc  (this is created)

When I try and mount it using:

mount -t ext3 /dev/sdb4 /media/abc  I get this:

mount: wrong fs type, bad option, bad superblock on /dev/sdb4,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

dmesg | tail  results in this:

[ 4048.126156]         00 7d 90 10 
[ 4048.126169] sd 3:0:0:0: [sdb]  
[ 4048.126175] Add. Sense: Unrecovered read error - auto reallocate failed
[ 4048.126180] sd 3:0:0:0: [sdb] CDB: 
[ 4048.126183] Read(10): 28 00 00 7d 90 09 00 00 08 00
[ 4048.126197] end_request: I/O error, dev sdb, sector 8228880
[ 4048.126239] ata4: EH complete
[ 4048.126246] JBD: Failed to read block at offset 12947
[ 4048.126622] JBD: recovery failed
[ 4048.126628] EXT3-fs (sdb4): error loading journal

I have tried it replacing ext3 with xfs as suggested.

Any help appreciated, complete newbie to Unbuntu.

Thanks
Caz:confused:

---

