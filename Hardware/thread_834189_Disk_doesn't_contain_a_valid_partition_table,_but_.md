---
title: "Disk doesn't contain a valid partition table, but Ubuntu can still see files on disk"
date: 2008-06-19
forum: Hardware
---

### Post by sohanley on 2008-06-19
Beginning with the upgrade to Hardy Heron in April, I've had a recurring problem where, approximately every other time I boot up my PC, Ubuntu doesn't detect one of my drives. I believe the issue may be related to Hardy renaming disks in an inconsistent manner, but honestly I'm not sure. My setup is like this:

1. a 160GB SATA ext3 disk which is where Ubuntu resides. mounts to /. also has a swap partition on it, which I've noticed is NOT activated (running 'free -m' shows I have no swap spcae).

2. a 300GB IDE ext3 disk which is the main problem. supposed to mount to /music. Every other time I boot, I get the following error (which leaves me in a root shell, and I can hit Ctrl+D to continue booting): ```
fsck.ext3: Device or resource busy while trying to open /dev/sda. Filesystem mounted or opened exclusively by another program? fsck died with exit status 0.
```


3. a 120GB IDE ext3 disk which also doesn't appear to mount properly approximately every other time I boot. supposed to mount to /movies.

Here is my /etc/fstab. I'm not sure why the partition that's supposed to mount to /music is listed as /dev/sda, but I think that's part of the problem:

```
# /etc/fstab: static file system information.
#
# <file sys> <mount point> <type>      <options>               <dump> <pass>
proc       /proc          proc         defaults                    0  0
/dev/sda1  /              ext3         defaults,errors=remount-ro  0  1
/dev/sda5  none           swap         sw                          0  0
/dev/cdrom   /media/cdrom0  udf,iso9660  user,noauto                 0  0
/dev/hdd   /media/cdrom0  udf,iso9660  user,noauto                 0  0
/dev/sda   /music         ext3         defaults,errors=remount-ro  0  1
/dev/sdb1  /movies        ext3         defaults,errors=remount-ro  0  0
/dev/sdb2  /mnt/ipod      vfat         user,noauto,umask=000       0  0

```

And here's fdisk -l:

```
Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x77c177c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   234435599   117217768+  83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5644cdaf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   308030309   154015123+  83  Linux
/dev/sdc2       308030310   312576704     2273197+   5  Extended
/dev/sdc5       308030373   312576704     2273166   82  Linux swap / Solaris
Note: sector size is 2048 (not 512)

```

As you can see, the disk I want to boot from (and did, in fact, boot from) is /dev/sdc. Meanwhile, /dev/sda has a Disk Identifier of 0x00000000 (doesn't seem right to me) and also doesn't contain a valid partition table.

I'm kind of lost and quite confused here. If the disk in question doesn't contain a valid partition table, how is it that it works fine every other time I reboot? (I've checked fdisk when it mounts fine, and fdisk still says that the disk doesn't contain a valid partition table) Also, why isn't my primary disk (the 160GB SATA which has Ubuntu on it) loading as /dev/sda, and instead is loading as /dev/sdc?

Most importantly, how do I fix this without losing my data? Any help is much appreciated.

---

### Post by stabu on 2008-07-03
this could be an lvm problem. 
try "apt-get install lvm2" and then rebooting.

---

