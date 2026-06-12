---
title: "Making partitions in Linux"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by jothunder on 2009-10-17
Hello people,
 
I am new to Linux and I am installing Ubuntu next to Windows Vista.
The problem i had when i installed everything is that my whole ext3 partition was full of installation data, so i can't install anything anymore. I installed the partition as ext3 and /. Should i make more partitions for the different files like, 1 partition for /boot and another partition for /home ?? And how big I need to make it, so i can install programs afterwards and work with them with getting the error of not enough disk space?? Help would be nice :)
 
Greetz

---

### Post by oldfred on 2009-10-17
I think you are the third one today that I have seen with this problem. They really need to fix the install. You got bit by the slider that you have to move to make more space. Ubuntu will fit into about 4GB but we recommend 10GB unless you are installing lots and lots of big stuff. It also depends on whether most data like movies & music are in another partition.

HOWTO: 2.5 GB System Partition - What Went Wrong? 
[http://ubuntuforums.org/showthread.php?p=7658271](http://ubuntuforums.org/showthread.php?p=7658271)

---

### Post by jothunder on 2009-10-17
So i can't fix this? Making several partitions is not an option so i can install more updates, programs etc?

---

### Post by tpjk on 2009-10-17
> **jothunder said:**
> Hello people,
 
I am new to Linux and I am installing Ubuntu next to Windows Vista.
The problem i had when i installed everything is that my whole ext3 partition was full of installation data, so i can't install anything anymore. I installed the partition as ext3 and /. Should i make more partitions for the different files like, 1 partition for /boot and another partition for /home ?? And how big I need to make it, so i can install programs afterwards and work with them with getting the error of not enough disk space?? Help would be nice :)
 
Greetz

if you're planning on keeping your personal data on a different partition/using the ext3 partition only for ubuntu and additional software your ubuntu partition should be around 10 to 15 GB in size.
in order to change the size of your ubuntu partition just boot from your live cd and open the partition editor (System -> Administration -> Partition Editor). Make sure everything is unmounted. Additional information on how to use the partition editor can be found at [http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

backup your data before attempting to resize your partition(s)!

good luck!

---

### Post by jothunder on 2009-10-17
Wel i made the partition 12 Gb but it was completly filled up with installation data. And going bigger is not possible since Vista is using the rest of the amount and i already shrunk the vista part.

---

### Post by tpjk on 2009-10-17
> **jothunder said:**
> So i can't fix this? Making several partitions is not an option so i can install more updates, programs etc?

don't create several partitions, just resize the one you installed ubuntu to :]

before doing anything you might want to open up a terminal and post the output of

```
sudo fdisk -l
```so we can get a better idea of your current setup and perhaps provide some more detailed suggestions.

---

### Post by tpjk on 2009-10-17
> **jothunder said:**
> Wel i made the partition 12 Gb but it was completly filled up with installation data.

that's unusual.

for now, let's start by looking at your existing partitions. please post the output of sudo fdisk -l

---

### Post by jothunder on 2009-10-17
I removed everything to start all over again so i don't have an output right now :s
Should i install ? But with what sizes of partitions?

---

### Post by tpjk on 2009-10-17
> **jothunder said:**
> I removed everything to start all over again so i don't have an output right now :s
Should i install ? But with what sizes of partitions?

you can still get the output if you boot into your live cd, open a terminal and type sudo fdisk -l there. i can't really make any sensible suggestions if i don't know anything about how your hard drive is currently set up.

---

### Post by jothunder on 2009-10-17
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc10a28e3
 
Device Boot             Start              End           Block           Id         System
/dev/sda1                1                   1567         12586896     27        Unknown
/dev/sda2                1568              17928     131414948     7          HPFS/NFTS

---

### Post by tpjk on 2009-10-17
> **jothunder said:**
> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc10a28e3
 
Device Boot             Start              End           Block           Id         System
/dev/sda1                1                   1567         12586896     27        Unknown
/dev/sda2                1568              17928     131414948     7          HPFS/NFTS

ok with this setup i'm not entirely sure if you're going to be able to make this work.

please check if sda2 is your boot partition:

1) run the partition editor from the live cd
2) in the 'Flags' column look for where it says 'boot'
3) report back here

