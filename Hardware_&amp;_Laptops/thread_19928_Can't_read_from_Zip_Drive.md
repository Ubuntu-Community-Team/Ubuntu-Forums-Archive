---
title: "Can't read from Zip Drive"
date: 2005-03-14
forum: Hardware &amp; Laptops
---

### Post by whell on 2005-03-14
[http://www.ubuntuforums.org/showthread.php?p=93956#post93956](http://www.ubuntuforums.org/showthread.php?p=93956#post93956)

Sorry for the cross post, but this is more of a hardware issue anyway.  I've followed the instrucitons in the attached link.  I now have a Zip Drive icon in my "Computer" folder, and the zip drive does spin up during boot.  However, I get an error message that implies that Linux can't determine the type of file system on the drive (its plain old FAT).   This is an ATAPI Zip 100 drive, and has been detected, and used, successfully using other flavors of Linux. 

Can anyone provide any assistance?  Thanks!

---

### Post by mac57 on 2005-03-14
Internal ATAPI Zip disks do seem a bother to get working, don't they? I got mine working on the Ubuntu 5.04 Live CD the following way - seems to work for most distros. 

ATAPI Zip disks are supported by kernel module ide-floppy. If you do an lsmod, you will likely find that it is already loaded. The problem is, for some unknown reason, you can only actually work successfully with the drive if you load this module while a zip disk is in the drive. So, to get access to your disk, simply su to root, rmmod ide-floppy, put a zip disk in the drive, and modprobe ide-floppy. You will hear the disk spin.

Then, proceed as normal. In my case, my zip disk shows up as /dev/hdb. To gain access after doing the rmmod/modprobe, simply enter the following as root (this assumes you have created a /mnt/zip directory as you mount point):

mount -t vfat /dev/hdb4 /mnt/zip -o users,gid=users,umask=0002,rw

The "-o" stuff just sets up the vfat volume so that you have write access.

Good luck.

---

