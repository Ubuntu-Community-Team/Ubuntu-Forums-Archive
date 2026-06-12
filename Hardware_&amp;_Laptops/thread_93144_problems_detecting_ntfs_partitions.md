---
title: "problems detecting ntfs partitions"
date: 2005-11-21
forum: Hardware &amp; Laptops
---

### Post by proxess on 2005-11-21
Ive got 2 NTFS partitions (different HDDs). On one linux doesn't detect all the files, and the other is unmountable (acording to the disks manager the file sistem is unknown).

this is what my fstab looks like:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/hdb5	/mnt/D		ntfs	users,uid=1000,ro	0	0
/dev/hda	/mnt/c		ntfs	users,uid=1000,ro	0	0

```

this is the output of when i do sudo mount -a:
```
proxess@PrXss:~$ sudo mount -a
mount: /dev/hda already mounted or /mnt/c busy
```

and strangely enough this is what i got from sudo fdisk -l
```
proxess@PrXss:~$ sudo fdisk -l

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4997    40138371    7  HPFS/NTFS

Disk /dev/hdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               2       17380   139596817+   f  W95 Ext'd (LBA)
/dev/hdb2   *       17381       19929    20474842+  83  Linux
/dev/hdb5               2       17267   138689113+   7  HPFS/NTFS
/dev/hdb6           17268       17380      907641   82  Linux swap / Solaris

```

As you can see hdb5 and hda1 are my ntfs partitions.

I just want to at least read the partitions again. All the files on them. Any solution? Im running Ubuntu 5.10: Breezy Badger, Kernel 2.6.14.2

-Proxess

---

### Post by MarcDM on 2005-11-21
This is what your /etc/fstab should look like :
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/hdb5	/mnt/D  ntfs  user,uid=1000,gid=1000,umask=0222  0  0
/dev/hda	/mnt/c  ntfs  user,uid=1000,gid=1000,umask=0222  0  0

```

Works for me. 

----
Hope This helps.

---

### Post by proxess on 2005-11-25
this one WORKED for me, i recently formated my ubuntu partition and compiled a new kernel. maybe its because of that??

---

