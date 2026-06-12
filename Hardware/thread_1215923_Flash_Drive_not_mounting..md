---
title: "Flash Drive not mounting."
date: 2009-07-17
forum: Hardware
---

### Post by MXIIA on 2009-07-17
I have a cruzer U3 flash drive that is not mounting, I can remember a time when it did mount, not to long ago, and I do not recall editing any settings that might have interfered with it.

I attached the error that pops up when I insert the flash drive, as well as my /etc/fstab file.

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=d2cc20a2-6fbb-42a6-bf27-f5a13a5bfb17 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=6c13af9a-db5d-49c6-9847-73aa9250db8b none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by dlmarti on 2009-07-17
[http://howtoxyz.blogspot.com/2008/07/how-to-mountpoint-cannot-contain.html](http://howtoxyz.blogspot.com/2008/07/how-to-mountpoint-cannot-contain.html)

---

### Post by MXIIA on 2009-07-17
Thank you! That worked perfectly!

---

