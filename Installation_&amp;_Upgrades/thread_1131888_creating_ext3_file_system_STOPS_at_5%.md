---
title: "creating ext3 file system STOPS at 5%"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by Colossos on 2009-04-21
Hi,

yesterday I tried installing Ubuntu 8.10 from the official CD I recieved through post. The installation stops at 5% when it says:

Formatting partitions:
"creating ext3 file system for/in partition...." 

I've waited for more than an hour before manually turning of power. I also tried the iso alternate 64bit version which i downloaded/burned and it gave the same problem. 
Apparently I'm not the first one with this problem when I browse the internet but there has never been given a solution to this problem.

I'm using the guided install using the full disk as I dont need anything on the HDD anymore. What is causing this and what can I try?

Specs:
HP Pavilion Media Center Desktop (2 years old)
AMD Athlon64
1GB RAM
2,6Mhz

My hard drive is 500GB SATA or something.

I can browse Ubuntu using the CD without installing but it doesnt connect to the Internet though. The PC has its own Wireless LAN and  Windows Vista automatically recognized the wireless network but Ubuntu apparantely not. How can I solve this problem?

I'd really appreciate any help as I'd really like to try Ubuntu but apparently its not as easy as alot of people are claiming.

Steven

---

### Post by Colossos on 2009-04-22
Ok,

now I left the PC running at 'Formatting Partion Creating ext3 file system in / for partition...' and it stayed at 5% for 2 hours and afterwards I got the message:

Failed to create ext3 file system in partition...

and I get sent back to the partition manager part of the installer.
Sigh. 

The strange thing is that when I use Gparted from the Live CD , I can create ext3 partitions. But when running the installer , it seems he formats the partition again and wants to create an ext3 file system again and the same error occurs. 

Is there anyway to make the installer skip this step as I can make the partitions (formatting and making ext3) in Gparted?
How do I exactly make the right partitions (I dont want to keep anything on my HDD , so everything can be erased).

Are there any other ways to install Ubuntu? 

The error occurs in 8.10 , the alternate iso 8.10 and the 9.04 version. 

Pls someone help me!

---

### Post by niqmk on 2009-04-22
have you erased all partition?

---

