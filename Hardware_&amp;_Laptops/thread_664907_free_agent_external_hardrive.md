---
title: "free agent external hardrive"
date: 2008-01-11
forum: Hardware &amp; Laptops
---

### Post by rauko113 on 2008-01-11
hi im a noob, just installed 7.10 and its really cool, but im not sure how to get my external hardrive - seagate free agent - to work.  basically all the software it comes with is for mac or windows, so i got wine emulater to install the windows software, but installation software just freezes when i run it. ive looked around and found similar posts, but they didnt really help.  any ideas?

---

### Post by logos34 on 2008-01-11
you don't need to do any of that.

Is it recognized?

sudo fdisk -l

sudo lshw -C disk

---

### Post by rauko113 on 2008-01-11
k

---

### Post by rauko113 on 2008-01-11
so i guess its not recognized.
is there something i can do to change that?

---

### Post by chicken101 on 2008-01-11
I have a free agent drive and I got it to work 100%.  

1) to get read/write access to it you might need to just add it to your fstab file, at least I needed to with my free agent drive.  
> sudo gedit /etc/fstab

and add this to the bottom of the file

> /dev/sdb1 /media/mountpoint ntfs defualts 

if it's the first usb drive you have use sdb1, the second sdc1 etc.
you must make a mount point by doing 
> sudo mkdir /media/mountpoint or whatever you want to call it.

Also, the free agents have a problem with linux because they spin down while not in use and causes I/O errors of all kinds.  You might have to use a windows or mac partition to run the software so you can set the drive to never spin down.

---

### Post by rauko113 on 2008-01-11
awesome, thanks guys its working now.  hopefully it doesnt spin down like you said but we'll see...

---

### Post by logos34 on 2008-01-11
So editing fstab caused it to start working?

You might be able to set the spindown time with hdparm, if it's an ide drive underneath. (see man hdparm)

---

