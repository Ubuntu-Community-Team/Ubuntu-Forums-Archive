---
title: "USB disk mounts but cant use it"
date: 2007-05-24
forum: Hardware &amp; Laptops
---

### Post by tmogeem on 2007-05-24
im new to linux so plz i need detailed info :P

i have a 100 GB hard disk, USB external .. and everytime i hook it up to the pc it says

Cannot mount volume.
You are not privileged to mount the volume 'my volumes name'

and when i input

sudo fdisk -l

in the terminal, this is what i get

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         131     1048576   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         131        6658    52428800    7  HPFS/NTFS
/dev/sda3            6659        6901     1951897+  82  Linux swap / Solaris
/dev/sda4            6902        9729    22715910   83  Linux

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       11009    88429761    6  FAT16
/dev/sdb2           11010       12161     9253440    f  W95 Ext'd (LBA)
/dev/sdb5           11010       12161     9253408+  83  Linux

so, the device is there and when i double click on it, i go to lost+found folder.

do you guys have any idea?

---

### Post by tmogeem on 2007-05-25
up

---

