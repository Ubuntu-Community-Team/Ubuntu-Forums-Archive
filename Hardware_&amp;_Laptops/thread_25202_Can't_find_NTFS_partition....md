---
title: "Can't find NTFS partition..."
date: 2005-04-09
forum: Hardware &amp; Laptops
---

### Post by JoernErik on 2005-04-09
Hi there... 

I just installed Kubuntu 5.04 as my secondary OS on my Seagate SATA Barracuda disk which also has WinXP on it on an other partition. When I open  "media:/" and then try to access my NTFS partition, named "115G Media", i get this error message: "mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab"

here's how these files look like:
--------- fstab -------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdb        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
-------------------------------------------------------

------------mtab -----------------------------------
/dev/sda2 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
/dev /.dev unknown rw,bind 0 0
none /dev tmpfs rw,size=5M,mode=0755 0 0
usbfs /proc/bus/usb usbfs rw 0 0
-------------------------------------------------------

if it helps, my chipset is NForce 3 (250GB) <-- somthing like that
and the mainbord is Epox 8KDAJ3 <-- somthing like that too  :?

---

### Post by arDAWG on 2005-04-09
You'll find your answer here:
[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)
 :wink:

---

