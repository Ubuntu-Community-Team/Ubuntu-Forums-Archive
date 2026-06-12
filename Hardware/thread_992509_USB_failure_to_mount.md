---
title: "USB failure to mount"
date: 2008-11-24
forum: Hardware
---

### Post by shane wiley on 2008-11-24
Have just installed Ubuntu latest (8.x). Because my laptop CD rom is faulty, I used Unetbootin program and an ISO file on a USB stick. Installation went fine BUT the USB drives do not mount memory sticks. If you put any stick in (and these are sticks that work fine on my other Ubuntu machine and on Windows) you see the volume of the stick appearing on the desktop but I get the message
"Cannot mount volume, invalid mount option when attempting to mount the volume".
Now interestingly the whole program was installed by a usb disc that the system will now not mount.
Also (get this) the computer recognises and mounts a USB floppy.
I am a Windows user, if you know how to assist please start from the basics with baby steps, ie first turn computer on, etc.
I have tried things like $ mount/dev/sda1/usb etc etc with no results.

---

### Post by ChanServ on 2008-11-24
have you tried this?:
```
mount -t vfat /rout/to/usb /mount/point -o force
```

---

