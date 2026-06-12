---
title: "External Drive"
date: 2008-08-21
forum: General Help
---

### Post by starving030 on 2008-08-21
I use an old laptop hdd as kind of a giant thumb drive. But when i try to connect it via USB I get this error. I tried doing what it said but it makes no sense to me. Advice?

[[IMG]http://host.photogalaxy.net/thumbs/5114_Screenshot.png[/IMG]](http://host.photogalaxy.net/viewer.php?id=5114_Screenshot.png)

Running Ubuntu 8.04

---

### Post by forger on 2008-08-21
1) Did you right click on the icon of the hard drive and unmount the external hard drive properly or did you just pull the plug?
2) The last time you used it, was it in Windows or Ubuntu?

I suggest to connect it from Windows and do a checkdisk from there

---

### Post by Titan8990 on 2008-08-21
You need to run a NTFS filesystem checker on that drive such as mschkdsk. Unmountable boot volume errors can easily lead to the data loss of the entire drive.

---

### Post by starving030 on 2008-08-21
I got it to work but I hope there is a easier way to do it.

It seems Ubuntu is more sensitive than XP. I had to actually but it back into a laptop, reboot, and shut down to get it to work.

---

### Post by Titan8990 on 2008-08-21
"sensitive"? And you don't think that this has anything to do with the fact that the Windows OS you loaded it back on is the thing that had it locked?

---

### Post by SuperSonic4 on 2008-08-21
I pick option 2: has never failed for me so far

---

### Post by ajgreeny on 2008-08-21
Don't forget, you MUST "remove safely" any usb drives. flash or hard drive, when you use them in windows, not simply pull them out as most people do.  That can cause not only the problem you have seen but could also lead to corrupted data if something is still being written to the drive when pulled.

---

### Post by forger on 2008-08-21
There is an easier way:
1) a) Format it to ext3 using gparted (Gnome partition editor) system > administration > partition editor (it's in the repositories)
b) Use fs-driver: [http://www.fs-driver.org/](http://www.fs-driver.org/)

or

2) Format it to FAT32, both operating systems will be happy :)

---

### Post by starving030 on 2008-08-21
Yeah, the last time it was used was in windows as a hdd on a laptop. I did get it to work tho. Just need to figure out how to unpack a .ace file. I'm trying to run World of Warcraft. So far it just says reading archive when I try to unpack it.

---

### Post by forger on 2008-08-22
do you have unace installed?
```
sudo apt-get install unace
```

---

### Post by Terry19 on 2008-08-22
I had the exact same problem, And i asked someone. 
It seems that windows when it mounts an external drive it places a small hidden file that only windows can read, it tells the computer the device is there and not to allow anything but windows to access it. When you safely remove the device windows removes that file and turns the devise off. Unfortunately Ubuntu doesn't like this small hidden file and refuses to mount it. I solved the problem by re attaching the external hard drive to a windows computer and safely removing it. There is a much more technical way to say all that so i kept it simple. remember i got this from an unreliable source so it may be wrong. You would think that the coders of ubuntu would fix this problem because its highly annoying.

---

