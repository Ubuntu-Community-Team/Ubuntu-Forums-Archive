---
title: "[SOLVED] Cany anyone help me with shifting drive assignments?"
date: 2007-08-26
forum: Hardware &amp; Laptops
---

### Post by Phurious on 2007-08-26
Here is my dilemma .  I have 3 drives in my system:

[LIST=1]
[*]3 x 74GB WD Raptor on an Areca 1210 RAID card (System)
[*]8 x 250GB Hitcahi SATA II drives on an Areca 1220 RAID card (Data)
[*]1 160GB Hitachi SATA II drive (Scratch) 
[/LIST]

Here is a copy of my FSTAB file:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9e6ecdf2-843f-4337-af1c-46939db7f6f8 /               ext3    defaults,errors=remount-ro,noatime,data=writeback 0       1
# /dev/sda5
UUID=3e518479-9487-420f-a18c-01b7c1fe4be4 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/sdb1 /mnt/RAID ext3 defaults,noatime,data=writeback 0 0
/dev/sdc1 /mnt/DATA ext3 defaults,noatime,data=writeback 0 0
```

Looks pretty simple and straight forward, but it's not.  It seems that *ALMOST* every time I reboot my machine the drive assignments change - and I do not know how or why. 

Here are the results of a fdisk -l corresponding to the above FSTAB
```
Disk /dev/sda: 209.9 GB, 209999364096 bytes
255 heads, 63 sectors/track, 25530 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16324   131122498+  83  Linux
/dev/sda2           16325       17020     5590620    5  Extended
/dev/sda5           16325       17020     5590588+  82  Linux swap / Solaris

Disk /dev/sdb: 1749.9 GB, 1749999419392 bytes
64 heads, 32 sectors/track, 1668929 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1     1668929  1708983280   83  Linux

Disk /dev/sdc: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       20023   160834716   83  Linux

```

The problem is, when I reboot my drives are all screwy, and fdisk -l will result in this (or some other variation):

```
Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       20023   160834716   83  Linux

Disk /dev/sdb: 209.9 GB, 209999364096 bytes
255 heads, 63 sectors/track, 25530 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       16324   131122498+  83  Linux
/dev/sdb2           16325       17020     5590620    5  Extended
/dev/sdb5           16325       17020     5590588+  82  Linux swap / Solaris

Disk /dev/sdc: 1749.9 GB, 1749999419392 bytes
64 heads, 32 sectors/track, 1668929 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1     1668929  1708983280   83  Linux
```

Cany anyone tell me what I need to do to prevent my drives from playing musical chairs? :confused:

---

### Post by Hoenheim on 2007-08-26
Have you turned off auto reset in bios? That might help.

---

### Post by jordanmthomas on 2007-08-26
If all your disks have labels, you can put something like this in your fstab
```
/dev/disk/by-label/labelname
``` instead of 
```
/dev/sdx
```

If you don't have labels you can use UUIDS.  I'm not sure how to get the UUID of a volume, but a quick google should turn it up.  Hope this helps get you going in the right direction.

---

### Post by merlinus on 2007-08-26
```

blkid

```

will give you the UUIDs for your partitions.

-merlin

---

### Post by jordanmthomas on 2007-08-26
That was easier than I expected.  :)

---

### Post by Phurious on 2007-08-26
Love this forum!  The UUID's were EXACTLY the answer to the problem!  Thanks so much everyone!  :popcorn:

---

