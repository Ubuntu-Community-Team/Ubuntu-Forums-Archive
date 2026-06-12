---
title: "Mount DVD-Writer"
date: 2008-07-31
forum: Hardware
---

### Post by scottyf11 on 2008-07-31
Hello,

I am unable to get my external usb dvd writer to mount.  I am new to linux so hopefully it is something easy.  I've searched around, and found out that the contents of fstab is important.

Here is mine
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b55e90ff-7466-48b9-ae1a-36a2646aec7c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=9f27196d-692e-4401-aa81-b057a8eb9600 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

I have one internal cd drive which works fine, but my external one does not.

Thanks,
Scott

---

