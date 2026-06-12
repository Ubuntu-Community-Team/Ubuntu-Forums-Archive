---
title: "Installation alongside Windows XP (no Wubi)"
date: 2009-09-24
forum: Installation &amp; Upgrades
---

### Post by rckShow on 2009-09-24
Hello,


I wanted to install Ubuntu in my PC that has already a Windows operating system 
- The installation doesn t recognize any operating system.
- I had already prepared a partition, but I didn t knew that the installation of ubuntu did it itself. In the partition table i just selected the prepared partition to be formatted.

I don t know what is going to happen to the other partition and to the other disk that i have that contains 400GB of data. I don t have ways to make any backup.

would someone please tell me how the advanced partitioner at the installation work .Am i going to loose the data?

I am really blocked, i really see Ubuntu as a new beginning 
please help

thx

---

### Post by bruno9779 on 2009-09-24
First : You won't lose any data. You had already prepared the space for ubuntu, so ubuntu will not mess with the other partitions.

You should read through this:

_[Dual Boot]("https://help.ubuntu.com/community/WindowsDualBoot")_

It is very complete, you shouldn't need anything else.

Still, write on the forums if you encounter any issue.

Welcome to Ubuntu!!!

---

### Post by rckShow on 2009-09-24
I deeply appreciate your concern,  bruno9779. :)
I had already read the section that you suggested but It did n answered my question. that s why i referred to the forum
Do you know, any docs about the manual partitioner in the installation?
or else i will try it anyway , no guts no glory lol

thx

---

### Post by bruno9779 on 2009-09-24
the thing with repartitioning a windows partition is:

a) of course make sure you have the free space for the new partition.

b) defrag and scandisk in windows.

so, when all your win files are together and the disk is scanned for errors there isn't much that can go wrong.

For peace of mind you could use a Windows partitioner like "partition magic" or the like (ask a win user) but I had 100% results with Gparted at that

---

### Post by rckShow on 2009-09-27
Well infact all the preliminary work was already done with partion magic from from hiren usb boot .

So I decided to install Jaunty jackalope, installation went fine, do data loss as you predicted. But once i enterred Windiws Xp and rebooted my PC , surprise surprise 
GRUB ERROR 22 !!  nothing can be done , can t boot to anything except CD . So I start a  live session from the installation CD And start trying to find out what the problem was , I Thaught maybe this will be a GRUB configuration problem. So I try tu fix it . It worked once, then my windows Xp partition goes unrecognize , every time I try to boot my on Win XP  it automatically gets restarted . I can t even boot via USB .  Then I run fdisk -l and the partition is shown as if there is no operating system on it.  

This is really anoying me, maybe you can give a hand  with this too .
Is there a way to uninstall Ubuntu :confused:  

I will try making another post

Thanks for all your help

---

