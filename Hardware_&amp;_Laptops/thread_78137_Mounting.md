---
title: "Mounting"
date: 2005-10-17
forum: Hardware &amp; Laptops
---

### Post by penguinchrissy on 2005-10-17
I tried to mount a hard drive and it worked but when I restarted my computer I lost the drive is there I way I can make it stay

---

### Post by Murgle on 2005-10-17
you will need to add it to your /etc/fstab.  if you know the type and location of the hardrive (/dev/hdb1) for example then you should be fine.  do this by typing 

sudo gedit /etc/fstab

then you add another line for your harddrive, the first colum is where the device for the harddrive is, such as /dev/hda1 (the first partition on the fisrt drive) the second colum is where you want to mount it, the third colum is the type such as ext3 or reiser, the forth colum is the options and you probably want to leave that just as defaults although I believe that the user option allows you to umount it without sudo, the last two colums you should probably just have as 0 and 0, then save the file and when you re-boot it should auto-mount

---

### Post by wylfing on 2005-10-17
The strict answer is "Yes, you can make it stay." :)

What kind of drive are we talking about here? Is it just a separate partition, or a 2nd internal hard drive, or an external USB drive...?

Edit: The reason I asked for the type of drive, Murgle, is because (1) if it's an external drive there's probably no good reason to put it into fstab, and (2) it's possible the OP doesn't know the device name, and knowing what the drive is will help to discover that.

---

### Post by penguinchrissy on 2005-10-23
I edited the tab and it worked but I need to find a way I can write to a NTFS drive I can only find a way to read them but I don't have write privleges and this is an internal harddrive

---

### Post by aysiu on 2005-10-23
[http://www.ubuntuforums.org/showthread.php?t=10175](http://www.ubuntuforums.org/showthread.php?t=10175)

---

