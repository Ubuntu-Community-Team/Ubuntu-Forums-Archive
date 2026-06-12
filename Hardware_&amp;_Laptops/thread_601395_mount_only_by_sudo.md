---
title: "mount only by sudo"
date: 2007-11-03
forum: Hardware &amp; Laptops
---

### Post by DJTurboToJo on 2007-11-03
Hi Community,

I have several partitions and I want that some (let's just say my Windows partition) can only be mounted as root. Actually I want to set some permissions that only some user might mount some drives.
Additionally, is there any way I can even hide the hardware information from the device manager. So that only me and root could see all drives but another user cant see these drives at all and dont try mounting them???

Normally when I log in all my drives are mounted. I uncommented the lines in /etc/fstab so that only one drive is mounted (fstab see below). The problem with that solution is that after clicking on My Computer all drives are visible but not mounted and they can be mounted without password. 

So I want that some drives are not visible in My Computer (if possible hiding in the hardware information). However I should still be able to mount them, but only password protected. Well, I guess this hiding stuff might be a bit hard....so lets say I just want to have some access control for some drives.
------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=8b58d29c-2163-46e3-89fa-4ec705ebad8a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=9af071df-815e-4da7-9533-203a88bfacbb /home           ext3    defaults        0       2
# /dev/hda1
###UUID=125861DC5861BF5B /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
###UUID=FA8CEAAE8CEA651B /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=2C0A91273D5FF43D /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
###UUID=46FB-AFD0  /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=d9b30172-b1ce-4e62-b371-0dc539caed2f none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
------

Thanks
TurboToJo

---

### Post by kidders on 2007-11-04
Hi there,

You're approaching your problem from the wrong angle, I think. Linux already has perfectly adequate mechanisms for controlling access to files ... I would suggest using them.

Your hard disk is already full of things you won't want people messing with ... /etc/hosts for example. Users can see that it's there, but they can't alter it. Similarly (assuming your computer is properly configured), nobody but you should have any access *at all* to the files stored on your desktop. Imagine, for the sake of argument, that your /home/DJTurboToJo was kept on a disk partition by itself. One *might* think, since nobody but you would ever have any reason to access it, that the filesystem should only be mounted when you're logged in ... but in reality, it should be kept mounted all the time.

You can password-protect filesystems if you really want to (by encrypting them), but the majority of users find that unnecessary. In any case, it's no substitute for setting proper permissions on private files.

---