### Post by Colossos on 2009-04-22
I dont think so because there seem to be 2 really small partitions locked up (i'm not allowed to delete them - there is this picture of a key next to them in gparted).
How can I delete all partitions completely? Is it possible using a command in the terminal for this?

Also keep in mind that i used the 'guided use complete disk' for install already which gives the same error. I think this install deletes all partitions automatically first so dont know if this is the cause of the error.

---

### Post by niqmk on 2009-04-22
unmount it first then erase

---

### Post by Colossos on 2009-04-22
How do I do that? I am completely new to Linux and dont know anything actually. 

Thx for the help, really appreciate it.

---

### Post by niqmk on 2009-04-22
just right click to your media partition then unmount. then the locked criteria will show up

---

### Post by unutbu on 2009-04-22
The error you are experiencing is probably related to the undeletable partitions.
Since you have nothing on the drive that you wish to keep, let's wipe your partition table clean. Then I believe the installation should be able to proceed.

Boot from the LiveCD.
Open a terminal (Applications>Accessories>Terminal)
Type
```

sudo umount /dev/sda
sudo dd if=/dev/zero of=/dev/sda bs=512 count=1
```

Then try installing.

---

### Post by Colossos on 2009-04-22
Ok , i'll try that this evening. After I erased all partitions, I will retry to install. Dont really understand how this can cause a problem though. I guess i have to type in the two codes seperately , right? So type

sudo umount /dev/sda

than press enter 

sudo dd if=/dev/zero of=/dev/sda bs=512 count=1 

than press enter again

sry, i'm willing to learn all this stuff but it's seems all very complicated

---

### Post by unutbu on 2009-04-22
Yes, you have it right. Type the two commands separately.

Sorry your introduction to Ubuntu has started out rather rough.
Usually it isn't like this. 

I'm not 100% certain, but here is my guess as to what's happening:

Not all partition editors are compatible.
Your partition table might be readable as far as Windows is concerned, but it might contain what GParted and the Ubuntu installer consider errors. If that is so, you could have the problem you are experiencing.

---

### Post by Colossos on 2009-04-22
Hey,
I will first try the above suggestions but apparently i'm not the only one having this problem. I browsed other threads and someone posted a possible solution I would like to try. Here it is:
----------------------------------------------
Open up a terminal in the Live-CD environment.

sudo nano /lib/partman/commit.d/30parted

Edit the file to look like this (only diffrence is that update-dev is added):


#!/bin/sh

. /lib/partman/definitions.sh

disable_swap
for dev in $DEVICES/*; do
[ -d "$dev" ] || continue
cd $dev
open_dialog COMMIT
close_dialog
update-dev
done

Then start the installation.
---------------------------------------------------

My question is: How do I save these changes in the terminal? Or dont I have to save them? I can see in the top right corner of the terminal 'modified' when i type something but whats next? Do I just close the window? If I close and reopen the file, nothing changed.
When i use gedit <filename> it doesnt allow me to save (probalby because I'm running from the Live CD)

---

### Post by unutbu on 2009-04-22
If you run "sudo nano", then you save by typing Ctrl-x.
If you type "gksu gedit", then you save by clicking the save button.

You should use gksu to run graphical programs with root privileges.
You should use sudo to run command-line programs with root privileges.

Could you post the link to the other thread? I'd like to read it.

---

### Post by Colossos on 2009-04-22
Ofcourse , here is the thread 
[http://ubuntuforums.org/showthread.php?t=1031111&highlight=diffrence+update-dev+added](http://ubuntuforums.org/showthread.php?t=1031111&highlight=diffrence+update-dev+added)

.

So if I just press CTRL+X after using the sudo command it will save changes to the file? I'm wondering how this is possible if running from the live CD. Where is he writing the save?

I have a feeling it will be a long evening....

---

### Post by unutbu on 2009-04-22
Thanks for the link. 

When you boot the LiveCD, a filesystem is created in RAM. It's just like any other Ubuntu filesystem, except that it disappears when you shutdown. 

So Colin Watson's suggestion was to edit /lib/partman/commit.d/30parted in the LiveCD's filesystem. When you double-click the "Install" icon, I expect this file is read, and that is why editing it makes a difference.

Please keep us posted on how things go.

Edit: If you could, would you please post the output of 

```
sudo fdisk -l
sudo sfdisk -d
```
This will give us a picture of your current partition table.

---

### Post by Cybie257 on 2009-04-22
> **Colossos said:**
> 
The strange thing is that when I use Gparted from the Live CD , I can create ext3 partitions. But when running the installer , it seems he formats the partition again and wants to create an ext3 file system again and the same error occurs. 

Is there anyway to make the installer skip this step as I can make the partitions (formatting and making ext3) in Gparted?
How do I exactly make the right partitions (I dont want to keep anything on my HDD , so everything can be erased).

Are there any other ways to install Ubuntu? 

The error occurs in 8.10 , the alternate iso 8.10 and the 9.04 version. 

Pls someone help me!

When you run the installer, select manual partitioning, which you will find at the bottom of the screen that you are hitting ok for 'use entire disk', or whatever the exact words are. When you get to the next screen (After you have created the partitions the way you said it worked with Gparted/Live), be sure that one partition is "/", and at least one other is SWAP. Typically, 3GB is more than enough for SWAP and what usually is close to default. If those both exist, UNCHECK the "Format Partition" box and continue. That will allow the install to continue without trying re-format the drive/partition. 

These are the only two partitions that are required for an install. All the others are for advanced needs. 

Give that a shot if the other suggestions don't manage to work. Also, be sure that your drive isn't bad. Linux is a little better at not wanting to allow you to install on a bad drive, while Windows tends to do so, which usually can result in the infamous Blue Screen Of Death. The bad part is, is that it doesn't always tell you it's bad and just sits there.:(

-Cybie

---

### Post by Colossos on 2009-04-22
hey me again,

I just had a question when i was reading some forums:

/dev/hda and /dev/hdb from the can be replaced with /dev/sda or /dev/sdb or any partition or hard drive you may have on your system

in the commands ubutnu posted that i will try this evening:

sudo umount /dev/sda
sudo dd if=/dev/zero of=/dev/sda bs=512 count=1

he uses 'sda'  . whats the difference with hda? does it make any difference wether i should use sda or hda when giving the commands?

---

### Post by unutbu on 2009-04-22
Modern Linux distributions use "libata" to control hard drives.
When using libata, all hard drives are given device names of the form /dev/sdX,
never /dev/hdX. Since you are installing a current version of Ubuntu, you can be confident your drives will be called /dev/sdX. If you have only one drive, then you can be confident it will be called /dev/sda.

By the way, just so you know what the command is doing:```


sudo dd if=/dev/zero of=/dev/sda bs=512 count=1
```

writes zeros on the first 512 bytes of the hard drive. These bytes usually contain the drive's Master Boot Record (MBR) -- used for booting operating systems -- and its partition table. It doesn't affect anything else about the drive. By wiping it out, it should trick the Ubuntu installer into thinking the drive is blank.

---

### Post by Colossos on 2009-04-22
Ok ,thx for the explanation. And indeed my drive was called /dev/sda. I'm saying "was" because I just issued the given commands and afterwards I checked with Gparted if there was anything on the drive. I didnt see anything except a big grey block and underneath that one thing: unallocated space 470GB.
So I suppose everything is gone now. I'm currently trying to install ubuntu now but it still stays long at the 5% partition formatting; creating ext3 file system for / in partition SDCS (...)

I cant imagine this is supposed to take this long unless its normal if he formats and changes the file system for a 500GB hard drive. I'll let it run anyway. If it gives the same error again, I'll try partioning in Gparted and already giving the ext3 file system (it works in gparted) there. Hopefully the partition manager in the install allows me not to do this stuff again during the install. We'll see.....

---

### Post by unutbu on 2009-04-22
If you can partition the drive using GParted before you install, then during the install, when you get to "Step 4: Partitioning"
select Manual partitioning (rather than Guided). 

You can then select the partition you wish to use for root /, and which you wish to use for /home, and which to use for /swap.

This is basically what Cybie257 already recommended. I think it is a good idea.

---

### Post by Colossos on 2009-04-22
Hey,

ok 1 problem is down: I used Gparted to make an ext3 partition after issuing ubutnu given commands (thx) and the installer continued... UNTIL

it sais copying files 24% and than it sais 

"read/only error
probalby due to bad disc, overheating, bla bla bla "

SIGH and the installer stops.
I was using the disc I burned myself so now I'm going to try the offical Ubuntu 8.10 disc I recieved but I'll leave my pc cool down for awhile (desktop). Maybe its a bad disc but I have a hunge that this will not be the case and this is a problem of different nature.

Getting frustrated here. 

Pls guys, dont make me go back to those guys in the shop and let them reinstall vista.

---

### Post by Colossos on 2009-04-23
Ok so the problem of 
'failed to create ext3 file system on partition...' is solved and I thank you all for all the help. **BUT** 

now the installer stops during installation: Errno5 and some useless explanation that this might be due to bad disk etcetera...

I tried it again with the iso alternate8.10 I downloaded and burned. Now it really got far in the installation:
Partitioning ok
Base package installed
Password users . ok
Select and install software: FAILED and they dont say why but I'll bet its the same problem as with the official live CD.

Damn it , it was looking so good and was almost at the end. The only thing I can think of that might have caused the fail is that I didnt make a swap partition. I didnt do that because I just wanted to see if the damn software would install. 

Sigh. I'm gonna try OpenSuse 11.1 this evening and if that also doesnt want to install properly , its back to Windows for me. Nothing is worth all this trouble and time.

---

### Post by s1c on 2010-10-21
> **unutbu said:**
> The error you are experiencing is probably related to the undeletable partitions.
Since you have nothing on the drive that you wish to keep, let's wipe your partition table clean. Then I believe the installation should be able to proceed.

Boot from the LiveCD.
Open a terminal (Applications>Accessories>Terminal)
Type
```

sudo umount /dev/sda
sudo dd if=/dev/zero of=/dev/sda bs=512 count=1
```Then try installing.

well hello everyone... 


i was stupid enough to do the second command before i read what it is actually doing

would like to know if there is anyway of recovering some partition from sda... or it is completely lost for all eternity?

---

### Post by s1c on 2010-10-23
well, i had the same issue
(only it occured with ext4 file system also...)

the install stopped at 5% (when trying to create the ext3/ext4 file systems)

tried few things and then i finally decided to try install ubuntu on my second newer drive...

guess what.. it created the partition without any problems.. and the install finally completed..

So i guess it was my older disk drive that either had few bad sectors.. or it couldnt for some weird reason support the ext file systems...

So maybe that was the case for you too... dunno.. just maybe

---

