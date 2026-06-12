---
title: "usb floppy doesn't mount automatically"
date: 2008-01-27
forum: Hardware &amp; Laptops
---

### Post by zhangweiwu on 2008-01-27
Dear all

I have a USB floppy that comes as part of my Thinkpad Notebook. The USB floppy was recognized as /dev/sdb automatically when plugged, and it works fine if I manually mount it with:
```
$ sudo mount /dev/sdb1 /mnt
```

Although I am a bit curious because as far as I learned, the floppies do not have a partition table on it, thus it should be /dev/sdb. But anyway /dev/sdb1 works. The diskette in it was formatted in FAT and is usable on all other computers here.

The only problem is it doesn't mount automatically. The person who need to use these floppy is our accountant who will never manage to learn command line. Also I cannot write her a script because the device is not always /dev/sdb (it is sdc if it's plugged after a USB flash).

I cannot see it in nautilus. I cannot see it in Disk Mount desktop applet in Gnome. anyway, there is no user-accessible way to mount it.

I read various discussion about such topic by searching and see no working solution yet.

As far as I know showing mount-able device in nautilus is handled by HAL, but I don't know where to check error messages from HAL.

Thanks in advance for help and hints.

P. S. My case looks identical as the one in this thread:
[http://ubuntuforums.org/archive/index.php/t-556142.html](http://ubuntuforums.org/archive/index.php/t-556142.html)

However the only difference is the original poster said his USB drive is probably broken and ended the discussion there, while I can prove it must be working and it works fine for me if mounted manually, the problem lies on how to get it automatically mounted.

---

### Post by zhangweiwu on 2008-01-28
After some experiments I found that if a floppy is formatted as ext2, and plug it in the USB floppy driver, and plug the driver in a usb slot, then the disk can be recognized and automatically mounted and usable in nautilus. This is very easy. MS fat doesn't work.

---

