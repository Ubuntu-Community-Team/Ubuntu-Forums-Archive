---
title: "Can't Access 2nd Hard Drive"
date: 2009-01-18
forum: Hardware
---

### Post by jplunday on 2009-01-18
I can get access to my 2nd hard drive but the other users on my desktop can't. It contains all my media files so it would be good if they could use it also.
I've tried a multitude of different fstab settings but I only succeeded in removing my own access. It seems as long as the drive mounts with my uid then I can get access.

Here is what's in my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
usbfs	/proc/bus/usb	usbfs	devmode=664	0	0
#Entry for /dev/sda1 :
UUID=b88d7367-0977-4c41-809a-a963898c8d4b	/	ext3	relatime,errors=remount-ro	0	1
#Entry for /dev/sdb1 :
UUID=74B9-6536	/media/disk	vfat	defaults,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush	0	2
#Entry for /dev/sda5 :
UUID=b474087e-36f4-439b-bb8f-8c3e7d7e2c63	none	swap	sw	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0


The disk in question is /dev/sdb1 and I'm running Ubuntu 8.10. Any help would be appreciated. Thanks

---

### Post by Kanga on 2009-01-18
I wonder if changing the authorizations for the other users would work.

System - administration - authorizations, then scroll down to storage, or policy kit,  where it is possible to revoke or allow authorizations to other users.

---

### Post by cdtech on 2009-01-18
Looking at the "fstab" man page, I see you would need to add "user" to the list of comma separated options to allow a user to mount the drive.

---

### Post by jplunday on 2009-01-18
Thanks for the quick response guys. I tried the "user" option in the fstab before with no effect. It seems the other users can mount the drive but they can't access the drive. Error message says "you do not have permissions to access these files".

Kanga - I checked out the Authorizations. There was nothing set under Policykit but under Storage the option "Mount File System from Internal Drives" did only have myself with permission under Explicit Authorizations. So I added another user with "must be on console, must be on active session" but it had no effect. So I changed Implicit Authorizations to be Yes for anyone and Yes for active console. It also had no effect. 

I'm really stumped on this one.

---

### Post by efalk on 2009-01-18
You should double-check that the UUID= entries are correct.  I upgraded to Hardy last night, and my fstab was trashed.

> # /dev/sda2 -- converted during upgrade to edgy
UUID=32db6025-9e17-4bc0-b288-7c280368cc59 / ext2 defaults,errors=remount-ro 0 1

One small glitch:  **ls -l /dev/disks/by-uuid** shows that 32db6025-9e17-4bc0-b288-7c280368cc59 is actually /dev/sdb2.  Thank goodness I noticed this before my nightly backups ran.

So now I'm in this state where I really don't know which disk is which, and where Hardy actually got installed, or what.

---

### Post by jplunday on 2009-01-18
I ran ls -l /dev/disk/by-uuid and that seems to check out with what's in fstab.

> lrwxrwxrwx 1 root root 10 2009-01-18 09:33 74B9-6536 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2009-01-18 09:33 b474087e-36f4-439b-bb8f-8c3e7d7e2c63 -> ../../sda5
lrwxrwxrwx 1 root root 10 2009-01-18 09:33 b88d7367-0977-4c41-809a-a963898c8d4b -> ../../sda1

I never would have thought of checking that out but it doesn't seem to be my issue.

---

### Post by jplunday on 2009-01-20
I found a solution on another post for accessing a FAT32 drive. I changed the fstab to look like the following and all is working. Thanks everyone.

> #Entry for /dev/sdb1 :
UUID=74B9-6536	/media/disk vfat users,rw,owner,umask=000 0 0

---

