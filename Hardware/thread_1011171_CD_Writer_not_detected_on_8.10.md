---
title: "CD Writer not detected on 8.10"
date: 2008-12-14
forum: Hardware
---

### Post by ahvi on 2008-12-14
OK, so in the short time that I've been using 8.10, my cd writer drive has disappeared. A while ago I installed CDemu and all of those virtual drives work perfectly. I don't believe CDemu to be interfering with the drive.

Here's my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb6
UUID=25a8beab-4608-451d-a058-894fbb903c96 /     ext3    relatime,errors=remount-ro 0 0
# /dev/sdb3
/dev/sdb3               none                    swap    sw              0 0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0                /media/floppy0  autorw,user,noauto,exec,utf8    0 0
/dev/sda1               /home                   ext3    nodev,nosuid    0 0

```

It doesn't seem to appear in fstab or df:
```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb6             25397140   4662516  19454648  20% /
tmpfs                  1035944         0   1035944   0% /lib/init/rw
varrun                 1035944       216   1035728   1% /var/run
varlock                1035944         0   1035944   0% /var/lock
udev                   1035944      2820   1033124   1% /dev
tmpfs                  1035944       296   1035648   1% /dev/shm
lrm                    1035944      2000   1033944   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda1            240355200 235857864   2055376 100% /home

```

I also can't seem to find anything in /dev

I know the CD drive works, because it works perfectly in my backup Linux Mint partition.

I appreciate any help in advance.

---

### Post by ahvi on 2009-01-01
Any hints? Guesses?

---

