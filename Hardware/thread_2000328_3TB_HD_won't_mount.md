---
title: "3TB HD won't mount"
date: 2012-06-09
forum: Hardware
---

### Post by vjfidalgo on 2012-06-09
Hi,

I have three 3TB Seagate Go Flex HDs. These were formatted under Linux about a year and a half ago using the ext4 fs (if I remember correctly). I have used them as a back up location, so not too often. They have always worked perfectly well, and nothing out of the ordinary has happened.

I recently replaced my desktop's internal HD by a new bigger one. On it, I installed Ubuntu 12.04 and all of a sudden, they drives won't mount any more. The drives are seen by the OS, as shown by the disk utility, but it's impossible to mount them.

I have tried loading different versions (from the CD) of Ubuntu: 9.04, 10.04.4, 10.10, 11, etc., hoping that the drives would behave as they used too. No success. I even put my old internal HD back and booted my old Linux OS and the HDs are no longer properly recognised.

This is very strange. The disk utility seems to offer the possibility of partition/format the drives, which I would happily do, were it not for the fact that I have all my phd results on those drives! Any help would be very much appreciated.

Please, see two attached screen shots of the disk utility.

[IMG]https://dl.dropbox.com/u/4770407/DiskUtilityScreenshot1.png[/IMG]

[IMG]https://dl.dropbox.com/u/4770407/DiskUtilityScreenshot2.png[/IMG]

Please, see the output when I try to do a manual mount:

```
sudo mount -t ext4 /dev/sdb1 /media/
```

-----------------------------

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

-----------------------------


Please, see below the output of ```
sudo fdisk -l
``` :


-----------------------------

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  1953118439   976559188+   7  HPFS/NTFS/exFAT
/dev/sda2      1953118440  2451328388   249104974+  83  Linux
/dev/sda3      2451329022  3907028991   727849985    5  Extended
/dev/sda5      2941143040  3885953023   472404992   83  Linux
/dev/sda6      3885955072  3907028991    10536960   82  Linux swap / Solaris
/dev/sda7      2451329024  2921211903   234941440   83  Linux
/dev/sda8      2921213952  2941132799     9959424   82  Linux swap / Solaris

Partition table entries are not in disk order

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.

Note: sector size is 4096 (not 512)

Disk /dev/sdb: 3000.6 GB, 3000592977920 bytes
256 heads, 63 sectors/track, 45422 cylinders, total 732566645 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  4294967292   ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.

Note: sector size is 4096 (not 512)

Disk /dev/sdc: 3000.6 GB, 3000592977920 bytes
256 heads, 63 sectors/track, 45422 cylinders, total 732566645 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  4294967295  4294967292   ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.

Note: sector size is 4096 (not 512)

Disk /dev/sdd: 3000.6 GB, 3000592977920 bytes
256 heads, 63 sectors/track, 45422 cylinders, total 732566645 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1  4294967295  4294967292   ee  GPT

-----------------------------

---

