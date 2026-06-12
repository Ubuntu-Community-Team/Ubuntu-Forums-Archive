---
title: "How to automount creative zen"
date: 2008-09-13
forum: Hardware
---

### Post by shikharus on 2008-09-13
Hello guyz i have recently migrated to ubuntu 8.04 from windows.
now the problem is that i want my creative zen to work with ubuntu.now by reading an article i came to know that by installing mtpfs & mtpfs tools i can make ubuntu detect my zen.
now whenever i try to mount it then everytime i have to type in command 

mtpfs -o allow_other /media/zen

and to unmount it

fusermount -u /media/zen

I want that ubuntu should automatically mount it as soon as i connect it.Like it mounts the usb pen drive.
Please help me.

---

### Post by muranyia on 2010-02-24
Create your mountpoint (sudo mkdir /media/Zen).

Add this to /etc/fstab :

```
mtpfs /media/Zen   fuse   noauto,user,allow_other   0 0
```

Add this to /lib/udev/rules.d/45-libmtp8.rules (it's broken into two lines now, stick it back to one line AND match idProduct with the output of lsusb):

```
ATTR{idVendor}=="041e", ATTR{idProduct}=="4161", SYMLINK+="libmtp-%k", MODE="660",
 GROUP="audio", RUN+="/bin/mount /media/Zen"
```



I still cannot mount/umount this as a regular user, but at least it is an automount. :P

---

