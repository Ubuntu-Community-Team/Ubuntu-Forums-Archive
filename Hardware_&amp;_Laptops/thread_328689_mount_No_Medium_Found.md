---
title: "mount: No Medium Found"
date: 2006-12-31
forum: Hardware &amp; Laptops
---

### Post by sonusandhu on 2006-12-31
My DVD RW is not working in ubuntu 6.10.The DVD RW works fine in windows xp. when i try to access them, i get the following error.
"Mount: No Medium Found"
My fstab file is as follows.
```
khalsa% cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=d1151591-9c82-43e8-8037-0b137dc13241 /               reiserfs notail          0       1
# /dev/sda4
UUID=4588-4063  /media/D     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sdb2       /media/ipod     vfat    rw      0       0
# /dev/sda5
UUID=a1df8e75-2203-400d-a369-96a12e8d1be9 none            swap    sw              0       0
/dev/hda        /media/cd   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cd   udf,iso9660 user,noauto     0       0
```

---

### Post by aidanr on 2006-12-31
it says there that hda and hdb are both mounted to /media/cd, this might be normal i'm not sure, but just incase it isn't try making a directory /media/dvd and changing the mountpoint of the dvd drive to that

---

### Post by sonusandhu on 2006-12-31
thanks for reply.my latest fstab is as follows
```
khalsa% cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=d1151591-9c82-43e8-8037-0b137dc13241 /               reiserfs notail          0       1
# /dev/sda4
UUID=4588-4063  /media/D     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sdb2       /media/ipod     vfat    rw      0       0
# /dev/sda5
UUID=a1df8e75-2203-400d-a369-96a12e8d1be9 none            swap    sw              0       0
/dev/hda        /media/dvd   udf,iso9660 user,auto     0       0
/dev/hdb        /media/cd   udf,iso9660 user,noauto     0       0

```

---

