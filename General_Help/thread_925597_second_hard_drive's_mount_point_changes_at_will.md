---
title: "second hard drive's mount point changes at will"
date: 2008-09-20
forum: General Help
---

### Post by boandmichele on 2008-09-20
i set my new second hard drive to mount at /media/750gb.  yet every few reboots or so, it changes to /media/disk.  its always changing back and forth, and i need to constantly adjust my pytivo.conf file.  any ideas on what is causing this, and what i could do to fix it?  its very frustrating, as my pyTivo is continuously crippled.  :(

pytivo is below:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=56231b10-75df-4566-97ff-1a87d534f795 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=aba72626-4255-4b88-9fe9-a840683377e1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdc1       /media/750gb    ext3 defaults 0 0
```

---

