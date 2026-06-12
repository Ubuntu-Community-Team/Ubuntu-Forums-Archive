---
title: "unmount Lacie external dirve"
date: 2005-07-08
forum: Hardware &amp; Laptops
---

### Post by Jason-X on 2005-07-08
Hi all,

I have an external Lacie 200G hardrive (firewire) which auto mounts when I boot up. This is all great and it has been formatted to ext3 and holds all my backup files.

The only problem is when I unmount the drive it does not seem to wind down like it did with Mac OS X. The icon disappears from the desktop like it should.

Is it safe to switch the drive off because I am concerned it will damage the drive if not unmounted properly?

Here is my fstab file:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda4       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/sda        /mnt/ipod       auto    noauto,user,rw 0 0
/dev/sda1      /media/ieee1394disk ext3 noauto,user,rw 0 0

The bottom line is my external dirve.
Am I doing something wrong here?

Thanks
Jason :)

---

