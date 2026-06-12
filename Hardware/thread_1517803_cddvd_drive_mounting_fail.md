---
title: "cd/dvd drive mounting fail"
date: 2010-06-25
forum: Hardware
---

### Post by gillisb91 on 2010-06-25
here is the error: 
Error mounting: mount exited with exit code 1: helper failed with:
[mntent]: line 13 in /etc/fstab is bad
mount: can't find /dev/sr0 in /etc/fstab or /etc/mtab

i open fstab and i see this:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sda1 during installation
UUID=ee38bedd-9df2-43df-89a2-137211023516 / ext4 errors=remount-ro 0 1
# swap was on /dev/sda5 during installation
UUID=9e9515a5-9f91-47ea-bb28-6b54ab70e20b none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0#usbfs for virtualbox
none /proc/bus/usb usbfs devgid=125,devmode=664 0 0

im running ubuntu 10.4 on dell latitude d610

thanks in advance

---

### Post by gillisb91 on 2010-06-26
does ANYBODY know how to fix this????

---

### Post by kaiwi on 2010-06-26
Had and am still having the same problem. See thread
[http://ubuntuforums.org/showthread.php?p=9208913](http://ubuntuforums.org/showthread.php?p=9208913)

Right now I started my PC with a CDROM inserted, and CDROM is still not mounted. 

Sorry if this doesn't help you much

---

### Post by kaiwi on 2010-06-26
see also
[http://ubuntuforums.org/showthread.php?t=1516501](http://ubuntuforums.org/showthread.php?t=1516501)

---

### Post by gillisb91 on 2010-06-27
Damn. I just reformatted my drive..... That fixed it.... But I lost all my info. 


Thnks though.

---

