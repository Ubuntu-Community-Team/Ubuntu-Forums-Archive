---
title: "Drive not mounting correctly."
date: 2005-11-29
forum: General Help
---

### Post by Jibboom on 2005-11-29
Ok, firstly, my hard drives are set up like this:
120Gb IDE > Ubuntu Breezy installed
200Gb SATA > Windows XP installed
200Gb SATA > No OS installed, formatted under windows

I can access all my files on the XP drive, but the other SATA drive which has no OS is not being mounted correctly on startup (I get the red "failed" instead of ok).

This is the contents of my fstab file:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1       /media/windows ntfs    nls=utf8,umask=0222 0       0
/dev/sdb1       /media/storage ntfs    nls=utf8,umask=0222 0       0

```

The one not working is "/dev/sdb1       /media/storage ntfs    nls=utf8,umask=0222 0       0"

When using the disk manager (System>Administration>Disks) the drive is shown, but under the Partitions tab it's status is "inaccessible".

Any thoughts how to solve this?

---

### Post by sapo on 2005-11-29
The mount point /media/storage exists? didnt you forget to create the dir?

O_o

---

### Post by Jibboom on 2005-11-29
[QUOTE=sapo]The mount point /media/storage exists? didnt you forget to create the dir?

O_o[/QUOTE]

Yes... yes I did. ](*,) Heh. Why did I remember that for the windows drive but not this one? ...eh.

Never mind then.

---

### Post by sapo on 2005-11-29
everybody do this once in live :)

---

