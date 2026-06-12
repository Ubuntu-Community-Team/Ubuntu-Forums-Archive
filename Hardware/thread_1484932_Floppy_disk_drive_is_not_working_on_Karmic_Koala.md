---
title: "Floppy disk drive is not working on Karmic Koala"
date: 2010-05-16
forum: Hardware
---

### Post by Homero C. de Almeida on 2010-05-16
I'm having a hard time trying to get a floppy disk drive to work with Ubuntu 9.10.

I insert the floppy, but whenever I try to mount, it doesn't work. No error message is displayed, it just doesn't show anything.

> 
# mount -t msdos /dev/fd0 /media/floppy0/
# ls -l /media/floppy0/
total 0
# umount /media/floppy0
umount: /media/floppy0: not mounted
Nothing is logged on dmsg or syslog.

I tried to use fdmount also. No luck but at least I get an error message:

> 
# fdmount fd0 /media/floppy0/
fdmount (/dev/fd0): ioctl(code) failed: Operation not permitted
# echo $?
255
The floppy is not empty and there are no hardware problems with the drive. I checked that using the same disk (which is an old Win98 recovery disk) to boot the system, and it works without any problem.

Does anybody have any idea on what I can do to get it working?

---

### Post by pixelatedpete on 2010-08-09
I don't know if this'll help you, but I was having the same problem in 10.04 (lucid). 

However, when I removed the automount line from fstab:

```
 /dev/fdo0      /media/floppy0  auto defaults,utf8 0 0
```

and then tried to mount the floppy manually:

```
sudo mkdir /media/myfloppy
``` (or wherever you want to mount the drive)

```
 sudo mount -t vfat /dev/fd0 /media/myfloppy
```

it worked!

---

### Post by bkline on 2010-08-20
Same problem with usb floppy on 64-bit Ubuntu 10.4: mount "works" for a second or so (I can see the icon flash up on the desktop and then disappear) but then it's gone.

---

