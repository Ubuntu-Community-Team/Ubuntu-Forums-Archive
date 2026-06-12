---
title: "Can't use second internal hard drive"
date: 2008-08-06
forum: General Help
---

### Post by who_cares on 2008-08-06
I have a second hard drive in my computer that I'd like to have mounted to /media/Storage, and I know it's at /dev/sdb1.
The problem is I had to replace the drive and reformat it to get it working again. Now I can't get it to mount on startup and when I do get it to mount I can't get write access. Does anyone know what I need to do to make it work again?

---

### Post by mc4man on 2008-08-07
well I don't mount my extra partitions at boot with fstab but I'd think the new drive has a different UUID.
 maybe run sudo blkid, get the new uuid and replace in fstab and reboot

if you didn't care about mounting at boot, delete the fstab entry and see here to get permissions
[http://ubuntuforums.org/showthread.php?p=5535259#post5535259](http://ubuntuforums.org/showthread.php?p=5535259#post5535259)

---

### Post by jualin on 2008-08-07
Check out this [thread]("http://ubuntuforums.org/showthread.php?t=880457"). They were having a similar issue and you can try the suggestions

---

### Post by who_cares on 2008-08-08
Okay, I can get the drive to mount now, but I can't write to the disk. I read the thread jualin linked to but I have write access to every other external disk, it's just this one disk I can't use.

---

