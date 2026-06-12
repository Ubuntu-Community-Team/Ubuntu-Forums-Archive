---
title: "Changing permissions on USB flash drive"
date: 2005-12-30
forum: Hardware &amp; Laptops
---

### Post by TheEHMan on 2005-12-30
When I insert my flash drive in the port, it appears on the desktop and allows me to view what's on it, but not to write to it.  The reason it gives is that I'm not the owner.  I know I need to change the permissions, but I'm unsure of where to start.

---

### Post by aysiu on 2005-12-30
See the fourth link in my sig.
Generally flash drives appear as /dev/sda1, but follow the directions to be sure.

---

### Post by TheEHMan on 2005-12-30
I tried the info in the link.  The drive shows up in fdisk -l as:

Disk /dev/sda: 259 MB, 259522560 bytes
65 heads, 32 sectors/track, 243 cylinders
Units = cylinders of 2080 * 512 = 1064960 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         244      253424    4  FAT16 <32M
Partition 1 has different physical/logical endings:
     phys=(249, 64, 32) logical=(243, 44, 32)

but it doesn't show up in fstab.  Here's what fstab shows:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1       /media/windows1  ntfs  nls=utf8,umask=0222 0       0
/dev/hdb5       /media/windows2  vfat    iocharset=utf8,umask=000   0       0
/dev/hdb6       /media/windows3  vfat    iocharset=utf8,umask=000   0       0
/dev/hdb7       /media/windows4  vfat    iocharset=utf8,umask=000   0       0
/dev/hdb8       /media/windows5  vfat    iocharset=utf8,umask=000   0       0
/dev/hdb9       /media/windows6  vfat    iocharset=utf8,umask=000   0       0

---

### Post by aysiu on 2005-12-30
[QUOTE=TheEHMan]
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         244      253424    4  FAT16 <32M
**Partition 1 has different physical/logical endings:**
     phys=(249, 64, 32) logical=(243, 44, 32)[/quote] This bold part may be out of my league. Is your USB drive partitioned?

---

### Post by TheEHMan on 2005-12-30
AS far as I know, it's just one partition.

---

### Post by aysiu on 2005-12-30
Well, go ahead and add it to the /etc/fstab, reboot, and see if it makes a difference...

---

### Post by TheEHMan on 2005-12-30
Exactly what would I need to type in to add it to fstab?  Sorry to be a pain, but I'm still in the learning process here.

---

### Post by jpkotta on 2005-12-30
Mine comes up with the same "Partition 1 has different physical/logical endings:"  In my case, it's on /dev/sdb1.  Here's my /etc/fstab:

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda9       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       /boot           ext3    defaults        0       2
/dev/sda4       /dos            vfat    defaults        0       0
/dev/sda1       /win_xp         ntfs    rw,user,noauto,dmask=000,fmask=000           0       0
/dev/sda6       /archive        ext3    rw,user         0       2
/dev/sda7       /home           ext3    defaults        0       2
/dev/sda8       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

# usb key drive
# permission = default & ~mask
/dev/sdb1       /media/removable  vfat    rw,user,noauto,dmask=077,fmask=177  0       0


You may want to fiddle with dmask (dirs) and fmask (files).  I don't use GNOME, so it might not work there.  I've had trouble in the past with GNOME being confused with fstab-ed keydrives.

More information about /etc/fstab can be gotten with ```
man mount
```

---

### Post by TheEHMan on 2005-12-31
JPKOTTA, I tried your suggestions but it didn't help.


Tried the directions posted here:

[http://www.ubuntuforums.org/showthread.php?p=616396#post616396]("http://www.ubuntuforums.org/showthread.php?p=616396#post616396")

and everything works fine now.  Thanks to everybody for their efforts.

---

