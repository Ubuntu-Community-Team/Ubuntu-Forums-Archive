---
title: "[SOLVED] remount partition to /home when home already exists"
date: 2008-11-18
forum: Hardware
---

### Post by airjaw on 2008-11-18
Hi guys, got myself into a bit of a pickle here upon reinstalling 8.10 and hope someone can help, so that i don't have to reinstall 8.10 over again.

My previous setup on 8.04 had root mounted on /dev/sda3
and /home mounted on /dev/sda2

Upon installing 8.10 I mounted root again to /dev/sda3 but forgot to mount /home to /dev/sda2

So now I have two /home , one on sda3 and my old /home on sda2, which is now mounted in /media/sda2

IS there a way I can reconcile this?  I tried to go to properties for /sda2 but I mistakenly put the mount point as /home/ , with the last slash I think messing the mount up.  Now I can't access properties anymore.

Thanks


edit: :if someone could point me in a good direction to go in the terminal, i would appreciate it. I knwo there is /etc/fstab but mine so far doesn't show much.
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=a72a4c0e-6c54-4319-a502-294187c5e700 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=315badc5-b892-4cad-b994-500b4daa9929 none            swap    sw              0       0
# /dev/sda6
UUID=c7080b1b-92c8-4237-9505-08519ff3a851 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

It doesn't have sda2 or sda3.

Where do I find unmounted drives?

---

### Post by taurus on 2008-11-18
If you don't have anything valuable on the new $HOME, you can remove it.  Then, add an entry in /etc/fstab for the old home, separate partition.  Reboot and your old /home will be mounted.

```
sudo fdisk -l
sudo blkid
```

---

### Post by airjaw on 2008-11-19
Thanks for the help.  I just reinstalled ubuntu.. did it the long way.

---

