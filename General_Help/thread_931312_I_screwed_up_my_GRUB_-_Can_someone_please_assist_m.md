---
title: "I screwed up my GRUB - Can someone please assist me."
date: 2008-09-27
forum: General Help
---

### Post by Disgruntled on 2008-09-27
Hey, I am not sure whether this is the correct thread for my particular problem, but you'll have to forgive me if it isn't.

I am having an issue with my GRUB loader, when I start my pc it gives me an error and doesn't let me go into XP or Ubuntu.

The following happened prior to my error; I had installed Ubuntu a few months ago using one of those handy Live CD's (I am currently on it aswell, cause I cant get on to windows/ubuntu) After installing Ubuntu however, I never used it(Basically I intended to use it only when windows would crash so I could go on internet, it used to crash a lot before I installed ubuntu. Ironically, however, windows didn't crash after I had installed Ubuntu - for months now, which is a personal record -. I got a 80 gb hard drive, and when I installed Ubuntu I gave it half, so 40 gb. During these months I clogged up my windows partition and found myself left with only 3 gb of free space. So I decided (stupidly) that I could probably just format the partition that had Ubuntu on it, and then re-install Ubuntu, but this time with only 10 gb allocated to it. 

Well, it didn't work out that well. When I was looking in to how to format the Ubuntu partition. I ignored the part where you had to use a windows recovery CD to use the fixmbr command (or something) to get windows to load directly instead of through GRUB. (I dont have a windows CD). I didn't think it would be an issue, but it is. I've been googlin a bit and reading the forum, I came across a particular topic that somewhat addresses my problem, but all the solutions offered do not work for me. (I think at least, I am not that computer savvy) 

This is the thread: [http://ubuntuforums.org/showthread.php?t=740221](http://ubuntuforums.org/showthread.php?t=740221)

If anyone out there knows how to restore my GRUB through the LIVE CD(or remove it entirely so I can get back to my windows XP and re-install Ubuntu from there) I would appreciate it a lot!


Just in case anyone tries to offer me the same solution as the ones in the thread I posted. The ubuntu terminal cannot find my stage1 file, which is necessary to use the solution provided by the thread poster, probably cause I formatted the entire partition. (this is just me guessing, not stating anything)

PLEASE, PLEASE, PLEASE help me out. I can follow directions, but they have to be given in baby steps so that I don't screw up again. 

Thanks a lot to whomever replies.

---

### Post by Disgruntled on 2008-09-27
Bump

Any ubuntu whizzkid out there? -_-

---

### Post by reality1011 on 2008-09-27
Try using super grub disk... I have messed up my grub/MBR NUMEROUS times.  at the very least you will be able to boot again.

---

### Post by reality1011 on 2008-09-27
fyi : 

[http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5)

---

### Post by Disgruntled on 2008-09-27
Yeah I came across Super Grub Disk too, but I am not sure whether I can use it. I only have one working optical drive DVD-RW, which I am currently using for the Live CD. And to my understanding I am supposed to burn the Super Grub Disk to a CD and then boot it from there? But I cant burn anything, cause I already got ubuntu Live CD in it. In case I am missing anything, please point it out. 

Also, I don't have floppys (does anyone?) so can't use that to boot Super Grub Disk either :(

---

### Post by reality1011 on 2008-09-27
Interesting.. what about USB?

---

### Post by Disgruntled on 2008-09-27
I don't have any usb sticks, and no mp3 players either. I listen to all my music through my phone...

Would my phone work too?

I guess I could put Super Grub Disk in the memory card of my phone through a USB cable. But I am somewhat skeptical about whether BIOS would let me boot Super Grub Disk through my phone? Perhaps skeptical isn't the correct term, I think it's more like impossible? Considering, I have loads of songs on my phone card too. Surely it isnt possible for my computer to fetch Super Grub Disk out of my memory card and boot it?

---

### Post by Disgruntled on 2008-09-27
Btw, thanks for replying. I really appreciate it!

---

### Post by plucky on 2008-09-27
Your options are:


1) Using the Partition Editor on the Live CD,create a 5GB ext3 and swap partition to install Ubuntu on.

2) expand your windows partition to take up the remaining space.

3) Reinstall Ubuntu on to the 5GB partition and hope that it picks up your windows install when it installs grub.

4)Boot windows to see if it works.

5)Download and burn Super Grub Disk.

6)Use Super Grub Disk to Fix your windows boot.

7)If windows boots without Grub,Use Live CD to delete your Ubuntu partition and expand your windows partition.

 **You now have only windows on your computer.**


**OR**

Borrow a windows CD from a friend and use it to FIXMBR for windows and use the Live CD to expand the windows partition to take up the whole disk.

Good Luck

---

### Post by gkestrel on 2008-09-27
Try this from a live cd to restore grub.

Boot from the live cd first when you get to the desktop, open up a terminal window and type

sudo grub

you should now see a grub prompt like below

grub>

now at the grub prompt type

find /boot/grub/stage1

and press enter

you will see it return a location, on my computer its (hd0,0) on yours it might be different depending on what hard drives you have.

make a note of what is returned so you dont forget.

Now whatever was returned for the find command you use in the next commands. Type

root (hd0,0)

then press enter

Now we need to enter the command to install grub to the mbr of the hard disk

setup (hd0)

then press enter

Finally to exit the grub shell type

quit

then press enter

That should be it. Grub should be reinstalled to your hard disk mbr and when you reboot you should have the grub menu again.

If you get any error messages then post back here so that someone can help you further.

---

### Post by caljohnsmith on 2008-09-27
If you don't have Ubuntu installed right now, the problem is that your Grub can't find the files it needs to load, which used to be on your Ubuntu partition. That is also why when you do the "find /boot/grub/stage1" command in the Grub CLI, it doesn't find anything. :) Is there some reason why you can't just reinstall Ubuntu at this point, or did I miss something? Assuming your install goes OK, that should fix Grub.

---

### Post by WWSmith36 on 2008-09-27
I see a couple of options

1)  Borrow someones Windows CD to do the fixmbr

2)  Boot with LiveCD, enable universe repository and install ms-sys and follow that method (FYI you can install packages even though you are on the LiveCD)

---

