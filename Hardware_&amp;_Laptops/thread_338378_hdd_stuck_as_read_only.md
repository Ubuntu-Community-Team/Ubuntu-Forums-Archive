---
title: "hdd stuck as read only"
date: 2007-01-14
forum: Hardware &amp; Laptops
---

### Post by goodall on 2007-01-14
hey i have an external hdd formatted as vfat, it shows up at the correct mount point, however i cannot copy any files onto it, i get told that it is a read only disk, and that the owner is root, so i do a sudo nautilus, try it again and its stuck on read only, i cant change any permissions on it at all or copy files to it, 

here is my fstab entry

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/mapper/Ubuntu-swap_1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb1       /home/goodall/storage	vfat	rw,user,auto	0	0

```

can anyone help?

---

### Post by taurus on 2007-01-14
Personally, I would do something like this with that drive in /etc/fstab.

```
/dev/sdb1   /media/sdb1   vfat   iocharset=utf8,umask=000   0   0
```
Then, create a mount point for it.

```
sudo mkdir /media/sdb1
```
Reboot.

---

### Post by goodall on 2007-01-15
Done, but still get the same problem, although the permissions have changed, which is great, the disk is still read only.

---

