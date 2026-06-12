---
title: "How do I install ubuntu into free space?"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by PieLover on 2009-01-31
I recently decided I was going to download and install ubuntu on my desktop computer. I have downloaded and burnt the disk and started the installation. When I got the the "Prepare Partitions" section of the installation I chose the first option and gave 20% of my 120GB hard drive to ubuntu. When it got to the point where I had to input my details I ralised that my keyboard was not working so I quit to see if i could get around this. Unfortunately this was after it put Windows (which I intended to preserve) into a partition so now I have 24GB of unusable hard drive. I have fixed the keyboard problem but I don't know how I can tell ubuntu to install itself onto the free space. Can anybody help me please?

---

### Post by labinnsw on 2009-01-31
Restart the installation process. This time use manual partitioning and select the free space.

---

### Post by 73ckn797 on 2009-01-31
Boot up with the LiveCD and go to System/Administration/Partition Editor.

There you should be able to see the unused space. Make note of what it is designated as (ie...sda1 or whatever). Select the desktop icon to install. When you get to the choices of where to install to, select manual and select the free space partition.

---

### Post by PieLover on 2009-01-31
When I checked the free space designation in the partition manager it said undesignated and when I try and use it the installer comes up with an error syaing "no root file system is defined"

---

### Post by labinnsw on 2009-01-31
You need to designate the free space as root by using "/"

---

### Post by PieLover on 2009-01-31
How do you mean "use /"? (i'm a total novice at linux)

---

### Post by labinnsw on 2009-01-31
When you select the free space, the drop down menu, beside it I think, is the space for the designation. "swap", some other options and "/". Use "/" this makes it the root partition. Just leave out the open and closed quotation marks.

---

### Post by PieLover on 2009-01-31
I've chosen that under the "mount point" dropdown menu now but I also have another drop down menu called "Use as". The options I have for that are:

Ext3 journaling file system
Ext2 file system
ReiserFS journaling file system
JFS journaling file system
XFS journaling file system
FAT16 file system
FAT32 file system
swap area
do not use the partition

Which one do I need to choose? the top one was already selected when I loaded up the window.

---

### Post by labinnsw on 2009-01-31
Use ext 3 but there should also be a window for you to type "/"

Ok now I remember. The mount point is where you type the "/"

---

### Post by PieLover on 2009-01-31
There was a dropdown menu for me to select "/" so I have chosen that. I have clicked forward and it is prompting me about there not being a swap space partition. what should I do now? It allows me to continue or go back.

---

### Post by labinnsw on 2009-01-31
Yes that should be correct. You also need to make a small swap partition. It is OK to use the smallest possible space which, to the best of my memory is about 7mb.

You may need to go back to do this.

---

### Post by 73ckn797 on 2009-01-31
Make the swap at least the same as the physical RAM. They recommend 1.5 times the physical RAM (ie....1 gig Memory = 1.5 gig swap)

---

### Post by PieLover on 2009-01-31
Thank you for all your help. I've successfuly installed ubuntu! \\:D/

---

### Post by bunnsnow on 2010-10-12
Hi Guys, just a quick "How to" here on installing Ubuntu into free space on your HDD. Just in case anyone else has similar problems......

What you will need to do is:

[LIST=1]
[*]Click on the free space you have and select [COLOR=Red]*Create new partition*[/COLOR]. Then select [COLOR=Red]*Logical*[/COLOR], then* [COLOR=Red]Swap[/COLOR]* and set the size to double your system memory or 1.5x
[*]                   Select the remaining space (unless you want a home partition). Click [COLOR=Red]*Create new partition*[/COLOR]. Then select [COLOR=Red]*Logical*[/COLOR], *then [COLOR=Red]Ext3[/COLOR]* and set it to use the remaining space. Lastly enter the mount point as */*.
[/LIST]
In regards to the home partition. This step is not necessary but will allow you to keep your settings and  files in the event you reinstall Ubuntu. The home partition can be setup the same as you would for the root  partition, but choose [COLOR=Red]*/home*[/COLOR] as the mount point.

---

