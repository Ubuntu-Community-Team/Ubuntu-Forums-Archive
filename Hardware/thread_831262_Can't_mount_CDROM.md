---
title: "Can't mount CDROM"
date: 2008-06-16
forum: Hardware
---

### Post by Monkey22 on 2008-06-16
I've scoured the internet and it seems this problem has come up many times before, but none of the solutions offered helped me. I have a Lenovo 3000 n200 and am running Gutsy. My cd/dvd drive works during boot (I can boot using the Live CD) but as soon as I try to mount the CD when logged on it gives:


mount: special device /dev/scd0 does not exist


so I went into /dev and found that indeed it did not exist, but I had sda, which I was told was the one I had to use for mounting instead of /dev/scd. So i tried the command (cant remember what it was now) and then it said. 

mount: /dev/sda already mounted or /media/cdrom busy


And I'm a relative newb so try to keep thing simple if you can. Thanks!

(And if you saw this n another thread, just ignore that one because I realised it was the wrong place to put it)

EDIT: o yeah and fstab:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d08dfc8c-451a-410b-80f1-e742d880928b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=ce3fd8fa-3041-40f8-9d75-09ee511823d9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

