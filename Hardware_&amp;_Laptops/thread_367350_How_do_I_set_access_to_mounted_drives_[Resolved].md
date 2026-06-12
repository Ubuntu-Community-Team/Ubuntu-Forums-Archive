---
title: "How do I set access to mounted drives? [Resolved]"
date: 2007-02-22
forum: Hardware &amp; Laptops
---

### Post by DennShin on 2007-02-22
Hi guys, 
      I hope you can help I am trying to mount two hard drives.  One being formatted fat32 the other NTFS.  Both drives contain information I need from when I had Microsoft Windows installed.  The drives were not mounted automaticaly when I installed Ubuntu (6.06).  So I figured I would read Man Mount and do it myself.  Well I managed to get both drives mounted I can see them and I can see the data present on them, The ntfs is Read Only which I expected but the fat32 one is also read only with the permissions set to root only.  Any idea's?

MOUNT -L
```
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-28-386/volatile type tmpfs (rw)
/dev/sda1 on /home/dennshin/250gb_Drive type ntfs (rw,nls=utf8,umask=0222)
/dev/hdb1 on /home/dennshin/60gb_Drive type vfat (rw,iocharset=utf8,umask=0222) [MASTER]

```

If you need any more information please let me know.

---

### Post by aysiu on 2007-02-22
FAT32 should be umask=000, not umask=0222

More details here:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by DennShin on 2007-02-22
Thank You!  I was setting that before and just realized I was not unmounting then remounting the drive to produce the effect.  Much thanks :)

---

