---
title: "My Filesystem or Drive's Setup"
date: 2005-11-21
forum: General Help
---

### Post by Drifter on 2005-11-21
Look at this and tell me how I can get gnucash and dvdshrink to see my dvd drive.
I have wine and all the plugins.  I can use the players with my movie's but I can't use dvdshrink and I can't get gnucash to see my drive.  Help me if u can thanks.


# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hdb1 / ext3 defaults,errors=remount-ro 0 1
/dev/hdb5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/sda /media/usb0 auto rw,user,noauto 0 0

---

### Post by Drifter on 2005-11-22
Am I invisible or what

---

