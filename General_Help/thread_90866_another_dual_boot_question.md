---
title: "another dual boot question"
date: 2005-11-16
forum: General Help
---

### Post by cobelloy on 2005-11-16
hi there all, I am loathe to admit I am trying to get windows aswell as ubuntu on my computer. But - here's what I have, Ubuntu on the primary master (with the kubuntu packages - I like KDE) and another disk installed as the secondary master (listed as /dev/hdc1) with windows xp on it. is there any way to get grub to see the windows disk at startup so I can choose which OS to boot. A while back I had mandrake/lilo and all I did was put the windows HDD in the case and switch on and lilo saw it and offered it as a boot option (windows 98 though).  Is this at all do-able?

---

### Post by aysiu on 2005-11-16
Theoretically, Grub should see the XP partition (it did for mine). You can try [reinstalling Grub](http://ubuntuforums.org/showthread.php?t=24113).

---

### Post by cobelloy on 2005-11-17
Hi there, grub didn't automatically see the new disk, but it is completely visible/accessible from within ubuntu. I looked at the instructions for reinstalling grub, but neither method worked, with the live disk method I entered the command "grub" like it said and got a reply that it was an unknown command. with the other method, the partitioner would not continue if I did not format a partition. So I am stuck again. Thanks for the reply tho xx

---

### Post by cobelloy on 2005-11-18
OK, so I went back to the link and read the instructions *properly* and I reinstalled grub - it sees winXP and offers it as a boot option, but it doesn't boot it stops just after it starts. could this have anything to do with the format type - I formatted the win drive as fat32 not ntsc, so it would be easy to find from ubuntu.

---

### Post by cobelloy on 2005-11-18
oops - i mean ntfs not ntsc (ha ha ha silly me...)

---

### Post by al7kz on 2005-11-20
Windows needs to "think" it is on the first hard drive (hd0 to grub). Google grub manual to find out about a workaround in grub for this. In brief, if windows is on the second hard drive (hd1 to grub):

#sudo gedit /boot/grub/menu.lst

title windows
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
savedefault
chainloader +1
boot

Let me know if this works or not. Cheers mate, Joe

---

### Post by al7kz on 2005-11-21
grub designates drives as hd0, hd1, hd2 etc where hd0 is the first drive, hd1 is the second drive, etc. Find out which drive XP is on by running grub:

$ sudo grub

grub> root (

(hit Tab key)

you will get output similar to:
grub> root (hd
 Possible disks are:  hd0 hd1 hd2

Run fdisk -l to find out which drive XP is on:

$ sudo fdisk -l

So once you determine that XP is on, say, hd1, then revise the windows entry in  menu.lst:

$ sudo gedit /boot/grub/menu.lst

title Windows
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive 
savedefault
chainloader +1
boot

if windows was on hd2, then substitute hd2 for hd1 in the above menu.lst entry

---

### Post by tOpEzz on 2005-11-22
i also running on dual boot (ubuntu + winXp), before install ubuntu i use partition magic to create partition for ubuntu(create /swap & /ext2) then after finishing create those partition i restart my pc and insert the ubuntu cd. installing like normal... when finish i can select the boot option between ubuntu and winXp.. walla luckly i dont found any problem during the installation.

---

