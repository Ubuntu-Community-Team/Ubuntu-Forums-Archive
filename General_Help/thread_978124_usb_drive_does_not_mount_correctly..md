---
title: "usb drive does not mount correctly."
date: 2008-11-10
forum: General Help
---

### Post by lhong1987 on 2008-11-10
first of all, here is my fstab.
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d8e22541-f9d9-48d7-8d0b-bf77be8ab460 /               ext3    noatime,errors=remount-ro 0       1
# /dev/sda5
UUID=291695cf-4140-88aa-550b-707a4f74bc01 none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
tmpfs /var/tmp tmpfs defaults,noatime,mode=1777 0 0
tmpfs /var/log tmpfs defaults,noatime,mode=0755 0 0 
tmpfs /var/log/apt tmpfs defaults,noatime 0 0
none /var/cache unionfs dirs=/tmp:/var/cache=ro 0 0

whenever I connect WD passport drive to the usb port, i get an error message saying that i need to be superuser to mount.
i followed the instruction to modify fstab for i use SSD and wanted to minimize disk write/erase.
I have also installed the OS (ubuntu eee) via usb drive, i don't know if that does anything though.
thank you in advance.

---

