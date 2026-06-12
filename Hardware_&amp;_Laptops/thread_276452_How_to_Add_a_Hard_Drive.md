---
title: "How to Add a Hard Drive"
date: 2006-10-12
forum: Hardware &amp; Laptops
---

### Post by Gomez_Adams on 2006-10-12
I tried to install a second hard drive, but could not make it visible in Nautilis. fdisk, mount, GPARTED and Disk Manager showed it was there, but I could not access it. I tried it with two different drives, known to be good. In Disk Manager, when I tried to browse contents of the disk, I got shot back to the folder the drive was mounted to rather than to the drive itself. 

Here is what I did:

Partitioned and Formated to ext3 using GPARTED.

Created new folder in /mnt and made the folder read and write using chown and chmod per [http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html).

Edited /etc/fstab to point to the mount point.

Ran sudo mount -a to mount the drive.

The disk showed up in Nautilis when I first installed and formated it, but disapeared when I rebooted.  Following are contents of the first attempt at fstab. /mnt/40G is the added directory.

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 none swap sw 0 0
/dev/hdb1 /mnt/40G ext3 defaults 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

What finally corrected the problem was changing the mount point to /media/40g.  Contrary to what is posted on several websites, the correct mount folder for permanent drives is /media.  Per "Begining Ubuntu Linux", /mnt is only for temporary drive access.

---

