---
title: "[SOLVED] Mounting external USB hard drive as read/write"
date: 2008-08-29
forum: General Help
---

### Post by Sam Lars on 2008-08-29
Hello,
I'm trying to mount an external USB drive with fstab with read/write access.
I have two ext3 hard drives that work great.
When unmounted, ls -l shows this for them:
```
drwxr-xr-x  2 root root  4096 2007-11-22 17:35 37
drwxr-xr-x  2 root root  4096 2008-08-13 18:24 500
drwxr-xr-x  2 root root  4096 2008-08-10 18:39 60
```
The 500 is the external, the others are the internals.
When I mount them, ls -l shows this:
```
drwxrwxrwx 11 root root  4096 2008-08-22 18:33 37
drwxr-xr-x  8 root root 32768 1969-12-31 18:00 500
drwxrwxrwx  3 root root  4096 2008-08-15 09:55 60
```
This would explain why I can't write if I'm not root.
Here's my fstab:
```
/dev/sdc1 /37 ext3 defaults,errors=remount-ro 0 1
/dev/sdb1 /60 ext3 defaults,errors=remount-ro 0 1
/dev/sdd1 /500 msdos auto,users,uid=1000,gid=1000,dmask=46,fmask=137,utf8 0 1
```
I have tried the same options as the ext3 drives, just the rw option, and a couple other suggestions from the forums.
No matter what I do, I get
```
mkdir: cannot create directory `test': Permission denied
```
Is this related to the drive being a FAT/msdos filesystem?  Would I be better off just reformatting as ext3?  If so, how do I do that from the command line?
Thanks.


Edit: I finally found on a Gentoo wiki:
```
umask=0000
```
lets everyone have full permissions.
I also changed msdos to vfat so that I could have more that 8 characters in an object's name. :-|

---

