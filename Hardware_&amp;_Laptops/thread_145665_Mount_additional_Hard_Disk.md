---
title: "Mount additional Hard Disk"
date: 2006-03-16
forum: Hardware &amp; Laptops
---

### Post by mjfarina on 2006-03-16
I just ripped a hard disk out of an old RH9 machine I was running. I'd like to have that drive accessable to my new Ubuntu machine, but I'm a Linux noob and I have no idea how to mount it. Also, I don't remember what file system the RH9 drive is running.

Can someone let me know how to mount the new hardware, and see the existing files on the drive.

Thanks!! I'm psyched to check this new flavor of linux =).

---

### Post by taurus on 2006-03-16
Assuming that it is a second drive, then run
```

sudo mkdir /media/second
sudo mount -t ext2 /dev/hdb1 /mnt/second

```
If you get an error about filesystem, ext2, then try ext3...

---

### Post by mjfarina on 2006-03-17
Awesome, I'll try it as soon as I get home!!! Thanks!

---

### Post by taurus on 2006-03-17
Just let me know if you get any error or problem with it.

---

### Post by mjfarina on 2006-03-17
Will do...If you don't mind me bothing, what's with the /media/second? Is that where drive mounts go in Ubuntu? I've done some samba mounting before and it seems I always put my dirs under /mnt directory. Based on what you gave me, it almost looks like if I put a dir under /media it copies under /mnt. Maybe I have no idea what I'm talking about =). I'm just trying to wrap my head around this OS. Thanks again!

---

### Post by taurus on 2006-03-17
Normally, you want to mount stuff under /mnt (that's what Unix does it back then) but if you want Gnome to create a short cut on your desktop, then you need to mount it in /media!!!  Personally, I always mount my stuff in /mnt (may as well do it the right way) but it seems to me that most people here want their stuff to be mounted in /media...  So, if you want to mount it in /mnt, go for it as I would.  ;)

---

### Post by mjfarina on 2006-03-17
Great information! Thanks!!

---

### Post by mjfarina on 2006-03-17
PERFECT!! Turns out I had to mount /dev/hdb2, hdb1 was one of the boot or swap partitions...or whatever their called. Hdb2 has all my stuff =). Thanks again!!!

---

### Post by jcotter on 2007-07-04
thanks for the help with this, workes perfectly for me also.

---

