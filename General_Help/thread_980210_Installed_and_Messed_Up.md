---
title: "Installed and Messed Up"
date: 2008-11-12
forum: General Help
---

### Post by camper365 on 2008-11-12
I have an 8 year old Inspiron 2500 that my Grandmother gave me a few months ago. Let me get started by saying it has a 5 GB hard drive, so there isn't any free space at all. So I got a 120 GB external hard drive and tried to install Ubuntu on that. So, after a few months of playing around with anything Linux related, I got it installed. The only problem is, when I hit reboot, it tells me Grub Loading Stage 1.5

Grub Loading
Error 21.

I will try to look more into this, but I am unable to boot any operating system that is not on a CD. I have decided I do not want to put Ubuntu on my laptop if it means I can't have any Operating system, and I want to be able to boot Windows. Maybe when I get a new laptop I will try to install Ubuntu

---

### Post by john183 on 2008-11-12
quick fix, upgrade the HD in the computer. even if just to a 60 gig. if you can send me the info from your post in a PM (so i don't have to search fot this post should it get buried) i will do some research and see exactly what upgrades your computer can handle and may be able to give you some pointers as to the best ways to get your system up and running.

---

### Post by caljohnsmith on 2008-11-12
If you can change the BIOS boot order so that the external drive boots first on start up, that is ideal, because then you can keep your two drives independent of each other. If you can only boot your 5 GB internal drive, you could install Grub to its MBR (Master Boot Record) and still get things working just fine, but if anything happens to either drive, you most likely won't be able to at all. 

How about booting your Live CD, open a terminal (applications > accessories > terminal) and do:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd1,0), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
That will install Grub to the MBR of your external drive so you can boot it directly on start up, provided you set your BIOS to boot it on start up. If you can't set your BIOS to boot the external drive, then you can do the following to install Grub to the MBR of your internal drive:
```
sudo grub
grub> root (hdX,Y)
grub> setup (hd0)
grub> quit
```
And please post the output of all the above commands. If you run into any problems, please also post:
```
sudo fdisk -lu
```
And we can work from there if you want. :)

---

