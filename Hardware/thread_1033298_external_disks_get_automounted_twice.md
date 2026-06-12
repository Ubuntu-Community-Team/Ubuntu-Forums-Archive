---
title: "external disks get automounted twice"
date: 2009-01-07
forum: Hardware
---

### Post by morbid88 on 2009-01-07
I have something strange going on.
I installed xubuntu using unetbootin.

Since unetbootin ends up with an extra entry in fstab, I commented this out (it accidentally mounts usb-disks as cdroms, for some reason, and prevents their automounting afterwards.)

But now, every time I put in a cd (blank or written), or a usb disk, I get two windows popping open. I don't know if this is Thunar doing it, or a problem with fstab...

Anyone familiar with this?
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=04ae1336-3eb1-4c7b-bafd-80025ac4631f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=cbc51b5c-0e4d-46cd-aba4-e6f4ea4928f5 /home           ext3    relatime        0       2
# /dev/sda1
UUID=52A49DC2A49DA94D /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=91542869-a36e-404b-b73b-2ff744d80fec none            swap    sw              0       0
#/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

