---
title: "Other Hard drives"
date: 2005-04-30
forum: Hardware &amp; Laptops
---

### Post by master of all on 2005-04-30
(Just keep in mind I've just got Ubuntu this very hour and have joined these forums in the same space of time, so apologies if I do/say something stupid.)

On ubuntu, what I want to do is be able to access my other HD partitions(I have 1 85gig HD in 3 partitions, C-windows, E- backup of windows on C and my linux partition) but Ihave no idea how to find them on Ubuntu. (I've looked on google and other places and there's too much to dig through.) Any help is appreciated.

---

### Post by fordfan753 on 2005-04-30
You will need to modify your /etc/fstab file.
But first you must know the names of the drives, they will be something like /dev/hda1, or /dev/hda2, etc

---

### Post by fordfan753 on 2005-04-30
In a terminal type
$ sudo fdisk -l [disk]

eg. $ sudo fdisk -l /dev/hda
this will help you decide if you've found the disk you were looking for

---

### Post by fordfan753 on 2005-04-30
If possible can you paste the results to $ sudo fdisk -l /dev/hda    ?

---

### Post by master of all on 2005-04-30
[QUOTE=fordfan753]You will need to modify your /etc/fstab file.
But first you must know the names of the drives, they will be something like /dev/hda1, or /dev/hda2, etc[/QUOTE]

I know which HD I want, HDA1, so what do I do to the fstab file?

---

### Post by neville_lobo on 2005-05-01
Hi,

Go to [http://www.ubuntuguide.org](http://www.ubuntuguide.org) 

It has a section about mounting drives. Very useful guide for a new user. Hope you enjoy ubuntu.

Neville

---

### Post by fordfan753 on 2005-05-01
[QUOTE=master of all]I know which HD I want, HDA1, so what do I do to the fstab file?[/QUOTE]

Add a new line in /etc/fstab that looks something like

/dev/hda1           /media/windows             file system type        umount=000      0        0

file system type will be vfat or ntfs with windows.
umount=000 will give you unrestricted access, if you're mounting an NTFS partition this may not be a good thing, umount=002 may be better, and the two 0's just have to be there

---

### Post by fordfan753 on 2005-05-01
Make sure you put tabs between the seperate bits...or you will kill stuff.

---

