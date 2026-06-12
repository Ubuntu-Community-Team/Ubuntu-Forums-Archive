---
title: "[SOLVED] How do I mount an ntfs partition from a different hard drive at boot?"
date: 2008-06-26
forum: Hardware
---

### Post by SpiffyBalak on 2008-06-26
The partition I want to mount is /dev/sda1, and I mount it at /media/windows.

My friend suggested adding "/dev/sda1 /media/windows ntfs-3g defaults,umask=0 0 0" to my fstab, but I know that my other NTFS partition (which is on the same drive as Xubuntu) is automatically mounted, and in my fstab, is listed with "ntfs".

Here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=100e3d89-5a29-4244-ba77-7ff7bdfe581c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb4
UUID=374133a8-0ff1-4f69-a334-23a16112c633 /home           ext3    defaults        0       2
# /dev/sdb2
UUID=F8D03A9AD03A5ED6 /media/sdb2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb3
UUID=b9b58330-95c9-400a-a53c-38cec117b579 none            swap    sw              0       0
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
# 1001 is the VBox group
none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0

---

### Post by bpl07 on 2008-06-26
Download and run ntfs-config

---

### Post by SpiffyBalak on 2008-06-26
Thank you! It seems to have worked.:guitar:

---

