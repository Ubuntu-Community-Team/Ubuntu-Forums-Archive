---
title: "FUSE vs Canon Powershot SD 1000"
date: 2009-09-23
forum: Hardware
---

### Post by nickneedsausername on 2009-09-23
Hello,

I'm trying to get my camera to mount via FUSE, and I'm stuck.

First of all, let me say that I'm using a Canon.  Canons do not act like a USB hard drive (instead they use ptp).  So, I am using gphotofs to allow me to mount the camera as a filesystem.

I can mount the filesystem as root and everything works fine.

When I mount it as a non-privileged user, the mount "succeeds," but I get an Input/Output error on all file accesses within the mount point.

I /think/ the problem is that the device belongs to user root group plugdev, but the fuse daemon is running as user nick group nick.  I am a member of groups plugdev and fuse, but the fuse daemon inherits the wrong group.

Your advice is appreciated.  Additional details follow:

Root can mount successfully:

```

viperfish:/home/nick# mount /media/camera/
viperfish:/home/nick# ls /media/camera/
store_00010001
viperfish:/home/nick# umount /media/camera/

```User nick cannot:

```

nick@viperfish:~$ mount /media/camera/
nick@viperfish:~$ ls /media/camera/
ls: reading directory /media/camera/: Input/output error
nick@viperfish:~$ umount /media/camera/

```User nick should have the correct permissions:

```

nick@viperfish:~$ id
uid=1000(nick) gid=1000(nick),46(plugdev),104(fuse),1000(nick),
(and ten or more so groups)

```On the mount point:

```

nick@viperfish:~$ ls -ld /media/camera/
drwxrwx--- 2 root plugdev 4096 2009-09-17 17:19 /media/camera/

```And the camera device:

```

nick@viperfish:~$ ls -ld /dev/usbdev*
crw-rw---- 1 root plugdev 252,  1 2009-09-23 12:22 /dev/usbdev1.1_ep00
(and 20 or so more or less identical lines)

```And this is the fstab line:

```

nick@viperfish:~$ grep camera /etc/fstab 
gphotofs  /media/camera   fuse noatime,async,user,rw,noauto,noexec,nosuid,nodev 0 0

```

For what it's worth, I'm using ubuntu 9.04 amd_64 on a dell.

Thanks,

---

### Post by juergi on 2010-02-19
I get the same error, when the camera (Canon S90) is "mounted" in gnome (whatever "mounted" means). If I "unmount" the camera via nautilus, I can access the directory mounted with gphotofs.

---

