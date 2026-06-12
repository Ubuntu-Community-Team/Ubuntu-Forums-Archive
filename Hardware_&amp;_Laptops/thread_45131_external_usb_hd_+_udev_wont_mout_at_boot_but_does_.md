---
title: "external usb hd + udev wont mout at boot but does work"
date: 2005-06-28
forum: Hardware &amp; Laptops
---

### Post by tigerstripedcat on 2005-06-28
When I boot I get the error message:

mount: special device /dev/usbhd does not exist

(my external hard drive is assoicated with /dev/usbhd via udev)

HOWEVER, when I get into kde and type:

sudo mount -a

everything works perfectly.   It seems as if fstab is setup correctly (below), because it mounts after the fact fine.  The problem seems to be that udev, or usbfs, or hotplug (I don't know) isn't setting the device node in time for mount to mount this device.   But I could be way off base here.   I had this working in mandrake before, so it has to work somehow.

I hope someone can help me because I've spent far too much time on this problem.

THANKS!

________

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hda1 /mnt/win_c ntfs umask=0,nls=iso8859-1,ro 0 0
/dev/sdb1       /media/ipod  vfat       nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000,user,defaults,noatime,iocharset=utf8 0       0
/dev/usbhd /mnt/backuphd ext3 user,exec 0 0

---

### Post by tigerstripedcat on 2005-06-29
[QUOTE=tigerstripedcat]When I boot I get the error message:

mount: special device /dev/usbhd does not exist

(my external hard drive is assoicated with /dev/usbhd via udev)

HOWEVER, when I get into kde and type:

sudo mount -a

everything works perfectly.   It seems as if fstab is setup correctly (below), because it mounts after the fact fine.  The problem seems to be that udev, or usbfs, or hotplug (I don't know) isn't setting the device node in time for mount to mount this device.   But I could be way off base here.   I had this working in mandrake before, so it has to work somehow.

I hope someone can help me because I've spent far too much time on this problem.

THANKS!

________

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hda1 /mnt/win_c ntfs umask=0,nls=iso8859-1,ro 0 0
/dev/sdb1       /media/ipod  vfat       nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000,user,defaults,noatime,iocharset=utf8 0       0
/dev/usbhd /mnt/backuphd ext3 user,exec 0 0[/QUOTE]
 anyone?

---

### Post by tigerstripedcat on 2005-06-30
[QUOTE=tigerstripedcat]anyone?[/QUOTE]
 last time

---

### Post by Brandon Hoult on 2005-07-01
see [http://ubuntuforums.org/showthread.php?p=237561#post237561](http://ubuntuforums.org/showthread.php?p=237561#post237561)

---

