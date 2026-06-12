---
title: "Noob trying to automount"
date: 2008-08-11
forum: Hardware
---

### Post by zcartist on 2008-08-11
Hi

I have an hp. I dualbooted it 40/60 ubu/vista. It has 2 320 gb sata's. There's about 140 gb partioned on the primary & 140 on the other.

1. I noticed there is another file system on the second drive. How much of that do I need? It almost seems to be the same as the primary drive file system.

2.Can someone walk me through the automount of that second drive? It seems like theres three patitions just for hp on the primary drive. I'm not real sure which drive I want. There seems to be about 5.

3 On the second drive and an external I have the files can only be deleted theres no trash how do I fix that?

Thanks

---

### Post by wolfen69 on 2008-08-11
open a terminal and do
```
sudo fdisk -l
``` then we can go from there.

> 3 On the second drive and an external I have the files can only be deleted theres no trash how do I fix that?
you can do ctrl-h to show hidden files. then look for the .trash directory. then empty it.

---

### Post by zcartist on 2008-08-11
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe9e67578

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       22465   180450081    7  HPFS/NTFS
/dev/sda2           37730       38913     9510480    7  HPFS/NTFS
/dev/sda3           22466       37729   122608080    5  Extended
/dev/sda5           22466       37103   117579703+  83  Linux
/dev/sda6           37104       37729     5028313+  82  Linux swap / Solaris

Partition table entries are not in disk order



Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x17df5057

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19699   158232186    7  HPFS/NTFS
/dev/sdb2   *       19700       38128   148030942+  83  Linux
/dev/sdb3           38129       38913     6305512+   5  Extended
/dev/sdb5           38129       38913     6305481   82  Linux swap / Solaris
z@z-desktop:~$


For part 3 I can't move files in the trash only delete not sure why its not an option to trash

---

### Post by wolfen69 on 2008-08-11
post the output of ```
cat /etc/fstab
```

---

### Post by zcartist on 2008-08-11
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=be596469-e300-4564-88c8-a50a392072dd /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=6df9f2bd-eaa6-4b35-98fa-c30d51f61e20 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by zcartist on 2008-08-15
ideas?

---

### Post by zcartist on 2008-09-09
The drive I want to automount  shows up as 'Disk" if that helps

---

