---
title: "HD mounting issues (NTFS)"
date: 2011-10-20
forum: Hardware
---

### Post by Rocky1980 on 2011-10-20
Hi all,


I recently picked up a new 2tb internal SATA WD Hd to use as a storage drive. It installed fine and I used the disk utility (I am using ubuntu 11.4) to create one large partition on it I then copyied almost 600gigs worth off data onto the new drive. Everything was fine until there was a power cut :( all my other drives are fine but the new storage drive (Igor) is not, I will not auto mount and when I try to mount it from the places menu I get the following

"Error mounting: mount exited with exit code 12: NTFS signature is missing.
Failed to mount '/dev/sdb2': Invalid argument
The device '/dev/sdb2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
"


Worse still It looks like the partition has been split in two ??? 
[[IMG]http://img265.imageshack.us/img265/8411/screenshotqgc.th.png[/IMG]](http://imageshack.us/photo/my-images/265/screenshotqgc.png/)



I know a format and/or a new partition will fix the issue but I really cant afford to lose all my data :(

"sudo fdisk -l" gives the following output 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000dbb05

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121082   972584960   83  Linux
/dev/sda2          121082      121602     4174849    5  Extended
/dev/sda5          121082      121602     4174848   82  Linux swap / Solaris

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?         410      119791   958924038+  70  DiskSecure Multi-Boot
Partition 1 does not end on cylinder boundary.
Partition 1 does not start on physical sector boundary.
/dev/sdb2   ?      121585      234786   909287957+  43  Unknown
Partition 2 does not end on cylinder boundary.
Partition 2 does not start on physical sector boundary.
/dev/sdb3   ?       14052       14052           5   72  Unknown
Partition 3 does not end on cylinder boundary.
Partition 3 does not start on physical sector boundary.
/dev/sdb4          164483      164486       25945    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7d46be16

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      243201  1953512001    7  HPFS/NTFS





Any help would be great 

Many thanks

---

### Post by diasf on 2011-10-20
The power cut probably damaged your partition. Try one of the many possible recovery options..
(no, I don't remember any of them atm :( )

---

### Post by Rocky1980 on 2011-10-20
Help tried Testdisk but to many options :(

---

### Post by Rocky1980 on 2011-10-22
Sorted :) I had to use a Windows file recovery tool :( but I got 90% off my files back

---

### Post by crashnburn_in on 2011-10-22
Which tool did you use? People would appreciate it if you share complete information :)

---

