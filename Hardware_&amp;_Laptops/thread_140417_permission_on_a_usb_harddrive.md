---
title: "permission on a usb harddrive"
date: 2006-03-06
forum: Hardware &amp; Laptops
---

### Post by tioneb on 2006-03-06
Hi,

I can't get the permissions that I want (user can create a file on the harddrive) with my EXTERNE drive (USB)

**fstab**
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       		<dump>  <pass>
proc            /proc           proc    defaults        		0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 	0       1
/dev/hda7       /home           ext3    defaults        		0       2
/dev/hda1       /media/hda1     ntfs    defaults        		0       0
/dev/sda1	/media/EXTERNE  vfat    defaults,umask=0   		0       0
/dev/hda5       /usr            ext3    defaults        		0       2
/dev/hda8       /var            ext3    defaults        		0       2
/dev/hda6       none            swap    sw              		0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     		0       0
**mtab**
> /dev/hda2 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
usbfs /proc/bus/usb usbfs rw 0 0
tmpfs /lib/modules/2.6.12-10-k7/volatile tmpfs rw,mode=0755 0 0
/dev/hda7 /home ext3 rw 0 0
/dev/hda1 /media/hda1 ntfs rw 0 0
/dev/hda5 /usr ext3 rw 0 0
/dev/hda8 /var ext3 rw 0 0
tmpfs /dev tmpfs rw,size=10M,mode=0755 0 0
/dev/sda1 /media/EXTERNE vfat rw,umask=0 0 0

and the rights are 777 on /dev/sda1 et /media/EXTERNE 
some hints please

---

### Post by tioneb on 2006-03-08
I don't know how... :( but it works know after rebooting...
but when I changed fstab I took care of 
```
umount 'thedisk'
mount -a 
```

but it didn't seem to be enough for my drive ;)

... it works great now :rolleyes:

---

