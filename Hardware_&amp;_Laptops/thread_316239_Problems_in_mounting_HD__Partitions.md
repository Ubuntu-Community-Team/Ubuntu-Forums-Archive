---
title: "Problems in mounting HD / Partitions"
date: 2006-12-10
forum: Hardware &amp; Laptops
---

### Post by trank on 2006-12-10
UBUNTU 6.10

I have some trouble mounting hard disks partitions:

These are the NTFS devices:

[I]/dev/hda1 * 1 1275 10241406 7 HPFS/NTFS
/dev/hdc5 893 8541 61440561 7 HPFS/NTFS
/dev/hdc6 8542 16190 61440561 7 HPFS/NTFS
/dev/hdc7 16191 20397 33792696 7 HPFS/NTFS
/dev/hdc8 20398 24792 35302806 7 HPFS/NTFS
[/I]
and this is fstab:

[I]# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hda3
UUID=b2ecf901-2e3e-4b95-809e-9f25c456e689 / ext3 defaults,errors=remount-ro 0 1
#
#/dev/hda6
UUID=b0149bdf-403c-4c06-af1a-82f0697d9abc none swap sw 0 0
/dev/hdb /media/cdrom0 udf,iso9660 user,auto 0 0
/dev/ /media/floppy0 auto rw,user,noauto 0 0

/dev/hda1 /media/windows ntfs-3g defaults,locale=it_IT.utf8 0 0
# /dev/hda5 /media/windows vfat defaults,locale=it_IT.utf8 0 0
#
# /dev/hdc1 /media/windows vfat defaults,locale=it_IT.utf8 0 0
/dev/hdc5 /media/windows ntfs-3g defaults,locale=it_IT.utf8 0 0
/dev/hdc6 /media/windows ntfs-3g defaults,locale=it_IT.utf8 0 0
/dev/hdc7 /media/windows ntfs-3g defaults,locale=it_IT.utf8 0 0
/dev/hdc8 /media/windows ntfs-3g defaults,locale=it_IT.utf8 0 0

# /dev/hda1 /media/windows vfat defaults,locale=it_IT.utf8 0 0[/I]

I followed the instructions in: [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)
HOWTO: NTFS with read/write support using ntfs-3g (easy method)

but the only result is to mount automatically only the first partition of the first HD: /dev/hda1.

Anyone can halp me?
Thank You

---

### Post by bscbrit on 2006-12-10
You can't mount them all to the same point.  You need to rename your mount points /media/windows1, /media/windows2, /media/windows3 etc

---

### Post by trank on 2006-12-10
Great, now I see all NTFS partitions!
Thanks so much

---

### Post by bscbrit on 2006-12-10
You're welcome, see you around the forum. :-D

---

