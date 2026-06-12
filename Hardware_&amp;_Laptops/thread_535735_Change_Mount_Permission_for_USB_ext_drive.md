---
title: "Change Mount Permission for USB ext drive?"
date: 2007-08-26
forum: Hardware &amp; Laptops
---

### Post by myke on 2007-08-26
I have a Western Digital portable hard drive that I bought for that very reason.  It's very slim and small (less than the size of an index card) and holds 150GB so I can carry lots of stuff back and forth from work and home.  

This drive is formatted in Vfat/Fat32 and was auto detected nicely by Feisty.   All read and write functions work as well as they do under Windows XP at work.  

Here's my only problem:   when I try and safely unmount the drive, it gives me an error of not having permission to do so.  I have my system set where I can login graphically as root so I did so and can umount fine as root which I expected.  The problem is, I don't know how to change the mount permissions.  I have full read/write access but only can unmount as root.   I can just unplug the thing but it gives me the error that I've unsafely removed the drive and I'd rather not take the chance in damaging it anyway.

Long story short:  how do I change the permission where I not only have read/write access to this drive but can unmount it safely as well without logging in as root?   

Here's the exact error I get when trying to unmount via my non-root login:

[I][B]Cannot unmount volume
You are not privileged to unmount the volume 'WD Passport'.
unmount:  only root can unmount /dev/sdb1 from /media/sdb1[/B][/I]

Here's the line that pertains to the drive in fstab:
[B]
/dev/sdb1 /media/sdb1 vfat iocharset=utf8,umask=000 0 0[/B]

Here's the line that pertains to the drive in mtab:

**/dev/sdb1 /media/sdb1 vfat rw,iocharset=utf8,umask=000 0 0**

I thought changing something in one of these two files might be the answer but I'd rather not mess things up so I'm asking for advice.   Anyone know how to fix this issue??

---

### Post by ankorie on 2007-08-26
I think all you need to do is add "users" or "user" to your fstab like this

/dev/sdb1 /media/sdb1 vfat iocharset=utf8,umask=000,users 0 0

and I think you can add it to your mtab as well

/dev/sdb1 /media/sdb1 vfat rw,iocharset=utf8,umask=000,users 0 0

documentation for these are in man mount here are some snipits

user             Allow  an  ordinary  user  to mount the file system.  The
                     name of the mounting user is written to mtab so  that  he
                     can  unmount  the file system again.

users            Allow every user to mount and unmount  the  file  system.

---

### Post by myke on 2007-08-26
Thanks!  Adding "users" in fstab did the picture.  I initially had an error and thought that it didn't work fully but I did a system restart and after that, your solution worked like a charm.   I didn't add it to mtab but apparantly adding it to fstab caused the system to auto update the mtab file to this:
[B]
/dev/sdb1 /media/sdb1 vfat rw,noexec,nosuid,nodev,iocharset=utf8,umask=000 0 0[/B]

This did not affect my read/write capability and now I can safely remove the drive for transporting without shutting down everything.

Simple solution.

THANKS for the help!

---

### Post by Black Horn on 2007-08-28
i write "/dev/sda1 /media/sda1 vfat iocharset=utf8,umask=000,users 0 0"
and it said "Permission denied".....Dont know i just wanna chang permission of my USB flash memory.Can u help?

---

### Post by Kavster on 2008-06-03
you might need to use the following before you can edit fstab:

```
sudo gedit /etc/fstab
```

---