---

### Post by tpjk on 2009-10-17
i also suggest you do some reading on partitioning/setting up a dual boot system:

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://gwos.org/udsf/doku.php/core:dualbooting:ubuntu](http://gwos.org/udsf/doku.php/core:dualbooting:ubuntu)

---

### Post by jothunder on 2009-10-17
Can't find the partition editor :s
I just see now that i can install them next to each other with an option for dual boot.
Maybe i should do this , so it will use my vista partition i guess?

---

### Post by tpjk on 2009-10-17
> **jothunder said:**
> Can't find the partition editor :s

open a terminal and type

```
sudo gparted
```

> I just see now that i can install them next to each other with an option for dual boot.
Maybe i should do this , so it will use my vista partition i guess?

theoretically, yes, but isn't that what you did when you installed it for the first time and ended up with a partition that was already completely full?

---

### Post by jothunder on 2009-10-17
No i selected the option specify partitions manually, so I made an extra partition for Linux.
But when i install Ubuntu next to Vista it will install on the same partition as vista right?

---

### Post by tpjk on 2009-10-17
> **jothunder said:**
> No i selected the option specify partitions manually, so I made an extra partition for Linux.
But when i install Ubuntu next to Vista it will install on the same partition as vista right?

not necessarily. if you want your ubuntu install on the same partition as vista you should use the wubi-installer.

---

### Post by tpjk on 2009-10-17
like i said though, i really think you should read some tutorials before attempting to install ubuntu again. judging from the way your hard drive is currently set up there is definitely a chance that something could go wrong if you're not absolutely sure you know what you're doing.

it seems like you want to get the installation process over with as quickly as possible and believe me, i understand. but if this is the first time you're trying to install ubuntu/set up a dual boot you should take. your. time.

---

### Post by jothunder on 2009-10-17
Well i tried the Wubi installer but when it copies the data to my disc it gives an error at the end.
Unless you know what this error is i can use it.
Now I installed ubuntu the same like i did before and now i have spaces i guess, WEIRD :) I have to look at file system and then at properties free space right? That's the amount of space i have to install programs?

---

### Post by jothunder on 2009-10-17
i will look at the topics but it seems i have enough free space on my file system.
Thx i go sleep now

---

### Post by jothunder on 2009-10-17
I know what i did now, i didn't copy previous documents from vista to Linux and now i have enough space, it was probably to much data, or secured.
 
Thx for the help i will read the tutorials tomorrow

---

### Post by tpjk on 2009-10-18
> **jothunder said:**
> Thx for the help i will read the tutorials tomorrow

you're welcome. i have no idea what you did but it seems like you made it work, which is great. :popcorn:

---

### Post by Bartender on 2009-10-18
jo - 
Did you go into vista Disk Management and try to shrink the vista partition?  You might have better luck that way than having the Ubuntu installer try to shove vista aside.
Even using vista's tool, you may have limited success because of the way Windows scatters data hither and yon, then labels it unmovable.
Have you made recovery discs yet?  Or did your computer come with them?
I ask this because another route, although it may seem a little radical to you, goes like so:

#1: Wipe the HDD entirely using a partitioning tool like GParted or other.
#2:Create a primary NTFS partition out of the "front" of the HDD (depicted as the left-hand side of the drive in the partitioners).  Leave the rest of the HDD unallocated, or create an extended partition, or even a primary ext3 partition.  This second part doesn't matter so much, we just want to make sure the second part of the drive isn't NTFS.
#3: Pop your vista recovery disc in.  It "should" only recognize the NTFS partition and install to vista to that partition, leaving the rest of the HDD alone.  

You then have the rest of the drive to install Ubuntu.  I realize that advice sounds a bit like jumping out of a perfectly good plane, but it works.

---

