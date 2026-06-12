---
title: "ext3 commit interval"
date: 2008-11-21
forum: General Help
---

### Post by JNelson on 2008-11-21
Hi
I bought an eee PC. I am trying to get ext3 to commit every 30 seconds but it keeps mounting every 5 here is my fstab.


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=39d566d8-5553-4628-a81a-dd16f543f89e /               ext3     defaults,noatime,nodiratime,errors=remount-ro,commit=30 0       1
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

