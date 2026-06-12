---
title: "Unable to mount and followed FAQ"
date: 2005-04-27
forum: Hardware &amp; Laptops
---

### Post by swalsh on 2005-04-27
Here is the info.  Whenever I look in the media folder I see my Windows drive.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Here is the error message I get:
stephen@swalsh:~$ sudo mount /dev/hda1 /media/windows -t ntfs -o unmask=0222
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

What does that mean?

---

### Post by jodef on 2005-04-27
> stephen@swalsh:~$ sudo mount /dev/hda1 /media/windows -t ntfs -o **unmask=0222** should read **umask=0222**

---

### Post by swalsh on 2005-04-27
Thank you, sir.  That did the trick.

---

