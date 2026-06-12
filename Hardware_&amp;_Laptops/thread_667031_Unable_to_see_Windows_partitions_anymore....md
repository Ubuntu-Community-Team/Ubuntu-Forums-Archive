---
title: "Unable to see Windows partitions anymore..."
date: 2008-01-13
forum: Hardware &amp; Laptops
---

### Post by Zambini on 2008-01-13
I recently updated from 6.06 all the way to 7.10 and I can no longer see my windows partitions.

fdisk -l  

```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbac32136

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         784     6297448+  12  Compaq diagnostics
/dev/sda2   *         785       10249    76025752+   7  HPFS/NTFS
/dev/sda3           10250       12063    14570955   83  Linux
/dev/sda4           12064       12161      787185   82  Linux swap / Solaris
ryan@ryan-laptop:~$ 

```


my original fstab listed this

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3 / ext3 defaults,errors=remount-ro 0 1
/dev/hda1 /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
/dev/hda2 /media/hda2 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
/dev/hda4 none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

so I changed them to be sda1-4, now I have this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3 / ext3 defaults,errors=remount-ro 0 1
/dev/sda1 /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
/dev/sda2 /media/sda2 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
/dev/sda4 none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

but when I try and "sudo mount -a" it returns this:

```
fuse: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/sda1 ()
fuse: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/sda2 ()

```


And I'm stuck. I can't figure what to do and I've been fruitlessly searching google for an hour or so.

---

### Post by Zambini on 2008-01-14
So I did some googling of a big error message I got while X crashed, and the fix was this:

```
sudo aptitude remove evms

```

Removing EVMS fixed it, and now I can see my Windows hard drives, and my fstab config works perfectly

---

