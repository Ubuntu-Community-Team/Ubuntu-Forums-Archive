---
title: "fstab, labels, and external hard drives..."
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by Izkata on 2007-10-24
Hokay, I'm currently having a bunch of problems with mounting and fstab stuff... 

The first of which is addressed in another thread, [http://ubuntuforums.org/showthread.php?t=567965](http://ubuntuforums.org/showthread.php?t=567965) - that external hard drives (and flash drives, for that matter) won't auto-mount when plugged in if they have an fstab entry.  Removing the entry works for flash drives, but not for external hard drives, although back in Edgy it worked even for my external hard drive.  "sudo mount -a" does work when an entry exists.

Next up, when a flash drive *is* auto-mounted, I can't eject it unless I'm root:
izkata@Izz:~$ eject /media/CLASSWORK/
umount: /media/CLASSWORK is not in the fstab (and you are not root)
eject: unmount of `/media/CLASSWORK' failed
izkata@Izz:~$ sudo eject /media/CLASSWORK/

Neither my external hard drive's label nor it's uuid will show up in /dev/disk/by-label/ and /dev/disk/by-uuid/, but flash drives are working fine there, too.

Here's the fstab I currently have:
```
# /etc/fstab: static file system information.
#
# <file system>                                 <mount point>   <type>  <options>                                               <dump>  <pass>
proc                                            /proc           proc    defaults                                                0       0
# /dev/sda1
UUID=F4749F4B749F100A                           /media/Windows  ntfs-3g defaults,rw,nls=utf8,umask=007,gid=46,uid=izkata,users  0       1
# /dev/sda2
UUID=cc9125d8-b6aa-47d7-a8a6-54a7c04a0016       none            swap    sw                                                      0       0
# /dev/sda3
UUID=530dd4cf-86a9-455b-be43-b1eb233dcb8e       /               ext3    defaults,errors=remount-ro                              0       1
/dev/scd0                                       /media/cdrom0           udf,iso9660 user,noauto                                 0       0
#LABEL=EXTERNAL                                 /media/External vfat    defaults,exec,uid=izkata,iocharset=utf8,users,nosuid            0       0
#LABEL=CLASSWORK                                        /media/CLASSWORK        vfat    defaults,exec,uid=izkata,iocharset=utf8,nosuid,users    0       0
```

---

### Post by Izkata on 2007-10-27
Anyone?  No help?

I've been looking around the forums and trying various things out..  The second one ('eject') was fixed somehow (not a clue), even though my fstab looks the same.  And I've been using pmount for my external drive...  (Which I notice that I failed to mention is formatted as a FAT32)

It'd still be nice if I could get everything to work, though.

---

