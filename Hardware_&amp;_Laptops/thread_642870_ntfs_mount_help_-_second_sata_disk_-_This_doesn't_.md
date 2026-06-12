---
title: "ntfs mount help - second sata disk - This doesn't look like a partition table"
date: 2007-12-17
forum: Hardware &amp; Laptops
---

### Post by qsluo on 2007-12-17
hi all.

i have 3 hard disk, one is IDE and two are SATA. Gutsy is installed on the IDE disk hda1. and the other two disk are NTFS. the problem is that i can read and write the first SATA disk sda1, but can NOT mount the SECOND SATA disk. there is only a /dev/sdb, and no /dev/sdb1 item. and fdidsk -f says: "This doesn't look like a partition table Probably you selected the wrong device."

did anybody encounter the same problem with me? or any suggestions?

thank you.



here comes the fdisk information:

sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
16 heads, 63 sectors/track, 310101 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x1c66b08e

Device Boot Start End Blocks Id System
/dev/sda1 * 1 310097 156288856+ 7 HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x5cbc07f3

This doesn't look like a partition table
Probably you selected the wrong device.

Device Boot Start End Blocks Id System
/dev/sdb1 ? 1 484518 244197040+ 7 HPFS/NTFS

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x077aad1c

Device Boot Start End Blocks Id System
/dev/hda1 * 1 9376 75312688+ 83 Linux
/dev/hda2 9377 9729 2835472+ 5 Extended
/dev/hda5 9377 9729 2835441 82 Linux swap / Solaris

---

### Post by viking777 on 2007-12-17
There are dozens of posts on the forum from people who have 'mixed' hard drives in their systems and these seem to cause Linux a good deal of difficulty at the moment. There are also several bugs on launchpad that deal with the same issue, they are very highly prioritised for repair, but I don't think there are any fixes out as yet. It may just be a question of waiting for this to be addressed at a high level, probably not something you can fix yourself. Don't stop trying though, if you solve it you can tell the developers how it is done!!

---

