---
title: "Mounting Hard drive error &quot;mount: according to mtab, /dev/sdb1 is already mount&quot;"
date: 2016-10-16
forum: Hardware
---

### Post by razaq on 2016-10-16
When trying to mount the 500GB Western Digital external USB hard drive I get the following error.

"mount: according to mtab, /dev/sdb1 is already mounted on /media/My_Passport"

I am able to mount this hard drive on my other Ubuntu laptop / Windows 10 fine.The hard drive does not seem to have any problem.

Have tried to debug the problem but could not find the problem.

$sudo fdisk -l


Disk /dev/sdb: 500.1 GB, 500074283008 bytes
255 heads, 63 sectors/track, 60797 cylinders, total 976707584 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7bfc420a


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   976707583   488352768    7  HPFS/NTFS/exFAT



$cat /etc/mtab
nothing in mtab

Not Auto-mounting from fstab either.

$dmesg | grep sdb


[   45.042975] sd 4:0:0:0: [sdb] 976707584 512-byte logical blocks: (500 GB/465 GiB)
[   45.043986] sd 4:0:0:0: [sdb] Write Protect is off
[   45.043994] sd 4:0:0:0: [sdb] Mode Sense: 47 00 10 08
[   45.045228] sd 4:0:0:0: [sdb] No Caching mode page found
[   45.045233] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   45.048852] sd 4:0:0:0: [sdb] No Caching mode page found
[   45.048859] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   45.063503]  sdb: sdb1
[   45.108251] sd 4:0:0:0: [sdb] No Caching mode page found
[   45.108260] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   45.108267] sd 4:0:0:0: [sdb] Attached SCSI disk

---

