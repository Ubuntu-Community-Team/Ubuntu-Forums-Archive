---
title: "external hard drive not showing up in Nautilus"
date: 2008-05-04
forum: Hardware
---

### Post by nycjeff on 2008-05-04
So I had backed up a bunch of stuff on an external hard drive before I installed Hardy. 
Now when I am trying to put it back onto my system, Nautilus doesn't recognize it.
I can see it when I do fdisk -l, but when I try to mount it (sudo mount -t ntfs /dev/sdb1 /media/sdb1, it tells me that sdb1 doesn't have a valid ntfs.
But when I use HPFS/NTFS instead of ntfs, it tells me its an unknown file system type. 
Any thoughts are appreciated.

fdisk -l is below:

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02519901

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24791   199133676    7  HPFS/NTFS

---

