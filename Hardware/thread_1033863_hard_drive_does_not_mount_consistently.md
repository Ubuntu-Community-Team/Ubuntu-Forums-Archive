---
title: "hard drive does not mount consistently"
date: 2009-01-07
forum: Hardware
---

### Post by frankups1 on 2009-01-07
i have three hard drive in my computer running ubuntu 8.10. 
they are /dev/sdc, /dev/sda, /dev/sdb. sdc is for ubuntu and sda and sdb are for file sharing/storage.  for some reason when i reboot the system sdb gets mounted as the root. here is a copy of /etc/fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=04c86b82-cbc9-471a-94f5-c31c4deeccdc /               ext3    relatime,erro$

# /dev/sdc5
UUID=a29bc68a-fe01-43bd-75df-63c5fd34c44a none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /ftp www
/var/www        /home/frankfimmano/var/www_dev  none    bind    0       0
# /dev/sda1
/dev/sda1       /mnt/sda1       ext3    defaults        0       2
#/dev/sdb1
/dev/sdb1       /mnt/sdb1       ext3    defaults        0       3

i have tried all that i could think of and followed every tutorial i could find i can get the disks to mount right until i reboot the system.

---

### Post by taurus on 2009-01-07
You can edit /etc/fstab and replace the /dev/sda1 & /dev/sdb1 with the UUIDs.

```
sudo blkid
```

---

### Post by frankups1 on 2009-01-07
i had the UUID's there first, when i rebooted it changed /dev/sdb and /dev/sdc to the same uuid. does it matter that sdc is ide and sda and sdb are sata?

---

