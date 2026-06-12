---
title: "[SOLVED] Duplicate UUid's"
date: 2008-09-03
forum: General Help
---

### Post by texasjim on 2008-09-03
Howdy y'all, In trying to mount my partitions thru fstab, I have discovered that 2 separate partitions on 2 separate harddrives
have the same UUID. Thus, only one of them will mount at a time.

 In the enclosed fstab, fdisk, and blkid, the partitions SDA8 and SDC3 are the same.  Any ideas before a re-install?

Code:
studio@studio:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=e9cc487c-4843-4ab4-92ac-11ced150d6e0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=f90456a5-a292-4cef-85f7-2f96847ffe5f /boot           ext3    relatime        0       2
# /dev/sdb5
UUID=cda041b9-e2dd-49fb-82f7-a6404b6ad4a2 /home           ext3    relatime        0       2
# /dev/sdc2
UUID=64a4edbe-c867-4f03-adaa-6a27b3813f7f none            swap    sw              0       0
# ##########################################################################################
# /dev/sda1 winxp
UUID=E09446D79446B038                     /media/winxp    ntfs    defaults        0       2
# /dev/sda7
UUID=89172d89-7863-443c-b581-3dad89da1e1e /media/sda7     ext3    defaults        0       2
# /dev/sda8
UUID=3bad0d0e-ce83-40c3-8968-9f603eea326a /media/sda8     ext3    defaults        0       2 
# /dev/sda9
UUID=7df9ebde-52a9-47b7-abcb-9b77f45df492 /media/sda9     ext3    defaults        0       2  
# /dev/sdb5
UUID=cda041b9-e2dd-49fb-82f7-a6404b6ad4a2 /media/sdb5     ext3    defaults        0       2
# /dev/sdc1
UUID=6cf51156-47e2-41f1-abc5-84ce038ef287 /media/sdc1     ext3    defaults        0       2


# #############################################################################################
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0



studio@studio:~$ sudo fdisk -l
[sudo] password for studio: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00025108

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1305    10482381    7  HPFS/NTFS
/dev/sda2            1306        9729    67665780    5  Extended
/dev/sda5   *        1306        1688     3076416   83  Linux
/dev/sda6            1689        3218    12289693+  83  Linux
/dev/sda7            3219        6562    26860648+  83  Linux
/dev/sda8            8734        9729     8000338+  83  Linux
/dev/sda9            6563        8733    17438526   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x075b075a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb3               1        3649    29310561    5  Extended
/dev/sdb5               1        3649    29310529+  83  Linux

Disk /dev/sdc: 20.4 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007163f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1085     8715231   83  Linux
/dev/sdc2            1086        1346     2096482+  82  Linux swap / Solaris
/dev/sdc3            1347        2491     9197212+  83  Linux




studio@studio:~$ sudo blkid
[sudo] password for studio: 
/dev/sda1: UUID="E09446D79446B038" TYPE="ntfs" 
/dev/sda5: UUID="f90456a5-a292-4cef-85f7-2f96847ffe5f" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda6: UUID="e9cc487c-4843-4ab4-92ac-11ced150d6e0" TYPE="ext3" 
/dev/sda7: UUID="89172d89-7863-443c-b581-3dad89da1e1e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: UUID="3bad0d0e-ce83-40c3-8968-9f603eea326a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda9: UUID="0a40181a-e70c-481c-b206-fa75aaded0ae" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="cda041b9-e2dd-49fb-82f7-a6404b6ad4a2" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sdc1: UUID="6cf51156-47e2-41f1-abc5-84ce038ef287" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc2: TYPE="swap" UUID="64a4edbe-c867-4f03-adaa-6a27b3813f7f" 
/dev/sdc3: UUID="3bad0d0e-ce83-40c3-8968-9f603eea326a" SEC_TYPE="ext2" TYPE="ext3" 
studio@studio:~$

---

### Post by iaculallad on 2008-09-03
Instead of using blkid command, use:

```
ls -la /dev/disk/by-uuid
```

and compare the result with your current UUID's

---

### Post by sisco311 on 2008-09-03
you can set a new uuid with:
```
sudo tune2fs -U random /dev/sd**XY**
```

---

### Post by drs305 on 2008-09-03
Here are a couple of things to consider.

The blkid command now returns accurate UUIDs, but just to eliminate the possibility of it using outdated cache information, try running this command:
```
sudo blkid -c /dev/null
```
That will provide 'fresh' information.

You can change the UUID of a partition with tune2fs. Pick the partition least important to you, and back up the data if possible.

Read about tune2fs in its man page, but the command possible command to generate a random UUID would be:
```
sudo tune2fs -U random /dev/sd**c3**
```

If you do this, don't forget to update your fstab.

---

### Post by texasjim on 2008-09-03
Thanks for the prompt answer.
SDC3 is not in the list:

studio@studio:~$ sudo ls -la /dev/disk/by-uuid
[sudo] password for studio: 
total 0
drwxr-xr-x 2 root root 220 2008-09-03 18:01 .
drwxr-xr-x 5 root root 100 2008-09-03 13:01 ..
lrwxrwxrwx 1 root root  10 2008-09-03 13:01 0a40181a-e70c-481c-b206-fa75aaded0ae -> ../../sda9
lrwxrwxrwx 1 root root  10 2008-09-03 18:01 3bad0d0e-ce83-40c3-8968-9f603eea326a -> ../../sda8
lrwxrwxrwx 1 root root  10 2008-09-03 13:01 64a4edbe-c867-4f03-adaa-6a27b3813f7f -> ../../sdc2
lrwxrwxrwx 1 root root  10 2008-09-03 13:01 6cf51156-47e2-41f1-abc5-84ce038ef287 -> ../../sdc1
lrwxrwxrwx 1 root root  10 2008-09-03 13:01 89172d89-7863-443c-b581-3dad89da1e1e -> ../../sda7
lrwxrwxrwx 1 root root  10 2008-09-03 13:01 cda041b9-e2dd-49fb-82f7-a6404b6ad4a2 -> ../../sdb5
lrwxrwxrwx 1 root root  10 2008-09-03 13:01 E09446D79446B038 -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-09-03 13:01 e9cc487c-4843-4ab4-92ac-11ced150d6e0 -> ../../sda6
lrwxrwxrwx 1 root root  10 2008-09-03 13:01 f90456a5-a292-4cef-85f7-2f96847ffe5f -> ../../sda5
studio@studio:~$

---

### Post by drs305 on 2008-09-03
/dev/sdc3 was just an example. You would change that to the designation of whatever the partition was you wished to change. Sorry I wasn't clearer.

---

### Post by texasjim on 2008-09-03
Thanks to all, I'm markin' this one Solved.
The "sudo tune2fs -U random /dev/sdc3" command did it, 
sdc3 was a disposable partition I was getting ready 
to try dragonfly-bsd in, but I wanted it right before
I clobbered it.

  Jim Hayes

---

