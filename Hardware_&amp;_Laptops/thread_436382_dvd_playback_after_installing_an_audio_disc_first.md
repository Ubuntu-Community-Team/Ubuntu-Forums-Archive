---
title: "dvd playback after installing an audio disc first"
date: 2007-05-07
forum: Hardware &amp; Laptops
---

### Post by cjae on 2007-05-07
Hi, I can't get xdvdshrink to work I can't get any media player to recognize a dvd (and yes libdvdcss is installed) until I put in an audio disc first and then remove and enter a dvd.

There seem to be other people with this issue since breezy badger.

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda3
UUID=a2f2fd63-4f00-45ec-aafc-391988a8832e / ext3 defaults,errors=remount-ro 0 1
# /dev/sdb1
UUID=493c8f10-ef59-4234-8a5d-f2ffc55d4239 /home ext3 defaults 0 2
# /dev/sda1
UUID=CC341DB4341DA28E /windows ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda2
UUID=79016249-13ca-4468-8ec8-c42e67ec5a65 none swap sw 0 0
/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto 0 0

uname -r
2.6.20-15-generic
xubuntu 7.04

[https://bugs.launchpad.net/bugs/27316](https://bugs.launchpad.net/bugs/27316)

---

