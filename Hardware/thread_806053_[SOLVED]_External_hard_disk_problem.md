---
title: "[SOLVED] External hard disk problem"
date: 2008-05-24
forum: Hardware
---

### Post by fyz on 2008-05-24
Dear all, I just bought an external hard disk (Maxtor). But when I plug in to the USB port, I can see the disk, but I can not write to it because it is read-only. But if I plug it into windows vista, I can write to it. Anybody can help me to make it writable under Ubuntu 7.10? Thanks!

By the way, the box says it is compartible with vista, XP, etc., but dosen't mention linux which worries me.

---

### Post by pacificial on 2008-07-28
Hi, 

it seems that your hard disk is virus infected or you didnt mounted it. Try to mount it then perform write operation. If still error comes then use stellar phoenix ["]linux recovery ]("http://www.data-recovery-linux.com)software which will fix the error and again start to mount your hard drive. Now you will not get the write error.

---

### Post by Lucky LIX on 2008-07-28
To change read/write rights very easily you can run Nautilus (the file browser in Gnome, as you probably know) as super user by typing the following in the terminal (command line) :
/sudo nautilus
Now you should be able to navigate to your external drive, change the properties to make your account the owner with the limitations you like.

Hope that makes any sense and solves your problem ;)

Cheers

---

### Post by jbrown96 on 2008-07-28
Changing ownership is the easiest way to fix this problem. I believe you can do it within Nautilus on the same page that the previous poster mentioned. However, I would do it from the command line. Ubuntu mounts external hard drives and flash drives in /media/disk, /media/disk-1, /media/disk-2, etc. You need to determine the mount point. If you open the drive and click the up arrow, you should be able to figure out which disk is the one that you want. If it's the only storage device connected, then it should be /media/disk/. Open a terminal and copy the following command (change the /media/disk part if yours is different and change username to whatever your username is - make sure you type it twice, separated by a colon) ```
sudo chown username:username -R /media/disk
```

---

