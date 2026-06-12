---
title: "umount USB stick by UUID"
date: 2006-09-12
forum: Hardware &amp; Laptops
---

### Post by drm on 2006-09-12
[FONT="Arial"]Hi all,

I'm trying to use UUID in my fstab so I can mount external storage devices by unique id's. I'm having a strange problem with my USB memory stick. I can mount it fine. but when i try to unmount it, umount gives [/FONT]

[FONT="Courier New"]umount: /media/usb_mem mount disagrees with the fstab[/FONT]

[FONT="Arial"]Why is mount happy with the UUID in fstab but umount isn't?

By the way, if I umount the device as root, umount works fine.

Mario[/FONT]

---

### Post by sciurus on 2006-11-26
I'd love an answer to this if anyone has one.

# /dev/hda6
UUID=4386-3B67  /media/backup   vfat    defaults,noauto,utf8,umask=007,gid=46,user,noauto 0       1

mount /media/backup
umount /media/backup
umount: /media/backup mount disagrees with the fstab
sudo umount /media/backup

[https://launchpad.net/distros/ubuntu/+source/util-linux/+bug/71609](https://launchpad.net/distros/ubuntu/+source/util-linux/+bug/71609)

---

### Post by Stoff on 2007-05-18
I also have this problem.

But when I try to use the fix, I cannot execute
patch -Np1 -i ../util-linux_user_mount.patch
----------
patch: **** Can't open patch file ../util-linux_user_mount.patch : No such file or directory

Maybe I misunderstand how to execute the command properly.

All other commands work fine. Unfortunately, in end end the problem still exists.

Any help and suggestions are much appreciated.

Christoph

---

### Post by abrichr on 2007-09-16
Same problem as above.  Following the instructions at [https://bugs.launchpad.net/ubuntu/+bug/94848](https://bugs.launchpad.net/ubuntu/+bug/94848), but the file doesn't exist.  Anyone?

---

### Post by abrichr on 2007-09-16
...never mind, the poster included the patch at the beginning of his post.

[http://launchpadlibrarian.net/7435949/util-linux_user_mount.patch](http://launchpadlibrarian.net/7435949/util-linux_user_mount.patch)

---

