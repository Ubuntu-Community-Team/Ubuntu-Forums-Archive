---
title: "Mounting problems"
date: 2008-09-28
forum: Hardware
---

### Post by Kolmogorov on 2008-09-28
Hi everyone,

I have some trouble to mount my new usb external hard drive with Ubuntu 8.04. I have two external hard drives, one of 40 gig and one of 1TB (the new one). I used gparted to format the 1TB hard drive with a ext3 filesystem. I can't mount it properly...

That's what i got:

```
steeve@steeve-laptop:~$ cd /media
steeve@steeve-laptop:/media$ ls
cdrom  cdrom0  EULER  LACIE
steeve@steeve-laptop:/media$ 

```

Euler = 40 gigs HD and LACIE = 1TB HD.

Now, 

```
steeve@steeve-laptop:/media$ sudo fdisk -l
[sudo] password for steeve: 

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbc4bbc4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11918    95731303+  83  Linux
/dev/sda2           11919       12161     1951897+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005e4f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux

Disk /dev/sdc: 40.0 GB, 40007761920 bytes
240 heads, 63 sectors/track, 5168 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x32570eef

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        5168    39070048+   c  W95 FAT32 (LBA)
steeve@steeve-laptop:/media$ 
```

So, if i understand this, Ubuntu see the three HDs with

sda1 = 95 gigs (ext3)
sda2 = 2 gigs (linux-swap)
sdb1 = 1TB (ext3)
sdc1 = 40 gigs (fat32)

Now, if i do the following:
```
steeve@steeve-laptop:/media$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9a3dea7a-e68f-44b5-a2ae-75acc2ef5a79 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=39f3993d-4a0a-4060-a852-04f5f00463b4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
steeve@steeve-laptop:/media$ 
```

I don't see my 1TB HD !

I create a LACIE folder in /media and mount my HD with:
```
steeve@steeve-laptop:/media$ sudo mount -t ext3 /dev/sdb1 /media/LACIE/
steeve@steeve-laptop:/media$ ls
cdrom  cdrom0  EULER  LACIE

```

but i can't create any folder in this HD...it say that the owner is the root, not me...even if i change the owner, with 

```

steeve@steeve-laptop:/media$ sudo chown -R steeve /media/LACIE/

```

This doesn't work...

Any ideas ?

---

### Post by olejorgen on 2008-09-29
1. Automounting does not work?
2. Try to umount, chown the mountpoint, and remount

---

