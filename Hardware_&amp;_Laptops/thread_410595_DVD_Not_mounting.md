---
title: "DVD Not mounting"
date: 2007-04-15
forum: Hardware &amp; Laptops
---

### Post by winkerbean on 2007-04-15
I tried to mount my DVD drive and got the following messages:
Could not mount device.
The reported error was:
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

My /etc/fstab looks like so:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1    /media/hda1    ntfs-fuse    auto,gid=1002,umask=0002    0    0
/dev/hdb5       /nuetralzone    vfat    defaults        0       0
/dev/hdb6       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660    rw,user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1       /media/usb0     auto    rw,user,noauto  0       0

Any ideas?  Thanks in advance.

---

