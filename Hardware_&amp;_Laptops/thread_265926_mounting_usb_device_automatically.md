---
title: "mounting usb device automatically"
date: 2006-09-26
forum: Hardware &amp; Laptops
---

### Post by Kulgan on 2006-09-26
I was messing around with things when the bootloader was overwritten, so since I did not have anything of import on the hard drive, I decided that I would be easier to reinstall ubuntu, which has been a very pleasant experience with the past five installations, than to start f*ing around with something that won't work anyways...

So, I have reinstalled Ubuntu, but I can't mount the USB stick that has all the things that I took over from the previous installation. I can mount it from the terminal with 

```
mount /dev/sda/ /media/sda/
```

or something like that, as root. What I am looking for is a way that mounts it without all that hassle - granted, it looks great infront of a winbloz friend when the terminal pops up from nowhere and you quickly do some "complex command", but it is nice that it just does it. 

Tried installing "autofs", don't think that did much in my favour. 

All help welcome :D

K

---

### Post by ahaslam on 2006-09-26
Have you tried entering it in fstab?

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

Tony.

---

### Post by Kulgan on 2006-09-27
yay!

line

```
/dev/sda        /media/sda      vfat    defaults,utf8,umask=007,gid=46 0       1
```

to 

```
/dev/sda        /media/sda      vfat    [COLOR="Red"]user[/COLOR],defaults,utf8,umask=007,gid=46 0       1
```

in /ect/fstab gave success, and even the little icons as usual :D

Thanks

---

