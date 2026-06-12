---
title: "Cannot access external hard drive"
date: 2007-06-25
forum: Hardware &amp; Laptops
---

### Post by westkoastal on 2007-06-25
I have an external hard drive connected to my computer. But it thinks I'm not the owner so I can't do things like make new folders in it. I can't change the permission settings either, all options are disabled. Any suggestions?

Thanks.

---

### Post by yabbadabbadont on 2007-06-25
As an example, let us assume that the drive is mounted on /media/mydrive.  Then, in a terminal window, run:
```
sudo chown username:username /media/mydrive
```
Substitute your real user name for username.  You should then be able to create/remove files and folders on the drive.

---

### Post by merlinus on 2007-06-25
If he has subdirectories and files, would this not be better?  Or will simply changing ownership of the partition do that for the contents?

```

sudo chown -R username:username /media/mydrive
```

-merlin

---

### Post by westkoastal on 2007-06-25
I get this message when I try both of those suggestions: chown: cannot access `/media/mydrive': No such file or directory

---

### Post by dfreer on 2007-06-25
The above suggestions assume you know the name of the drive. Try looking in /media/, and see the names of the drives listed. My USB drives, for example, are called /media/usbdisk and /media/disk.

Then, I'm willing to bet that your drive is formatted with NTFS, right? If so, you will also need to install and configure ntfs3g, which is a driver for writing to drives formatted with NTFS.

---

### Post by westkoastal on 2007-06-26
Thanks for the tip, I tried it, still no change. I'm still not able to write to the drive. Any other suggestions?

---

### Post by yabbadabbadont on 2007-06-26
Please post the output when you run "mount" in a terminal window.

---

### Post by westkoastal on 2007-06-26
what is the command exactly?

---

### Post by yabbadabbadont on 2007-06-26
mount

---

### Post by westkoastal on 2007-06-26
jesse@jesse-desktop:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdb1 on /media/SimpleDrivePS type ntfs (rw,nosuid,nodev,umask=222,utf8)
jesse@jesse-desktop:~$

---

### Post by yabbadabbadont on 2007-06-26
It is an ntfs drive.  You will have to use the ntfs-3g software in oder to be able to write to it.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by dfreer on 2007-06-26
like i said, you have ntfs as shown in this line:
```
/dev/sdb1 on /media/SimpleDrivePS type **ntfs** (rw,nosuid,nodev,umask=222,utf
```
You need to install the NTFS3G driver in order to write to it, because by default ubuntu can't.

EDIT: oops didn't see the post above me lol

---

### Post by yabbadabbadont on 2007-06-26
> **dfreer said:**
> EDIT: oops didn't see the post above me lol

A little reinforcement never hurt anybody.  :D

---

