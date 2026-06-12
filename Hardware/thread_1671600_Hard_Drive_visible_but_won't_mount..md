---
title: "Hard Drive visible but won't mount."
date: 2011-01-20
forum: Hardware
---

### Post by BluffTrout on 2011-01-20
I am relatively new to Linux and have been dual booting Ubuntu 10.10 pretty much since release. I have had no problems what so ever with anything other than my external hard drive.

When I go to 'places' it is listed twice, one as sdb2 the other as sdb3.

I have tried to manually mount the hard drive but it still throws an error saying that the ntfs partition is missing.

Here is what fdisk -l brings up:


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f37d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        8219    65913856    7  HPFS/NTFS
/dev/sda3            8219       14594    51200000    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6e697373

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?      120528      234814   918008208    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?      119381      153271   272218546+  73  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      113202      147075   272087568   2b  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?      177064      177067       27487   61  SpeedStor
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

any help would be greatly appreciated, I want to get this sorted so that I can fully boot Ubuntu on this system.

---

### Post by BluffTrout on 2011-01-21
Bump.

---

### Post by BluffTrout on 2011-01-25
No one having/had the same problem? :(

---

### Post by fjgaude on 2011-01-25
Okay, your external hard drive is USB... Is it formatted for Windows or Linux?

---

### Post by BluffTrout on 2011-01-28
It was formatted for Windows, but I haven't got a spare hard drive to transfer it all over and re-format it. I thought that seeing that it is recognised but won't mount, then there would be an easier fix for it.

---

### Post by vanadium on 2011-01-28
> **BluffTrout said:**
> 
When I go to 'places' it is listed twice, one as sdb2 the other as sdb3.

Each of these is a partition on the same drive, sdb.

> Here is what fdisk -l brings up:
...
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6e697373

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?      120528      234814   918008208    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?      119381      153271   272218546+  73  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      113202      147075   272087568   2b  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?      177064      177067       27487   61  SpeedStor
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order


It looks as if the partition table of that drive is badly damaged. Can it still be used under Windows?

As for now, the only possibility I see is to try repartitioning and reformatting the drive. It could be related to a hardware failing. If that is the case, you might or might not able to repartition it again, and then, it may be at risk of failing soon again.

You always should have a backup of your data. If you have not and need to rescue the data, you could try "testdisk" to attempt restoring the partitions and rescuing the data.

---

### Post by BluffTrout on 2011-01-28
It still runs on Windows fine. I have a partition that can be seen by both OS's so that I can transfer files to the hard drive within Windows.

Would making a new partition within Windows and then formatting that partition keep the current data safe?

---

### Post by vanadium on 2011-01-28
First have all partitions checked using the Windows file system checking tools. Then check whether the issue is resolved under Ubuntu.

If not, then repartitioning might be the only option to correct your partition table (which, apparently, Ubuntu currently cannot handle). However, this would involve erasing the data.

If you do not have a backup of these data, then the data are probably not that valuable after all. If you do have a backup, then make it up to date and proceed.

---

### Post by BluffTrout on 2011-01-28
Just had a look at the hard drive on Windows, and it is only showing one partition as opposed to Linux showing 4.

---

