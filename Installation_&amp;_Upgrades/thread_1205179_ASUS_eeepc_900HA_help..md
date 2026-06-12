---
title: "ASUS eeepc 900HA help."
date: 2009-07-05
forum: Installation &amp; Upgrades
---

### Post by physic.dude on 2009-07-05
[COLOR=black][FONT=Verdana]I have the ASUS 900HA eeePC w/ windows XP and I noticed that my 160 GB HHD was divided into a 80Gb "C" drive with windows on it and an empty 80GB "D" drive. Does this mean I can install Ubuntu on the empty "D" drive simply be selecting it on the installation from the USB drive? If so, how do I select witch OS I want to use on boot up.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I&#8217;ve known Ubuntu for a while now, but I am a total N00B at duel booting. [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]In advance thanks.[/FONT][/COLOR]

---

### Post by running_rabbit07 on 2009-07-05
> **physic.dude said:**
> [COLOR=black][FONT=Verdana]I have the ASUS 900HA eeePC w/ windows XP and I noticed that my 160 GB HHD was divided into a 80Gb "C" drive with windows on it and an empty 80GB "D" drive. Does this mean I can install Ubuntu on the empty "D" drive simply be selecting it on the installation from the USB drive? If so, how do I select witch OS I want to use on boot up.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I&#8217;ve known Ubuntu for a while now, but I am a total N00B at duel booting. [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]In advance thanks.[/FONT][/COLOR]

Yes you can use that empty "d" drive. When you start booting the Ubuntu CD it will take you through all the steps to set up a happy system. When you get to the part for setting up how you want to load the OS on your hard drive it will give you multiple options. read them closely and choose whichever one that will allow you to install on your "d" drive. Keep in mind it may not show it as being labeled "d" drive but it will show that it is unallocated or empty.

As far as the selecting which OS to boot, the installer will load a program call GRUB which is a boot loader program. When you turn on your system after the install your system will do it's normal POST test which normally occurs while the PC is showing it's brand name ie Dell, HP, Lenovo. After that test you will get a menu that will allow you to select between your current OS and Ubuntu. Just click the one you want and it will load.

---

### Post by physic.dude on 2009-07-05
[COLOR=black][FONT=Verdana]actually the "D" drive is about 65GB, (160 GB HHD) could this mean that it holds some invisible system files that I can&#8217;t see (even when showing hidden files) and if I format it could it mess up the whole thing? I know that on usb drives, a small amount of storage is used for formatting stuff. [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]--- see attached picture ---[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]sda1 - main "C" [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]sda2 - empty "D"[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]sda3 - USB Drive[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]sda4 - IDK?[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]do i need to check it for formatting too?[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Verdana]Ps. sorry for the bad picture.[/FONT][/COLOR]

---

### Post by running_rabbit07 on 2009-07-06
The best way to find out if you have hidden folders is to go into MSDOS or Command Prompt from within Windows and aid the command line to that drive by entering "CD D" enter "DIR /A" .This will show you all the directory trees(folders) and files even if they are hidden and their attributes.

Your screen shot shows that there is about 3 gigs of files there, so you definately need to find out what they are.

If you create a folder within the partition you use (C) you can then copy all the files from the D drive by aiming the Command line at the drive again and then using the COPY command, you can copy those files you found to that folder. To learn how to use the COPY command you can search google and/or enter COPY /?. ***Always take care to know what you are doing in command line. You can accidently delete files and not be able to recover them.***

You need to find out if the files on your D drive are back-up files before moving them.If you can back up your PC to disks, you will not have to worry about having a back-up partition. If they are back-up files and you can't back up to disk, you may want to create another partition to run Ubuntu or worse comes to worse you can load Ubuntu via Wubi.

---

### Post by physic.dude on 2009-07-12
Ok, I went on CMD and dir'ed the "D" drive. it came up with 2 files,
 
1. RECYCLER
2. System volume Information
 
see the attached picture**
 
I dir'ed the "C" drive and it too had the same 2 files

---

### Post by physic.dude on 2009-07-12
[COLOR=black][FONT=Verdana]Do I need to make yet another partition for a "swap space" as some other website sais.[/FONT][/COLOR]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]

---

### Post by geekity2 on 2009-07-13
> **physic.dude said:**
> [COLOR=black][FONT=Verdana]Do I need to make yet another partition for a "swap space" as some other website sais.[/FONT][/COLOR]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]

That depends on whether you choose manual partitioner or automatic. If you are using automatic (guided) partitioner during the ubuntu install, you don't have to worry about it, the swap is made automatically. If you use manual partitioner, you need to make a swap yourself. It should be about 2 times your RAM.

So if you use manual partitioning, first select the partition you want to install on (if it's not marked as free space already), and choose to delete the partition (if format check box isn't ticked on that partition, tick it). Then chose the free space and pick make new partition. In the dialog box that pops up, set the size of the partition at twice your RAM, the radio button at primary (that's what I always pick anyway) and the scroll down menu of type of partition as swap. 

Then make a root partition with the rest of free space, by doing the same thing as for swap, except just using the size given automatically (it's the rest of the available free space), setting type to ext3 or ext4 and setting mount point at "/". 

Hope that helps...

---

### Post by physic.dude on 2009-07-13
thanks geekity, but i had to select "logicial" when making the swap space.
 
it seems to be working..
 
lets hope it doesent scrue up my computer...
 
:-({|= :-({|= :-({|=

---

### Post by physic.dude on 2009-07-13
OMG it works!!!
both Windows and Ubuntu, no errors 
 
Thanks Guys
 
\\:D/\\:D/\\:D/\\:D/

---

### Post by physic.dude on 2009-07-27
there is one problem...
 
[http://ubuntuforums.org/showthread.php?t=1218632](http://ubuntuforums.org/showthread.php?t=1218632)

---

