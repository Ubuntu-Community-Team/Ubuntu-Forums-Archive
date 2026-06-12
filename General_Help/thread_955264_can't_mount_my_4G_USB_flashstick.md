---
title: "can't mount my 4G USB flashstick"
date: 2008-10-22
forum: General Help
---

### Post by chunri on 2008-10-22
help!I can't mount my 4G USB flashstick,but other person's USB can be mounted.

---

### Post by namegame on 2008-10-22
what is the file format of the flash drive?

---

### Post by chunri on 2008-10-22
> **namegame said:**
> what is the file format of the flash drive?

fat32.when i use code "cat /proc/partitions" in terminator,it is recognized sdb

---

### Post by Stefanie on 2008-10-22
can you mount it with sudo?

---

### Post by NeuB27 on 2008-10-22
I can tell you how to do it manually, but I don't know why it will not automount, unless its not formatted correctly.
You will need sudo access.
In the terminal use ```
fdisk -l
``` it might tell you that you should run it as sudo, and you can, it should change anything, just remember the -l (lowercase L) this should tell you where it is located, I think you said sdb was your guess, but whatever it is it should look like /dev/sd#* where # is a letter and * is a number.

*IMPORTANT* Your sata hard drives are of type sd# so try fdisk -l before and after you plug it in to be sure. We aren't changing anything special, but there is no reason to mess with the mount stuff of your HD.

So next your going to mount it yourself.
In the Terminal navigate to /media (or replace /media with /mnt if you do not want it to show up on the desktop, it will instead be found under /mnt/wyw)
```
cd /media
```
Next create a mount point, this is just a directory called wyw (whatever you want)
```
sudo mkdir wyw
```
And then mount it by using the mount command, the syntax is
```
sudo mount -t vfat /dev/sd#* /media/wyw
```
Where -t is to specify the filesystem, and vfat is usually the type for usb sticks, /dev/sd#* is kind of like the physical point of reference (bad lingo I'm sorry) and /media/wyw is your mount point.
That should do it, but a word of advice is to ask someone else why it didn't automount, because if you mount it as above, you cannot unmount it via the GUI, it will tell you that since it was mounted via command line it must be unmounted the same way.
The command for that is much simplier.
```
sudo umount /media/wyw
```
notice that its umount not unmount.
Hope this works, sorry that I can't tell you why it wont automount.
If btw it doesn't mount, try
```
sudo blkid
```
it should let you know if the device is seen at all, of course this would also be observable if you do not see it in fdisk -l.
Hope this helps.

---

### Post by chunri on 2008-10-23
> **NeuB27 said:**
> I can tell you how to do it manually, but I don't know why it will not automount, unless its not formatted correctly.
You will need sudo access.
In the terminal use ```
fdisk -l
``` it might tell you that you should run it as sudo, and you can, it should change anything, just remember the -l (lowercase L) this should tell you where it is located, I think you said sdb was your guess, but whatever it is it should look like /dev/sd#* where # is a letter and * is a number.

*IMPORTANT* Your sata hard drives are of type sd# so try fdisk -l before and after you plug it in to be sure. We aren't changing anything special, but there is no reason to mess with the mount stuff of your HD.

So next your going to mount it yourself.
In the Terminal navigate to /media (or replace /media with /mnt if you do not want it to show up on the desktop, it will instead be found under /mnt/wyw)
```
cd /media
```
Next create a mount point, this is just a directory called wyw (whatever you want)
```
sudo mkdir wyw
```
And then mount it by using the mount command, the syntax is
```
sudo mount -t vfat /dev/sd#* /media/wyw
```
Where -t is to specify the filesystem, and vfat is usually the type for usb sticks, /dev/sd#* is kind of like the physical point of reference (bad lingo I'm sorry) and /media/wyw is your mount point.
That should do it, but a word of advice is to ask someone else why it didn't automount, because if you mount it as above, you cannot unmount it via the GUI, it will tell you that since it was mounted via command line it must be unmounted the same way.
The command for that is much simplier.
```
sudo umount /media/wyw
```
notice that its umount not unmount.
Hope this works, sorry that I can't tell you why it wont automount.
If btw it doesn't mount, try
```
sudo blkid
```
it should let you know if the device is seen at all, of course this would also be observable if you do not see it in fdisk -l.
Hope this helps.

thanks for your help,but i have to say that it doesn't work.my 4G usb flash stick can't be recognized by using code "fdisk -l".I don't what going to do? Help me!

---

### Post by NeuB27 on 2008-10-24
Did blkid show anything? Go ahead and post the output from blkid and fdisk -l before and after drive insertion.

---

