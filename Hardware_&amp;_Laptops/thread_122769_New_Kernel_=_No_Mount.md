---
title: "New Kernel = No Mount?"
date: 2006-01-28
forum: Hardware &amp; Laptops
---

### Post by thewonka on 2006-01-28
Hi! i have this problem when ever i build and install a kernel newer that the ubuntu supplied linux-source-2.6.12, i have tried every kernel from rev from 2.6.13 to 2.6.15 with the same result.

I can't mount my storage drive!!! lol

the system recognized that the an EXT3 partition is there but when i try to mount it i get the old "mount: /dev/hdc1 already mounted or /media/storage busy" (/dev/hdc1 is the storage drive on my machine)

I have a media drive in /dev/hdd1 (also EXT3) that loads up just fine.. but not the /dev/hdc1.

this is my "mount" output:

> 
/dev/hda6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
/dev/hdd1 on /media/multimedia type ext3 (rw,nosuid,noatime,user_xattr)


this is my "mount /media/storage" output

> 
mount: /dev/hdc1 already mounted or /media/storage busy


"mount /media/multimedia" works just fine.

if i boot back to my 2.6.12 kernel the drive mounts up just fine... its is odd...

i never had this kinds of problems using straight up debian, but i guess its a kernel patch thing.

---

