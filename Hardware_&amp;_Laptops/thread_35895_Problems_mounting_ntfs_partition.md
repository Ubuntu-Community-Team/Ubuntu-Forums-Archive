---
title: "Problems mounting ntfs partition"
date: 2005-05-20
forum: Hardware &amp; Laptops
---

### Post by blahpro on 2005-05-20
Hi all,

I `converted` to ubuntu a while ago but yesterday i finally decided to ditch XP for most things and go ubuntu full time. Ubuntu is installed on partition hda5 and my main windows installation is on hda1.

All my files (mydocs, music, etc etc) are on another ntfs partition, hdb1 (which I want too mount to /x). However, "mount -t ntfs /dev/hdb1 /x" gives me an error:

mount: /dev/hdb1 already mounted or /x busy

"mount" gives me this:

root@hod-dt-002:~ # mount
/dev/hda5 on / type reiserfs (rw,notail)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)

...so i know its not already mounted. Any ideas?

Thanks,
Ben Hodgson

---

### Post by blahpro on 2005-05-20
Ok, I've found that the disk has bad blocks. This is possibly why it doesnt let me mount it. Does anyone know how I can fix this?

Thanks,
Ben

---

