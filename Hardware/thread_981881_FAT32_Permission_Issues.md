---
title: "FAT32 Permission Issues"
date: 2008-11-14
forum: Hardware
---

### Post by d-man97 on 2008-11-14
Installed a new hard drive. Secondary, storage only hard drive (/dev/sdb) with 1 partition (/dev/sdb1) formatted as FAT32.
```
$ sudo mkdir /media/Storage
```
From [https://help.ubuntu.com/community/InstallingANewHardDrive]("https://help.ubuntu.com/community/InstallingANewHardDrive"):
```
$ sudo chgrp plugdev /media/Storage
$ sudo chmod g+w /media/Storage
$ sudo chmod +t /media/Storage
```

Added the following to /etc/fstab:
```
# /dev/sdb1 - Storage
UUID=491C-F781 /media/Storage vfat defaults 0 0
```

```
$ sudo mount -a
```

As soon as the HD is mounted, the directory permissions are over-written by mount to whatever /etc/fstab defaults are. So, I tried to change them again, this time with the drive mounted:

```
$ sudo chmod 777 -R /media/Storage
```
(I'm pessimistic and I figured it wouldn't work; so, I used 777.)

No errors, so you would think it worked, but:
```
$ ls -l /media | grep Storage
drwxr-xr-x  2 root root 16384 1969-12-31 19:00 Storage
```

Two problems with that: 1) Permissions did not change and 2) the date/time is all out of whack.

To fix the date/time:
```
$ sudo touch /media/Storage/test
$ ls -l /media/Storage
-rwxr-xr-x 1 root root 0 2008-11-14 04:03 test
$ sudo rm /media/Storage/test
$ ls -l /media | grep Storage
drwxr-xr-x  2 root root 16384 2008-11-14 04:04 Storage
```

The permissions still are not 777, they are stuck on 755, but I do not know the behavior of touch, so this may be normal. But the date/time is fixed. (That is, until the drive is remounted, then the date comes back. Apparently empty drives were last changed 40 years ago, even though I just deleted a file...figure that one out.)

```
$ sudo umount /dev/sdb1
$ ls -l /media | grep Storage
drwxrwxr-t  2 root plugdev 4096 2008-11-13 23:00 Storage
```

Hey, look! My permissions are back! LOL! So, after I kept my head from exploding, I found and read [https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab").

It implies to me that fat16/fat32 file systems' permissions can ONLY be set during mount (via fstab, for auto mounting).

Using the 'defaults' option makes it so that nouser is set, thus only root can mount it and therefore owns it all. Besides that basic fact, if user is set, and auto is set (as it is by default), user doesn't matter because fstab is processed as root. See where this is going? Root again owns the entire drive!!!

This leaves user and noauto options to make the drive mine. However, those two options prevent it from being mounted during boot! Not what I want. Let's continue anyways...Say I have both those options. I mount it myself (or let gnome do it by clicking on it in Places). I put a file on there, it's mine. I log off, and another users comes on and mounts the drive too. Oh wow, now my file is their file!

What kind of security is this? Why can't it be like ~/ (home), where everyone can see it, if you create something it's yours, and you can prevent others from seeing it or let them write to it if you want?

I want multiple users to own and control directories on it, while root owns the base directory (/media/Storage) and everyone has access to it, then I will setup the further structure.

**So, my basic question is this:**
How do I translate the following into my fstab so /media/Storage will work as I expect it to, as in:
```
$ sudo chgrp plugdev /media/Storage
$ sudo chmod g+w /media/Storage
$ sudo chmod +t /media/Storage
Owner: root; Group: plugdev; Group write; +t: so users' creations are their own.
```

Is that too much to ask? To let multiple users own directories/files at the same time? Is it a deficit of FAT32, or am I just missing something? If FAT32 just can't do it, I guess I will have to switch it to NTFS and deal with the errors. I just got my HD back from Seagate warranty because the drive failed after a hard-restart: hard-restart, boot linux & noticed problems, ran Vista ntfs fschecker and in combination with the on-drive features they filled up the drive's spare recovery sectors and left over 17 still bad with no way to fix them, not even using Seagate's floppy! So, I'd like to stay away from NTFS (although it did support usr/group security). Any other file systems to choose from?


In the meantime I changed /etc/fstab:
```
$ cat /etc/fstab | grep Storage
# /dev/sdb1 - Storage
UUID=491C-F781 /media/Storage vfat defaults,noexec,uid=1000,gid=1000,dmask=027,fmask=137 0 0
```
Re-made /media/Storage to reset its permissions, and now:
```
$ sudo mount -a
$ ls -l /media | grep Storage
drwxr-x---  2 derek derek 16384 1969-12-31 19:00 Storage
```
Which, is good enough for now, except for the date/time issue, LOL.

P.S. - Why can't sudo cd? It is a pain to use 'sudo ls ./Storage/a/b/c' LOL! I know, I know, 'sudo su' works just fine. :)

---

