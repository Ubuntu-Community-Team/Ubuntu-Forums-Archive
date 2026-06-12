---
title: "cannot copy files on external drive"
date: 2012-02-02
forum: Hardware
---

### Post by mac67 on 2012-02-02
Hi,

when I try to copy files from my home directory (or any directory) into a 500 GB USB external drive, I get a message like "permission denied: read-only drive". This happens with Ubuntu 11.10 on my new laptop. I can only copy files into a 4GB USB pen drive.

I tried to change permissions, using "chmod 777 drivename" but nothing changed. I changed permissions from Windows 7, but still no way to copy files into it in Ubuntu.

It is definitely a problem of Ubuntu 11.10, since I can copy files from Kubuntu 11.04 (on another older laptop) into the same external USB drive.

Any idea? Thanks a lot.

---

### Post by mac67 on 2012-02-03
Nobody has any clue about my problem? Nobody had the same experience?

---

### Post by Jon Delorey on 2012-02-04
I'm having the same problem with all USB devices that I attach.  This includes USB flash drives with ext3 and vfat file systems.  The same problem with attaching an iPod classic and a Nook simple touch.  Neither will sync with Banshee or Calibre and the permissions are set to root.   

Everything used to work fine and this only began recently.  Maybe after the last kernal update?

I can change permissions or just work as root and move files around but something is different.  

