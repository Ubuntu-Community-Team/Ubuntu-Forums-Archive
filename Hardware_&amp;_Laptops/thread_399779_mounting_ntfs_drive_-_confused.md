---
title: "mounting ntfs drive - confused"
date: 2007-04-02
forum: Hardware &amp; Laptops
---

### Post by rudlavibizon on 2007-04-02
I have 3 hard disks (1 IDE + 2 SATA) with ntfs,ext3 and fat32 partitions which were all recognized by my previous installation (ubuntu edgy). I made a clean install of kubuntu feisty beta with the IDE drive turned off because previous ubuntu installations wrote GRUB on it and i plan on ditching this one in the month or two. Now in Feisty i don't have that IDE disk in /media. What do i do now to mount it ?


Here is my fdisk:

```
Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       20023   160834716    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sdb2            6375       24321   144159277+   f  W95 Ext'd (LBA)
/dev/sdb5            6375       24321   144159246    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        2433    19543041   83  Linux
/dev/sdc3            2434       30402   224653969    f  W95 Ext'd (LBA)
Partition 3 does not end on cylinder boundary.
/dev/sdc5            9102       12748    29294496    b  W95 FAT32
/dev/sdc6           12749       30402   141796840+   7  HPFS/NTFS
/dev/sdc7            8512        9101     4739143+  82  Linux swap / Solaris
/dev/sdc8            2434        8511    48821503+  83  Linux
```

and this my fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=1398f8cd-b8d9-45ae-88c0-a56ebfa20d7d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=600C0E490C0E1B24 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=B624DF8424DF45D1 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb5
UUID=DE10-CE4C  /media/sdb5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb6
UUID=78C8A971C8A92DF6 /media/sdb6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb8
UUID=a7784407-37bc-4398-bfd8-867f5fafa741 /media/sdb8     ext3    defaults        0       2
# /dev/sdb7
UUID=33bae1cb-f699-4937-8e91-2ad4d7c27ba0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

I did this on breezy once but i forgot due to the recent improvements in user friendliness of Ubuntu ;)

---

### Post by Sammi on 2007-04-02
[www.ubuntuguide.org](www.ubuntuguide.org) has some info on this:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows)
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Hard_Drive](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Hard_Drive)

---

### Post by rudlavibizon on 2007-04-02
Thanks a lot,  I completely forgot about that wiki/How-to. I should try some cod fish liver oil ;)

---

