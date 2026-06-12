---
title: "DVD Datadisc not mounting"
date: 2007-09-06
forum: Hardware &amp; Laptops
---

### Post by dvvb on 2007-09-06
With Ubuntu 7.0.4, My dvd drive works fine with CD data disks, dvd video disks. When I create DVD data disk using k3b(option linux/unix+Windows support), it doesn't mount. It errors out with msg. "Unable to mount device. Invalid Mount option".

I checked /etc/fstab:

/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0

ls -l /dev/hd* shows  hdb cdrom

CD Data disk works, dvd video works, dvd data disk doesn't work.

Is there something I need to change ?

Thanks
-VB

---

