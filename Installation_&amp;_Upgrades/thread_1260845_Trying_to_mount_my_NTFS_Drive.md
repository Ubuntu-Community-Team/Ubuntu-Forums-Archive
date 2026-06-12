---
title: "Trying to mount my NTFS Drive"
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by moe458 on 2009-09-08
Hi,

While I managed to mount my NTFS partitions, I cannot get my hard drive with the SFS filesystem to mount. Here's what I've done so far:

Linux moe-desktop 2.6.28-15-generic #51-Ubuntu SMP Mon Aug 31 13:33:16 UTC 2009 i686 GNU/Linux


sudo fdisk -l

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x781aa014
**/dev/sdb1 1 24321 195358401 42 SFS**


sudo gedit /etc/fstab
added the below line:
**/dev/sdb1 /media/sdb sfs umask=0222 0 0**

sudo mount -a
[COLOR="Red"]mount: unknown filesystem type 'sfs' [/COLOR]


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=abda2db5-cf62-4994-a550-5b33eadd49c3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb2
UUID=7524238e-7572-419d-a7c1-e8286c64ee2b /boot           ext3    relatime        0       2
# /dev/sdb3
UUID=80eb62a5-d8ff-41ef-ac96-35917618b5d6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1       /media/sdb sfs   umask=0222 0 0 
```

here is my fdisk -l
```
root@moe-desktop:~# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x529e3a04

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321   42  SFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x781aa014

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   42  SFS

Disk /dev/sdc: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x360c360c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3649    29310561    7  HPFS/NTFS

Disk /dev/sdd: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08550854

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        2117    17004771   83  Linux
/dev/sdd2            2118        2178      489982+  83  Linux
/dev/sdd3            2179        2482     2441880   82  Linux swap / Solaris
root@moe-desktop:~# 

```

---

### Post by moe458 on 2009-09-08
seems like i found some answer to my question here:
[http://www.linuxforums.org/forum/linux-newbie/4013-sfs-mount.html]("http://www.linuxforums.org/forum/linux-newbie/4013-sfs-mount.html")

---

