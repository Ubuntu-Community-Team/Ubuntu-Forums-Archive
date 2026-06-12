---
title: "VirtualBox problems... FATAL no bootable medium found!"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by drakoumel on 2009-05-14
hello i am trying to actually make virtualbox to work.. but no luck.
Lets take a look at my steps..
1)i open VB
2)click New
3)type the name "blabla" and choose the OS XP click next
4)i choose the memory capacity to use 
5)choose a virtual hardDisk (NewhardDisk1.vdi (home/raven.. ) click next 
6)i finish and go see my settings
7) on the settings i enable my pionner DVD so it can boot the windows XP installation CD 
8) then i click ok and start the virtual machine..
after it loads i get FATAL no bootable medium found !System Halted
( i pressed F12 and pressed 3 CD to boot from it )
whats the problem?

---

### Post by stanley82 on 2009-07-01
I have the same situation.  I can read the cd in linux.  Regards Ian

---

### Post by ronaldprettyman on 2009-07-01
> **drakoumel said:**
> hello i am trying to actually make virtualbox to work.. but no luck.
Lets take a look at my steps..
1)i open VB
2)click New
3)type the name "blabla" and choose the OS XP click next
4)i choose the memory capacity to use 
5)choose a virtual hardDisk (NewhardDisk1.vdi (home/raven.. ) click next 
6)i finish and go see my settings
7) on the settings i enable my pionner DVD so it can boot the windows XP installation CD 
8) then i click ok and start the virtual machine..
after it loads i get FATAL no bootable medium found !System Halted
( i pressed F12 and pressed 3 CD to boot from it )
whats the problem?
Click in side the box
hold rightCTRL+r to restart
when the blue screen for sun comes up, wait for it to disappear then start hitting enter
press right ctrl again to get your cursor back and wait for the installation to begin
You have to press a key to boot to the XP cd

Also are you using an iso of XP or an actual xp disc
does the disc work
is it mounted in linux

open a terminal and check
```
ls /media/cdrom
df -h
```
did ls show any files, did df -h show that the cdrom is mount
```
mount /media/cdrom
```
does it say mounted readonly or already mounted
restart the virtualbox and make sure you have the host cdrom mounted, Devices>Mount CD/DVD>Host
If its an image, make sure to have it mounted on boot

Also theirs a new version of Virtualbox out, vistit [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)
for details on it and how to add it to your repository, your want to have it in your repository because if you manually install it, your have to do so again with each kernel update.

---

