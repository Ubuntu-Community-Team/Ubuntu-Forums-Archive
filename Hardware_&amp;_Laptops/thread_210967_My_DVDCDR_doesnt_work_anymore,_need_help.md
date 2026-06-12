---
title: "My DVD/CDR doesnt work anymore, need help"
date: 2006-07-07
forum: Hardware &amp; Laptops
---

### Post by Bossieman on 2006-07-07
Today I was going to burn a CD but nothing worked. I started by putting in a CD-R disc and the drive started to sound "funny". Then I tried to put a ordinary music CD in but nothing happened at all.
Usally a icon appears on the desktop but now nothing happens.
Any ideas to solve this?

---

### Post by Bossieman on 2006-07-07
This is my /etc/tab file
> 
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-25-386/volatile tmpfs rw 0 0
capifs /dev/capi capifs rw,mode=0666 0 0


And this is my /etc/fstab file

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


Maybe this helps you to help me?

---

### Post by Bossieman on 2006-07-07
Okey, I installed Totem again and evrything worked now. Strange.

---

