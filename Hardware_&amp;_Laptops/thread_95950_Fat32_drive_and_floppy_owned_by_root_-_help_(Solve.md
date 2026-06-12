---
title: "Fat32 drive and floppy owned by root - help (Solved)"
date: 2005-11-27
forum: Hardware &amp; Laptops
---

### Post by Nunsta on 2005-11-27
Hello All,
A Linux noob here,

I installed ubuntu a few days ago and everything seems to be working fine.  The install was smooth as glass, all my hardware was detected and is operating correctly other than the following problems:

I have a fat32 partion I am going to share with my wife's Windows computer.  Ubuntu found the partion I named "share" and presents an icon on the desktop for it.  Except it says it is owned by root so I can't write to it.

Second, related problem:
I mounted my floppy with the following command:
```
sudo mount -t vfat /dev/fd0 /media/floppy
```
Again, I have access to my floppy disk, but it is also owned by root so I can't write to it either.

I created a root password and logged into gdm as root.   When I right click > Properties > Permissions I still can't enable "write" capability to anyone but the owner.  It also says I cannot change the ownership because I do not have permission--even while I'm logged in as root.  I tick the check boxes and they automatically untick.

Since I don't care if everyone has full access to my floppy drive, I tried the following commands, both as su and when actually logged in as root:
```
chmod a=rwx /media/floppy0
```
```
chmod a=rwx /dev/fd0
```
Neither had any effect.

1. I cannot write to the floppy unless I am logged in as root.
2. I cannot change the permissions from the cli even when I am logged in as root, unless I am typing the wrong command to change permissions.
3. I cannot change the permission using the graphical icon thingy even when I am logged in as root.

I think whatever will work for the floppy will work for the fat32 partition.

Thanks in advance for any help

---

### Post by aysiu on 2005-11-27
That's not a *chmod* issue. It's a mounting issue.
Follow these directions:
[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

It assumes your FAT partition is /dev/hda1
To find out what it really is, type ```
sudo fdisk -l
``` in a terminal

---

### Post by sjh on 2005-11-27
[QUOTE=Nunsta]

Second, related problem:
I mounted my floppy with the following command:
```
sudo mount -t vfat /dev/fd0 /media/floppy
```
Again, I have access to my floppy disk, but it is also owned by root so I can't write to it either.

[/QUOTE]

If I use that code to mount my floppy, it mounts as owned by root.

If I just use ```
mount /media/floppy0
```

it mounts as owned by my user.

Hope that helps,
SJH

---

### Post by Nunsta on 2005-11-27
I don't know how to delete posts on this forum.  Sorry.

---

### Post by Nunsta on 2005-11-27
Thanks to both of you.  The fast replies of this forum are truly appreciated.

Thanks aysiu for the link to the guide, which solved my windows partion problem.
And thanks sjh which solved my floppy issue.

---

### Post by alex_l on 2005-11-30
Thanks aysiu for the link to the guide, which solved  windows partion problem again. This lik helped me too.

---

### Post by yuri6312 on 2005-11-30
ye 
just i have the same problem..
but use this idea i can't slove it ...
please anyong can help me?

---

