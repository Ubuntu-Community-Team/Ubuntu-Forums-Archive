---
title: "Help: Change partition owneship form root to user"
date: 2005-11-12
forum: Hardware &amp; Laptops
---

### Post by waverave on 2005-11-12
I've inastalled breezy over houray and manegment of patitions is different. I have 4 partitions on one hard drive, beside ext3 and swap, ntfs with xp and fat32 for "documents".

My problem is I can not get ownership of the fat32, thus have no permissions. I tryed to get ownership (chown), but without success! I even tryed by acctivating an root account, yet couldn't get any result.

Please, if any one has an idea how to solve this problem, I'd approshiate the help!!!

Best regards

---

### Post by aysiu on 2005-11-12
[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

---

### Post by waverave on 2005-11-12
This is my /etc/fstab

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda4       /media/dokumenti vfat    user,rw,auto,umask=0000,iocharset=utf8           0       0
/dev/sda1       /media/xp       ntfs    defaults        0       0
/dev/sda3       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

...but don't think it's the problem, on hoeray it worked. However, here...is there a file i could edit to correct the owner form root to user? What if I install breezy once more (e.g. expart), how should I set partitions?

---

### Post by waverave on 2005-11-12
I found a temporary solution, changing the mode of the patition to rwx for user and groups.

I did this as root, and used my acount's UID.

```
$ chmod 1000 /dev/sda4 -R -v
```

However, this doasn't solve the problem! Still, I can not save files directly (e.g. form Azureus), but have to copy-paste them, and prabably I will discover other restrictions. Thus, some debugging on the brand new feature of Administation --> Disks has to be done, since command

```
$ chown username:username -R -v /dev/sda4
```

executes, but has no effect.

If You have any other suggestions, please post them!

---

### Post by aysiu on 2005-11-12
[QUOTE=waverave]
...but don't think it's the problem, on hoeray it worked. However, here...is there a file i could edit to correct the owner form root to user? What if I install breezy once more (e.g. expart), how should I set partitions?[/QUOTE] Actually, I think it is a problem. ```
/dev/sda4 /media/dokumenti vfat user,rw,auto,umask=0000,iocharset=utf8 0 0
``` Try using the actual parameters given in the link I put earlier. Your line should read ```
/dev/sda4 /media/dokumenti vfat    iocharset=utf8,umask=000   0       0
``` Try that out--it should work. Theoretically, you can just ```
sudo mount -a
``` to get it to work, but I've found reboots to be more reliable.

---

### Post by metoo on 2005-11-13
Funny, some use user, some use users.
There are other threads which mention to delete the utf=8 entry too.

a line that works for me here is:
/dev/sda3 /w ntfs noauto,ro,users,noexec,umask=000 0 0

You can try in /etc/fstab for /dev/sda4:
/dev/sda4 /media/dokumenti vfat auto,rw,users,noexec,umask=000 0 0

---

### Post by Saarg on 2005-11-13
[QUOTE=metoo]Funny, some use user, some use users.[/QUOTE]

Actually it's almost the same. Here is what the man page for mount says:

**user **
Allow an ordinary user to mount the file system. The name of the mounting user is written to mtab so that he can unmount the file system again. This option implies the options noexec, nosuid, and nodev (unless overridden by subsequent options, as in the option line user,exec,dev,suid). 

**users** 
Allow every user to mount and unmount the file system. This option implies the options noexec, nosuid, and nodev (unless overridden by subsequent options, as in the option line users,exec,dev,suid).

---

