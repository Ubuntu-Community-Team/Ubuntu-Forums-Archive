---
title: "USB ports work, then dont tx1000"
date: 2008-03-27
forum: Hardware &amp; Laptops
---

### Post by confuded92 on 2008-03-27
i have a tx1340ea. USB ports worked in the beginning. After some time (installing soft and updates) they stopped working after a certain amount of time. Now they don't work at all! When I say they don't work I mean Ubuntu does not recognize them, auto mount them. I think it has to do something with the AMD hammer nVidia chip set...  I think the contents of my fstab might help:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1 - didnt touch this one
UUID=d63a161d-7c52-4ff1-bf4f-a990d9ad4993 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2 - the home directory 
/dev/sda2	/home	ext3	nodev,nosuid	0	2
# /dev/sda3
/dev/sda3	/media/WindowsXP     ntfs-3g    user,auto,fmask-0177,dmask=0077,uid=1000 0       0
# /dev/sda5 - the swap
/dev/sda5	none            swap    sw              0       0
#the hp recovery partition on /dev/sda6 - doesnt mount for some reason
/dev/sda6	/media/HP_RECOVERY     ntfs-3g    user,auto,fmask-0177,dmask=0077,uid=1000 0       0
#cdrom? havent touched this one either...
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

#ok 'blkid /dev/sdaX/ gives the UID 
```

Thank you!

~confuded

---

### Post by dudafmendes on 2008-06-11
I have the same problem, after a while the kernel only recognizes usb devices when booting, then the usb detection stops working.

The problem is not that the system doesn't mount the device, it does not recognize at all. After plugging the device, lsusb does not detect a new usb device connected.

Does anyone have a sugestion?

Duda.

---

