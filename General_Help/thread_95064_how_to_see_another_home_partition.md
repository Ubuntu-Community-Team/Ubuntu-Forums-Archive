---
title: "how to see another home partition"
date: 2005-11-25
forum: General Help
---

### Post by skaboss on 2005-11-25
Hello,

Like many others, i just switched from my so loved debian etch to a wonderful kubuntu breezy.
But I would like to access my debian home from kubuntu. So i added this line to my /etc/fstab : 

```
/dev/hdb1       /media/debian     ext3    defaults,errors=remount-ro   0       1
```

That almost works : i can access all files of my debian but my home : /media/debian/home/skaboss appears empty ! 

What did i miss ?

Thanks for your help

---

### Post by Xian on 2005-11-25
Try to see the contents as admin:
$ sudo ls -a /media/debian/home/skaboss

If the contents are listed then check the folder permissions.

---

### Post by skaboss on 2005-11-25
Thanks a lot Xian for your interest in my problem.
I tried your solution, but don't see the content of home, even as root...

---

### Post by Xian on 2005-11-25
Oh, I thought you could see part of /home.
I misread your problem.

Try to mount it manually and see if there is any difference.
First check to see if it is mounted.
$ mount

If it is then unmount it.
$ sudo umount /media/debian

Then mount it from a teminal.
$ sudo mount /dev/hdb1 /media/debian

What do you see??

---

### Post by skaboss on 2005-11-26
Hello Xian

I followed your advice. When i mount /dev/hdb1 manually, i see dev, boot, usr and so on. I can also see their contents.
I see also /home, but it is still empty.

---

### Post by utcamperj on 2005-11-26
I would guess that you had more than one partition on your old drive.  Try running:

sudo fdisk -l /dev/hdb

It should list the /dev/hdb1 partition that you've already mounted, and a Linux Swap partition.  If it lists any other Linux partitions, try mounting those and see what you get.

What you describe would happen if the /home directory you're finding was just a mount point and your actual home data was in another partition.

---

### Post by skaboss on 2005-11-26
Utcamperj, you were absolutely right !
My debian home partition is actually on hdb9.
I'm really stupid.
Thanks a lot Utcamperj and Xian for your great help   :D

---

