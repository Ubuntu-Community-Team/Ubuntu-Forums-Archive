---
title: "Problem booting with second ide hard disk"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by girishvs on 2009-01-26
Hello,
I recently upgraded my dekstop to Ubuntu 8.0.4 LTS. I have 2 IDE hard disks - 40GB and 200GB. I am having problems getting both hard disks to mount at boot-up.

When my fstab looks like this
-----------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=7c970ac8-9434-44fd-98e4-9abb99f07c4d /               ext3    relatime,error
s=remount-ro 0       1
# /dev/sda1
UUID=fe29f63f-9da5-4674-b9ab-37735ccb64bd /boot           ext3    relatime      
  0       2
# /dev/sda2
UUID=e40f2528-d4e8-43fd-afda-4dd4d5e16a95 none            swap    sw            
  0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
-----------------------------------------
the starting up of the dekstop works fine.

But if my fstab looks like this 

-----------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=7c970ac8-9434-44fd-98e4-9abb99f07c4d /               ext3    relatime,error
s=remount-ro 0       1
# /dev/sda1
UUID=fe29f63f-9da5-4674-b9ab-37735ccb64bd /boot           ext3    relatime      
  0       2
# /dev/sda2
UUID=e40f2528-d4e8-43fd-afda-4dd4d5e16a95 none            swap    sw            
  0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

#/dev/sdb1
/dev/sdb1       /second      ext3    relatime      
  0       3
-----------------------------------------
the system does not boot-up.

The funny part is, after I boot up (with the first fstab), I can manually mount /dev/sdb1 (or by double clicking it from Places Menu) to /media/disk.

Am I missing something? Any suggestions/help is appreciated.
Also, is this the right forum?

---

### Post by opscure on 2009-01-26
forgive me if this is a little condescending, but did you create the /second directory?  What kind of errors are you seeing on the boot?  I'm assuming it's getting past your boot manager...

---

### Post by ajgreeny on 2009-01-26
You may find it easier if you use a mount point in /media, I think, as if I remember correctly, only devices mounted in /media will have a device icon on the desktop by default.  You could certainly make a launcher to it easily enough if in /second, but why bother?  Is there a reason for mounting in /second as opposed to /media/second, or something similar?

As opscure says, you must have a folder called /second for your fstab to work correctly.

---

