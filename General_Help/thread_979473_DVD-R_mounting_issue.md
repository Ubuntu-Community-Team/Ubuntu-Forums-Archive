---
title: "DVD-R mounting issue"
date: 2008-11-12
forum: General Help
---

### Post by badger_8007 on 2008-11-12
Hi

I have an issue with my DVD/RW drive on my laptop, when I insert a data DVD-R (burned in windows, has some avi and text files) and kubuntu tries to mount it, it shows me a message saying "Access denied to /media/cdrom0". It happens only with DVD-R media, I tried already with DVD+R, CD-R, CD-RW, and DVD movies and so far all of them work ok. If I open the same DVD-R using my Windows Vista (I have a dual boot system) on the same machine, it opens ok, with no problems at all. The only way to access the disk under kubuntu is opening konqueror as root, or in a terminal as root. Even then, I have read only access, I can not copy the files to the hard disk, and can not open them with any player.

I already have made a little research on the issue but I was not able to find a solution for this. Have read a lot other threads that point from an upgrade of the UDF module to version 2.5 ([http://ubuntuforums.org/showthread.php?t=718744](http://ubuntuforums.org/showthread.php?t=718744)), to modify the fstab settings for the cdrom for type auto, and so far i can not resolve this. For what I see it is a compatibility issue related to the UDF format under Windows Vista or something like that. The only way it seemed to work was to put on the fstab file the type as iso9660 for cdrom, but then i lose the long filenames, and some of the file cannot be opened anyway.

Now I ask: am I overlooking something in the procedure, or really there is no solution for this issue until today??

Will thank if somebody can help me with it. I am new to Linux, but I like it and try to learn as much as i can.

I attach my fstab file and a screenshot of the error.

I use a Toshiba Laptop A135-S4426, with Intel Core Duo T2250, 1 GB RAM, hard disk SATA 120 GB. The model of the DVD drive is TSSTcorp CDDVD/RW TS-L632D rev. TO03. I use Kubuntu Hardy 8.04 with kernel 2.6.24-21-generic.

fstab file
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda5
UUID=4edae53f-8fa0-4ac1-8c44-aa83310add46 / ext3 nouser,relatime,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda6
UUID=e7299c2f-feae-45a0-ada2-b91ebb333cdb none swap sw 0 0
/dev/scd0 /media/cdrom0 auto user,utf8,noauto,exec,suid 0 0
# /dev/sda2 particion Windows Vista
UUID=0A34ABFE34ABEAC1 /media/sda2 auto user,utf8,atime,auto,rw,dev,exec,suid 0 0

```

---

### Post by cariboo on 2008-11-12
Can you mount the DVD-R manually? In a Applications-->Accessories-->Terminal type:

```
sudo mount /dev/scd0 /media/cdrom
```

If the disk mounts manually then there is osmething wrong with the permissions of the DVD.

Jim

---

### Post by badger_8007 on 2008-11-12
It mounts but i have no access as normal user.

```
freddy@Rosenkreutz:~$ sudo mount /dev/scd0 /media/cdrom
[sudo] password for freddy:
mount: block device /dev/scd0 is write-protected, mounting read-only
freddy@Rosenkreutz:~$ cd /media/cdrom
bash: cd: /media/cdrom: Permission denied
```

If I login as root, then I can have access to the directory, and even can open the files (most are avi movies), but I'd like just to use it normally from inside the desktop (ex. in Konqueror, VLC, etc), is annoying having to change to root everytime I need to open a file.

```
freddy@Rosenkreutz:~$ sudo su
root@Rosenkreutz:/home/freddy# cd /media/cdrom
root@Rosenkreutz:/media/cdrom#
```

Any idea what can be causing this behavior??

By the way, the user and group that the files on the dvd belongs is 4294967295 (mine is 1000), but I already see that on other dvds that can be read with no problems is the same user and group.

```
-r--r--r-- 1 4294967295 4294967295  24248320 2005-03-05 15:50 (AMV) - Hellsing - The world is a Vampire.avi
```

---

