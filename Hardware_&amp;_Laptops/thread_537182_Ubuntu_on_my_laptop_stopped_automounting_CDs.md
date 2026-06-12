---
title: "Ubuntu on my laptop stopped automounting CDs"
date: 2007-08-28
forum: Hardware &amp; Laptops
---

### Post by tph on 2007-08-28
Hi,  it seems that ubuntu has stopped automounting my dvd-drive when I insert a cd/dvd. I remember that Ubuntu used to automount a while ago, but I don't really use CDs and/or DVDs that frequently. I haven't really figured out how to solve the problem or what exactly the problem is, but then I thought of one thing that maybe could've caused the problem.

A while ago I upgraded my Windows XP to Vista (acer laptop, got it for free, didn't see a reason not to as I don't really use Windows much etc. etc.). During the updrage I was told that it had to convert the old fat32-filesystem that used to be on my windows-partition to ntfs. Again, I didn't see a reason not to convert it. 

If the change from fat32 to ntfs really is the cause (I find it a bit strange), I would think that building a new /etc/fstab or something would work? (might be a command/program for this?)

Anyways, for those of you who like to peak into other people's fstab-files, here's mine:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=9324efbd-3f47-460d-95ad-0619c644d40f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda7
UUID=f743387a-4208-4562-9e6f-efba3a2b11d7 /home           ext3    defaults        0       2
# /dev/sda1
UUID=16D9-B5D2  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/sda2
UUID=61BA-087A  /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/sda5
UUID=de6de355-e38f-4010-a230-6d517f08b8de none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

/home           /chroot/home            none bind 0 0
/tmp            /chroot/tmp             none bind 0 0
/dev            /chroot/dev             none bind 0 0
/proc           /chroot/proc            proc defaults 0 0
/media/cdrom0   /chroot/media/cdrom0    none bind 0 0

```

---

