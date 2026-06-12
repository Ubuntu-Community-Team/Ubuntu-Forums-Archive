---
title: "/dev/hdc is not a valid block device"
date: 2006-03-18
forum: Hardware &amp; Laptops
---

### Post by sulien on 2006-03-18
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>      <dump> <pass>
proc            /proc           proc    defaults        0       0
/dev/hda        /               ext3    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/fd0        /media/floppy   auto    rw,user,noauto  0       0
/dev/hdb        /mnt            reiserfs defaults       0       0
/dev/hdb1       /mnt            reiserfs defaults       0       0
/dev/hdb5       /mnt            swap     defaults       0       0
/dev/hdc        /media/cdrom   iso9660    ro,noauto,user,exec 0   0
/dev/hdd        /media/dvdrom0  iso9660 ro,noauto,user,exec 0    0


Can someone explain to me whythis is so? I used sudo MAKEDEV hdc in /dev which worked. So what's the problem? I tried auto instead of iso9660 but it reported the same result.

---

### Post by virgule on 2006-03-18
Here come my cdrom line from my fstab file. I have **ufd,iso9660** but you don't? ::scratch head::
```

/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

