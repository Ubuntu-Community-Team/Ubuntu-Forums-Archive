---
title: "Second hard drive"
date: 2006-06-29
forum: Hardware &amp; Laptops
---

### Post by DarkStarDeity on 2006-06-29
I've just put a second hard drive in my ubuntu box, I used cfdisk to remove the existing partitions and create a single new one (I set the boot flag since it complained about it if I didn't), then tried to use the disks-admin GUI tool from the System menu to format the new partition to wipe the data that had been on it. I selected "Extended 3" as the file system type and, not knowing any better, chose /boot as the access path. But when I rebooted the machine, the changes had not "taken". The single partition was there, but the disk still shows up as Extended 2 file system and inaccesable unless I enable it again and give it an access path. (Is this tool just a GUI interface to mounting a drive? I know the terms, but I've never done this myself before.)

So, how do I set it up so that it will mount automatically on startup? One thing I always hated about Windoze was the complete separation of drives into C:, D: etc. What I want here is just to add the drive to the pool of free space available to the system, or at least to the free space available to the /home directories for data. Is this possible, and if so, how do I do it? Or am I stuck with drive separation the same as in Windoze? Also, should I change the filesystem to ext3 like the root drive (and if so how do I do that), or is it OK to just leave it as ext2?

---

### Post by handy on 2006-06-30
Have you edited **/etc/fstab** so as to **mount** your partition?

If not, have a look in the online help that is installed on your computer, it describes how to do this very well.

After editing **fstab**, you must creat a directory in **/media/*** your prefered name?*

Then enter the following in the Terminal:

handy@BirdFish:~$ **sudo mount -a**

I have found that sometimes a reboot is required before I will see the desktop icon of the just mounted item...

With this method you can mount & unmount drives via the command prompt.  Which I find useful having removable IDE drives, they become hot swapable.

---

### Post by DarkStarDeity on 2006-06-30
Does the directory I create have to be under /media, or can it be anywhere on the system? If I must have the new drive as a seperate directory, I'd rather just have it somewhere under /, with a generic name like "data", and accessible by any user that needs some space for data. Also, is there any way to have it *not* put an icon on the desktop (I actually hate desktop icons, I always use menus or panel icons to launch programs)

---

### Post by handy on 2006-06-30
You have to make the directory in **/media/**

You don't keep anything in that directory, but it has to be made, it is part of the mount process for your partition.

You can call it **data**, or anything you want. 

You set permissions in **/etc/fstab**

I have never looked into the icon thing, I'm sure you can remove them/it.  Someone else can answer that one for you.

Please read about **fstab** in the online help, you will understand a great deal more, & be able to write the line that you need to mount your drive.

---

### Post by DarkStarDeity on 2006-06-30
Thanks. I couldn't find any documentation other than the man page for fstab, which wasn't that useful, but I muddled it out from bits and pieces of other posts here.  I didn't get an icon on the desktop. Where is the online help you are referring to, because I could only find oblique references to fstab in the System->Help->Online and System docs, and none of them terribly useful.

---

### Post by handy on 2006-07-01
[QUOTE=DarkStarDeity]Thanks. I couldn't find any documentation other than the man page for fstab, which wasn't that useful, but I muddled it out from bits and pieces of other posts here.  I didn't get an icon on the desktop. Where is the online help you are referring to, because I could only find oblique references to fstab in the System->Help->Online and System docs, and none of them terribly useful.[/QUOTE]

***System / Help / System Documentation / Ubuntu Desktop Guide / Configuring Your System / Partitions & Booting***

Is pretty succint! :KS

---

