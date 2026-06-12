---
title: "Lost File System"
date: 2005-07-26
forum: Hardware &amp; Laptops
---

### Post by crobe on 2005-07-26
I've been using ubuntu for a few months, and it worked pretty well... however my laptop crashed (probably due to overheating) and now I seem to lack a file system.  I get grub error 17 on boot, which is "Cannot mount selected partition" i threw in the hoary install cd to see if i could just reinstall ubuntu and not touch the home directory but when i view the linux partition it says no existing file system detected.

Is there anyways to repair the file system?  I am willing to go ahead and just reinstall ubuntu from scratch but there is one file that I had been working on that I would like to recover.

---

### Post by crobe on 2005-07-26
I booted up using the live cd and when i run fdisk -l, i get nothing in return.

---

### Post by ubuntp on 2005-07-26
It's probably just the partition table that's corrupted, the file can be recovered i'm sure, so don't format the drive yet.

---

### Post by macgyver2 on 2005-07-26
Boot up that handy LiveCD then head over to [www.cgsecurity.org]("http://www.cgsecurity.org") and grab the testdisk utility. Excellent program for fixing up partition tables. It basically scans the disk looking for the actual markers that designate where your partitions start. It has good documentation, too, but if you need further help, well, I just learned how to use the program (and how good it is) first-hand this weekend :-\" (I seem to like doing things I really know I shouldn't do...I think I do them on purpose because I wind up having fun fixing things).

---

