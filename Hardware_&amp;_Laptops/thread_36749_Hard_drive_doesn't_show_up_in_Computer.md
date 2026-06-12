---
title: "Hard drive doesn't show up in Computer"
date: 2005-05-24
forum: Hardware &amp; Laptops
---

### Post by szczyp on 2005-05-24
I have a hard drive disk in FAT32 file system. I have edited the fstab file like this:
dev/hdd1	/media/disk  vfat    umask=000       0       0
Now, when I go to /media I can browse the contents of the disk, but I also would like to be able to see it in the Computer view, where are my other disk, floopy and CD-ROM drives.
What did I do wrong?

---

### Post by rickwood on 2005-05-26
This may be a hal/dbus problem that lots of people are having (including me).  Have a look at this thread to see what worked for me.  Look at stoneguy's post about half way down the page:

[http://ubuntuforums.org/showthread.php?t=21508&page=4&pp=10](http://ubuntuforums.org/showthread.php?t=21508&page=4&pp=10)

---

