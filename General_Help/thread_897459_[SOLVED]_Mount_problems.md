---
title: "[SOLVED] Mount problems"
date: 2008-08-22
forum: General Help
---

### Post by Tony_photoplus on 2008-08-22
I was trying to ensure that all updates were enabled.  I have to Software sources and ticked all the boxes - it seemed to ask for the disk so I put the disk into the comp it did its loading and I find that its mounted the disk to the desktop and I can´t un-mount it and eject it.  Yep stupid - not knowing what I am doing -yep learnt not to fiddle in that area again.  But now how do I undo what I have done?  It says I dont have permission to unmount.

The icon is on the desktop and states: You are not privileged to unmount the volume 'Ubuntu 8.04.1 i386'. 

Thanks

Tony

---

### Post by WRDN on 2008-08-22
Look in the /media folder for the mount point (it will likely be cdromN, where N represents a number). Now, in the Terminal, type:

```
sudo umount /media/cdromN
```

---

### Post by livestockPimp on 2008-08-22
you can check what mounted partitions you have by typing "df" at the command prompt.

from here you can use "umount" to unmount these. just type umount followed by the mount point, ie;

"umount /dev/sdb2"

You have to be root to do this or use "sudo".

---

### Post by Tony_photoplus on 2008-08-22
Not working, it couldn´t find
umount: /media/cdromN: not found
When I went to the files to unmount it  stated.

unmount - only root can unmount /dev/scdo/media/cdrom0

Thats it.

---

### Post by WRDN on 2008-08-22
> **Tony_photoplus said:**
> Not working, it couldn´t find
umount: /media/cdromN: not found
When I went to the files to unmount it  stated.

unmount - only root can unmount /dev/scdo/media/cdrom0

Thats it.

Did you literally type "cdromN"? I only added the letter N as it could be multiple numbers. It appears it is mounted in cdrom0, so type:

```
sudo umount /media/cdrom0
```

---

### Post by Tony_photoplus on 2008-08-22
> **livestockPimp said:**
> you can check what mounted partitions you have by typing "df" at the command prompt.

from here you can use "umount" to unmount these. just type umount followed by the mount point, ie;

"umount /dev/sdb2"

You have to be root to do this or use "sudo".

The terminal gave me this:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             37136072   2678972  32585532   8% /
varrun                  615156       120    615036   1% /var/run
varlock                 615156         0    615156   0% /var/lock
udev                    615156        48    615108   1% /dev
devshm                  615156        12    615144   1% /dev/shm
lrm                     615156     39760    575396   7% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon      37136072   2678972  32585532   8% /home/photoclub/.gvfs
/dev/scd0               711154    711154         0 100% /media/cdrom0

So would it be /dev/scd0?

Tony

---

### Post by Tony_photoplus on 2008-08-22
> **WRDN said:**
> Did you literally type "cdromN"? I only added the letter N as it could be multiple numbers. It appears it is mounted in cdrom0, so type:

```
sudo umount /media/cdrom0
```


Worked a dream thanks

Tony

---

### Post by WRDN on 2008-08-22
"/dev/scd0" is the device itself, while "/media/cdrom0" is the mount point. When unmounting mediums, you only need to enter the mount point (sudo umount /media/cdrom0).

---

### Post by prshah on 2008-08-22
> **WRDN said:**
> "/dev/scd0" is the device itself, while "/media/cdrom0" is the mount point. When unmounting mediums, you only need to enter the mount point (sudo umount /media/cdrom0).

Any of these three commands will work```
sudo umount /dev/cdrom0
sudo umount /dev/scd0
sudo umount /media/cdrom0
```

It doesn't matter whether you use the mount point, device name or device alias; they all work the same.

btw, sudo mounting is now on it's way out; the correct way is to use pmount. you will need to install pmount first:```
sudo apt-get install pmount
``` then a simple```
#to mount, note no sudo, pathname, /dev/, etc
pmount cdrom0
#to unmount, note no sudo
pumount cdrom0
``` This has the additional advantages of "fixing" umask and permissions, so that you do not need to be root and/or fiddle with fstab settings and/or mount options for umask, so that an ordinary (non-root, non-sudo) user can access it.

Note that the user has to be a member of the plugdev group (already done by default on hardy).

This also works for USB pendrives```
sudo pmount sdd1
``` 

In fact, this is how hardy handles all removable device mounting.

---

