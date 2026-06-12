---
title: "Can't Find External HD"
date: 2010-03-11
forum: Hardware
---

### Post by runr140 on 2010-03-11
I'm a bit new to linux and I just installed Xubuntu 9.10 on my server computer at home.  Everything looks good except Xubuntu can't find my storage drive, so I can't get all my files back.  Details:

- Xubuntu installed on WD 80GB drive.  Works fine, shows in Fstab, etc.
- 200GB storage drive connected on 80 wire IDE cable.  Shows up in BIOS as Primary IDE Slave, shows up in /dev/disk/by-id but not by-label, by-path, or by-uid.  Fstab doesn't show it either.  Fstab shows:

#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=8a9b56b1-b0d0-4f9b-8404-f60a31a29d88 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=77703fc0-a46e-4c7f-9c6c-8bfb7cf14b88 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


Any help would be appreciated.

runr140

---

### Post by Barriehie on 2010-03-11
Does it show up when you:
```

sudo fdisk -l
```or:
```

gksu gparted
```

---

