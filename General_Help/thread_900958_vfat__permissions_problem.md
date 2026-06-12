---
title: "vfat  permissions problem"
date: 2008-08-25
forum: General Help
---

### Post by weemstra on 2008-08-25
hello,

I'm busy quite a long time now, but I can't solve a very annoying problem.
I hav 2 FAT32 partitions under Windows (dual boot machine) and I have mounted them in my home folder in linux, but I cannot get the rw permissions right and I don't know what is the problem.


this the outcome of sudo fdisk -l


[I]
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe02ae02a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5004    40194598+   7  HPFS/NTFS
/dev/sda2            5005        9529    36347062+  83  Linux
/dev/sda3            9530        9729     1606500    5  Extended
/dev/sda5            9530        9729     1606468+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7ef3fba2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       25496   204796588+   7  HPFS/NTFS
/dev/sdb2           25497       29575    32764567+   c  W95 FAT32 (LBA)
/dev/sdb3           29576       33654    32764567+   c  W95 FAT32 (LBA)

Disk /dev/sdc: 2063 MB, 2063597568 bytes
16 heads, 32 sectors/track, 7872 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        7872     2015216    e  W95 FAT16 (LBA)[/I]



And this is how my /etc/fstab looks at the moment:



[I]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=c32a1995-e402-4249-b77b-9d8a3fb4a973 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=03427efe-3776-4864-919f-9e96db0dc593 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
# WINDOWS, NTFS, Mijn documenten
/dev/sdb1       /home/kees/MIJN_DOCUMENTEN      ntfs    defaults
# WINDOWS, FAT32, FILMS
/dev/sdb2       /home/kees/FAT_FILMS    vfat    uid=kees,umask=077 0 0
# WINDOWS, FAT32, SERIES
/dev/sdb3       /home/kees/FAT_SERIES    vfat   uid=kees,umask=077 0 0
[/I]



As you can see, I have a NTFS partition as well, but no problems with that.
Does anyone has a smart suggestion.
It would be much appreciated!!

---

### Post by iaculallad on 2008-08-25
Instead of using:

```
# WINDOWS, FAT32, FILMS
/dev/sdb2 /home/kees/FAT_FILMS vfat uid=kees,umask=077 0 0
# WINDOWS, FAT32, SERIES
/dev/sdb3 /home/kees/FAT_SERIES vfat uid=kees,umask=077 0 0

```

Try:

```
/dev/sdb2   /home/kees/FAT_FILMS     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sdb3   /home/kees/FAT_SERIES     vfat    defaults,utf8,umask=007,gid=46 0       1
```

Copy and Paste it on your fstab file, commenting/deleting your first configuration.

---

