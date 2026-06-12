---
title: "Mounting a second hard drive to /"
date: 2006-08-25
forum: Hardware &amp; Laptops
---

### Post by badi95 on 2006-08-25
Hello everyone,
I installed ubuntu on a 10 gig hd, and now want to add more space so it can function as a file server better.  I have my new 160 hard drive partitioned to Ext3, but I don't know how use it.  I am kinda a linux n00b.  I want to add space to the whole / file system if possible.  Thanks in advance for your help.

---

### Post by scxtt on 2006-08-25
you won't technically "add" it to the root F/S (which is what / is) - you'll mount it off of the / F/S ... something like:

#:> [B]mount -t ext3 /dev/hdc1 /media/new_drive
[/B]
if hda is your / disk, hdb is your CDROM, and hdc is your 160GB drive ...

---

### Post by aysiu on 2006-08-25
You can't just extend the / drive to encompass another physically separate drive. You can, however, move a folder over to the other drive and then mount it within /

This shows you how to do it for /home, but the same principle should apply for /var, /usr, or any of the other directories.
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

---

