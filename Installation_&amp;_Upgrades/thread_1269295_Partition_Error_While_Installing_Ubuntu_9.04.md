---
title: "Partition Error While Installing Ubuntu 9.04"
date: 2009-09-18
forum: Installation &amp; Upgrades
---

### Post by NoFriends on 2009-09-18
Hey Guys/Girls, New here :), thought i would say Hi, before i ask a question.

complete newbie to Linux/ Ubuntu, never used it before, but i want to get to play around with it a bit, got my free disc through yesterday, tried installing it onto my desktop, i can get through half of the setup until i get to step 4 of 7, which is Partitioning, i get a message saying  _***"NO ROOT FILE SYSTEM"***_ and i am unable to click on New Partition table and unable to click the other options given aswell, can anyone help me ? 

Also i do not have an operating system on there at all, so i am "NOT" Trying to partition it with windows, i just want to fully run Ubuntu :) if that makes sense ? :)

P.S you might have to reply in english instead of linux language until i start to pick things up. sorry to be a pain.

Thanks In Advance


NoFriends :)

---

### Post by tommcd on 2009-09-18
First, when you boot the Ubuntu CD, choose the option "check disc for defects". Let that run. If it passes then the disc is good. This will rule out a bad CD as the source of the problem.

Are there any partitions on the hard drive currently?
Which option are you choosing when you get to partitioning? For simplicity you could just choose the option to use the entire hard drive. This will erase the entire drive and create 2 partitions, one for root (/) and one for swap. See this guide to installing Ubuntu:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
If you want a separate home partition, which is ideal, see this section on manual partitioning:
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
For whatever option you choose you must have a partition designated for the root (/) file system. The forward slash (/) is the shorthand designation for the root partition mount point in linux.

---

### Post by NoFriends on 2009-09-18
Hi Tom, i Don't think there are any partitions on the drive atall, and i it grey's out the options to do anything when i click forward it just says NO ROOT FILE SYSTEM, the it has passed the check disks for defects. and when i do get to the Partition page, there is nothing in the list and all the options are greyed out, so i am guessing it could be the hard disk ?
what do you reccomend ?

Thanks Tom :)

---

### Post by tommcd on 2009-09-18
I don't know why all the options would be grayed out in the partition editor. While you are in the Ubuntu live CD open a terminal (applications > accessories > terminal) and run:
```
sudo fdisk -l
```
This will list the partitions on the drive, if any. Post back the output of that command. Ubuntu must be having trouble reading your drive.
While in the terminal you can run **gparted**. This will open up a graphical representation of the hard drive on your computer and allow you do delete any existing partitions. Then you can reformat the drive as ext3 file system. Then try again to install Ubuntu. If you need help using gparted see the documentation here:
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

If that fails, perhaps you can try using a Parted Magic or GParted live CD to partition the drive:
[http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
If you are using Windows now, you can use Iso Recorder or Infra Recorder to burn the iso image of GParted or Parted Magic to a CD:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Be sure to burn the CD at the slowest possible speed. Then boot with either GParted or Parted Magic and delete all the partitions on the drive. Then you can format the whole drive as ext3. Then boot up the Ubuntu live CD and try again.

---

### Post by NoFriends on 2009-09-18
Cheers Tom, you have been a great help, i am now running Ubuntu 9.04, time to play around :)

---

