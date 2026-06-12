---
title: "fstab repeat"
date: 2009-07-28
forum: Hardware
---

### Post by tir38 on 2009-07-28
Hi can anyone tell me why sda1 and sda5 are showing up twice in my fstab?

root@black:/home/jason# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda1
UUID=7a5d71ae-06d8-4c90-9b96-0a999f6eaec1  /              ext3         relatime,errors=remount-ro  0  1  
# /dev/sda5
UUID=307df195-65d0-41de-8fef-b972ae4d41d7  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  


/dev/sdb1                                  /media/shared  ntfs         nls=iso8859-1,umask=000,ro  0  0  
/dev/sda1                                  /media/sda1    ext3         defaults                    0  0  
/dev/sda5                                  /media/sda5    swap         defaults                    0  0

---

