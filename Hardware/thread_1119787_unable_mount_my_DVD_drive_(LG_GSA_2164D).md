---
title: "unable mount my DVD drive (LG GSA 2164D)"
date: 2009-04-08
forum: Hardware
---

### Post by tallgingerperson72 on 2009-04-08
hi i can't mount my DVD drive here is my 
FSTAB

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3e131947-3ab5-49df-b6e2-e886df913ec9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=7547d25e-b5d9-4f92-b88e-e3bb68968d98 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