There is another recent thread on this topic that's marked solved but that solution won't work for mounting the iPod and Nook.  
[http://ubuntuforums.org/showthread.php?t=1917790&highlight=usb+permissions](http://ubuntuforums.org/showthread.php?t=1917790&highlight=usb+permissions)

---

### Post by Jon Delorey on 2012-02-04
I forgot to mention that I can't dismount the drives (or devices) either without being root.  I get permission denied.

---

### Post by Jon Delorey on 2012-02-04
Correction: I can work with the files as root but cannot change permissions.

---

### Post by mac67 on 2012-02-05
Thank you for answering.

I have not solved the problem yet, I am not a Linux expert and change settings via terminal only when I know well what I am doing.

I have some news, though: it must be the NTFS file system. In the external drive I have one partition that contains Ubuntu 11.04. I can copy files from laptop Ubuntu into external drive Ubuntu.

:confused:

---

### Post by mac67 on 2012-02-05
> **Jon Delorey said:**
> I'm having the same problem with all USB devices that I attach.  This includes USB flash drives with ext3 and vfat file systems.  The same problem with attaching an iPod classic and a Nook simple touch.  Neither will sync with Banshee or Calibre and the permissions are set to root.   

Everything used to work fine and this only began recently.  Maybe after the last kernal update?

I can change permissions or just work as root and move files around but something is different.  

There is another recent thread on this topic that's marked solved but that solution won't work for mounting the iPod and Nook.  
[http://ubuntuforums.org/showthread.php?t=1917790&highlight=usb+permissions](http://ubuntuforums.org/showthread.php?t=1917790&highlight=usb+permissions)

That solution looks (to me, at least) a non-solution, since a full separation between Windows partitions and Linux partitions is exactly the opposite of what I look for.

---

### Post by aasdfasdfg on 2012-02-05
> **mac67 said:**
> Hi,

when I try to copy files from my home directory (or any directory) into a 500 GB USB external drive, I get a message like "permission denied: read-only drive". This happens with Ubuntu 11.10 on my new laptop. I can only copy files into a 4GB USB pen drive.

I tried to change permissions, using "chmod 777 drivename" but nothing changed. I changed permissions from Windows 7, but still no way to copy files into it in Ubuntu.

It is definitely a problem of Ubuntu 11.10, since I can copy files from Kubuntu 11.04 (on another older laptop) into the same external USB drive.

Any idea? Thanks a lot.

It sounds like the drive was mounted with the -ro (read only) flag. In order to make changes, you will need to mount it as -rw (read write).

As you said, you are not a power user, so I am confused about how this came to be. I think the easiest way to solve this would be to modify your ```
/etc/fstab
```We can help you out further if you post the contents of this file.
I would recommend running ```
gedit /etc/fstab
``` from a terminal and copying the contents here. There should not be any personally identifying information in that file, so it is safe posting it on the internet.

---

### Post by dFlyer on 2012-02-05
Is the external drive ntfs, win32, dos, ext3 or ext4?

---

### Post by varunendra on 2012-02-06
> **mac67 said:**
> That solution looks (to me, at least) a non-solution, since a full separation between Windows partitions and Linux partitions is exactly the opposite of what I look for.
While the USB drive is plugged in, please run and post the output of:
```
mount
```And while you are at it, plug in the drive in Windows, run *chkdsk* on it and see if any errors are found on it. If there are, run *chkdsk -f* to fix them. Linux mounts ntfs partitions as read-only if it contains filesystem errors or is not 'Clean' (the case when you unplug it without "safely removing" it). So running '*chkdsk -f*', then "safely removing" it may solve the problem.

Else we'll try manually mounting it with read-write permission (aka force-mounting!).

---

### Post by mac67 on 2012-02-06
Hi, thank you all for helping.

For some strange reason I cannot save when I try to post the content of fstab.

---

### Post by mac67 on 2012-02-08
> **aasdfasdfg said:**
> It sounds like the drive was mounted with the -ro (read only) flag. In order to make changes, you will need to mount it as -rw (read write).

As you said, you are not a power user, so I am confused about how this came to be. I think the easiest way to solve this would be to modify your ```
/etc/fstab
```We can help you out further if you post the contents of this file.
I would recommend running ```
gedit /etc/fstab
``` from a terminal and copying the contents here. There should not be any personally identifying information in that file, so it is safe posting it on the internet.

Hi

sorry for my late reply, but I could not struggle with the problem in these days.

So, I have side by side the old laptop with KUbuntu 11.04 (where external drives are recognized and I can copy into, no problem at all) and the new one with Ubuntu 11.1064-bit (where I cannot copy into external drives, but only into pen drives).

Looking at fstab, I do not see any relevant difference.

Both have the Ubuntu drive: 

the old one: ext 3, the options are relatime,errors=remount-ro, then 0 and 1
the new one: ext 4, the option is errors=remount-ro, then 0 and 1

then both have the swap drive, identical parameters

finally, the old one also has the dvd drive. Nothing in the new one.

---

### Post by varunendra on 2012-02-08
I think you should be aware of a few things:

[LIST]
[*]The fstab file WILL NOT contain windows partitions unless you manually add entries for them.
[*]chmod or chown WILL NOT work on windows partitions
[*]Linux WILL NOT mount an ntfs partition with read-write permission if it is not marked as 'Clean'.
[/LIST]
Accordingly, please do what I suggested in my previous post. It really won't hurt if couldn't fix things.

---

### Post by mac67 on 2012-02-08
> **varunendra said:**
> While the USB drive is plugged in, please run and post the output of:
```
mount
```

Hi, thanks for helping.

All partitions on external drive are rw. Windows partitions are type fuseblk, whereas the Ubuntu partition (I installed it also on the external drive) is ext4.

---

### Post by varunendra on 2012-02-08
Please post the output here so we all can see the details.

---

### Post by mac67 on 2012-02-08
> **varunendra said:**
> I think you should be aware of a few things:

[LIST]
[*]The fstab file WILL NOT contain windows partitions unless you manually add entries for them.
[*]chmod or chown WILL NOT work on windows partitions
[*]Linux WILL NOT mount an ntfs partition with read-write permission if it is not marked as 'Clean'.
[/LIST]
Accordingly, please do what I suggested in my previous post. It really won't hurt if couldn't fix things.

Hi,

I already checked one partition under Windows and there was no error.

I still do not understand one thing: if the ntfs partition is not "clean", shouldn't I have problems also with Ubuntu in the old laptop?

---

### Post by varunendra on 2012-02-08
> **mac67 said:**
> I still do not understand one thing: if the ntfs partition is not "clean", shouldn't I have problems also with Ubuntu in the old laptop?
Yes there should be. It is just a possibility, not a certainty.

---

### Post by mac67 on 2012-02-08
Hi, here it is:

> 

/dev/sda6 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev/ type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/markus/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=markus)
/dev/sdb1 on /media/STORE N GO type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sdc2 on /media/d60c6a66-e75f-4282-b3b6-45d44d3e8349 type ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc3 on /media/4AAD708D32A3A7A0 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc4 on /media/02541EAD0604C479 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)




---

### Post by mac67 on 2012-02-09
Well...

I decided to use Scandisk with Windows 7 on one of those external NTFS drives. No errors. Then I looked at the properties and found that only Administrator had privileges to write. So I extended all privileges to every user. And now, from Ubuntu, I can copy files into those NTFS drives. The problem is solved.

Nonetheless, I would like to understand what happened. I guess that the first time I connected those drives to the new laptop, Windows 7 changed permissions without notifying anything. Is that possible? And how does it come that the restrictions did not apply to Ubuntu on the older laptop?

Thank you all for care.

---

