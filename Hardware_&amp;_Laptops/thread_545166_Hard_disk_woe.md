---
title: "Hard disk woe"
date: 2007-09-07
forum: Hardware &amp; Laptops
---

### Post by Shootmeagain57 on 2007-09-07
Ive been a very silly boy, im nit sure how ive done it but i have lost access to one of my hard disks that i was using for  music, films  and photo.   This disk was shared access with my windows xp install.  Both my feisty  and XP install were on one hard disk(150GB) and my music on another(400GB).
It went missing after i was trying to reinstall grub  to my feisty install after a brief experiment with Feisty server on a third hard disk. 
The 400GB disk is no longer readable on either my  XP or Feisty  installs and both say that it needs to be formatted. Which I would do if I had a back up of all my music and photo. But I do not (big mistake) . 
I think that I installed grub to my 400gb NTFS  disk  and that has made it unreadable.

I need to get the data off the disk .

Can anyone help?

PS im a newbie,  please treat me like the idiot that I am

---

### Post by biophysics on 2007-09-07
Installing grub has nothing to do with file system. It might be that the partition is corrupted because of a unclean mount. 
First identify the partition ID of fat32 file system and then try:
[https://www.redhat.com/archives/fedora-list/2004-April/msg00865.html](https://www.redhat.com/archives/fedora-list/2004-April/msg00865.html)

---

### Post by Shootmeagain57 on 2007-09-07
I tried the link and got this from terminal:

$ sudo fsck.msdos -r -v -V /dev/sdb1
Password:
dosfsck 2.11 (12 Mar 2005)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Currently, only 1 or 2 FATs are supported, not 0

Im none the wiser.

any idea what to do next?

---

### Post by Shootmeagain57 on 2007-09-07
If this can help anyone help me when I do:

$ gksudo gedit /etc/fstab

I get this:

proc /proc proc defaults 0 0
# Entry for /dev/sda6 :
UUID=247e8b88-de03-42d9-a27e-33a168571c9a / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=1284F44984F430B9 /media/hda1 ntfs-3g defaults,locale=en_GB.UTF-8 0 1
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=f14ee649-fb0f-44f3-9b27-d9bc942009f2 /media/hda2 ext3 defaults 0 2
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=f7cc21cd-320c-4dbe-8390-6dec47cf72c7 /media/hda3 ext3 defaults 0 2
# Entry for /dev/sda1 :
UUID=224C005B4C002C5B /media/sda1 ntfs-3g defaults,locale=en_GB.UTF-8 0 1
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=F85C83585C831094 /media/sdb1 ntfs-3g defaults,locale=en_GB.UTF-8 0 1
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=89093943-0c8f-48d8-be86-6e66e7186a6f none swap sw 0 0
# Entry for /dev/sda5 :
UUID=8dbced14-94c1-49d1-b2f9-5c29397e51b9 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/sda1 /media/ntfs 0 0 0 0
/dev/sdb1 /media/media ntfs-3g defaults,locale=en_GB.UTF-8 0 0

---

