---
title: "mounting ipod touch?"
date: 2008-09-08
forum: General Help
---

### Post by mo.reina on 2008-09-08
hi,

is there any way to mount an ipod touch (firmware v2.0) withouth jailbreaking?  not interested in synching it, just mounting so that i can transfer videos, music, etc.

---

### Post by manishtech on 2008-09-08
goto Terminal and type

```
ls /dev/sd*
```

Now plug in the iPod into USB drive and again run the above command and post the output of it

---

### Post by mo.reina on 2008-09-08
before plugging the ipod

```
mo@mo-laptop:~$ ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda5
mo@mo-laptop:~$ 

```

after pluggin the ipod

```
mo@mo-laptop:~$ ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda5
mo@mo-laptop:~$ 

```

---

### Post by manishtech on 2008-09-08
Means your ipod's flash drive isnt being detected....

---

### Post by mo.reina on 2008-09-08
right, so what's the solution here besides jailbreaking?

---

### Post by tangibleorange on 2008-09-08
try posting the output of:

```
cat /etc/mtab
```

when the ipod is plugged in.

---

### Post by mo.reina on 2008-09-08
```
/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-19-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/mo/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=mo 0 0
/dev/scd0 /media/cdrom0 iso9660 ro,nosuid,nodev,utf8,user=mo 0 0

```

---

### Post by regala on 2008-09-08
> **mo.reina said:**
> ```
/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-19-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/mo/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=mo 0 0
/dev/scd0 /media/cdrom0 iso9660 ro,nosuid,nodev,utf8,user=mo 0 0

```

It has been known for a while that you have to use ssh and something like sshfs (with filesystem in userspace capability). don't bother try to have it recognized as a simple external usb disk, you are wasting your time.

[http://www.ipodtouchfans.com/forums/showthread.php?p=260605](http://www.ipodtouchfans.com/forums/showthread.php?p=260605)

by the way, I searched Google with "ipod touch linux sync" and this was the fifth entry on the result pages...

rgds

---

### Post by regala on 2008-09-08
> **regala said:**
> It has been known for a while that you have to use ssh and something like sshfs (with filesystem in userspace capability). don't bother try to have it recognized as a simple external usb disk, you are wasting your time.

[http://www.ipodtouchfans.com/forums/showthread.php?p=260605](http://www.ipodtouchfans.com/forums/showthread.php?p=260605)

by the way, I searched Google with "ipod touch linux sync" and this was the fifth entry on the result pages...

rgds

oh :) and no, there really seems to be no without-jailbreaking way of doing this. C'est la vie.
Sorry.

---

### Post by Zorael on 2008-09-08
Well, short of installing a virtual machine with XP/Vista/MacOS and doing it there. Blame Apple.

Here's the wiki link for jailbroken phones/pods. [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

---

### Post by retrovertigo on 2008-09-08
The iPhones and iPod touches are different types of devices and they don't mount themselves like the previous iPods did, not even in Windows and MacOS.

For know, unless you've got a jailbroken iPhone/Touch, yer outta luck in Linux.

---

### Post by 89vision on 2008-09-08
I've only been able to mount my iphone by jailbreaking and using openssh.

---

