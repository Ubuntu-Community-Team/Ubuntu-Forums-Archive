---
title: "How do I install Ubuntu 9.10 on a partition that I've already set aside?"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by Smithers37 on 2009-11-12
Hi. I have just finished installing Windows Xp and Windows 7, I installed Xp and 7 on their own partition and left 50GB for Ubuntu. When I started the installation procedure, I assumed I'd be able to just select the partition that I set aside and have it install there.

I only seem to have options to erase my 1TB storage HDD or install along side the Windows 7 partition.

Is there anyway I can just install it on this partiton?

Thanks!:)

---

### Post by apostra on 2009-11-12
Hi there,

Don't you have the option for manual partition at the end? You partition would be appear as free space at installation, since no OS is on there.

I just did the same thing on my PC ( with the help of the guys here of course, couldn't alone ).

What i did was:

1)boot on Live-CD, open the G Parted.
2) Delete all the partitions except the two using the vista adn want to keep the for vista
3) Created a new **[COLOR=black]Extended Partion,[/COLOR]**[COLOR=black] I put bold cause unfortunately all guides i found was saying "create partition" and i added Primary at first, then I got the msg that cant make more than 4 partitions, when i was trying to make the last one, the swap. So if you are noob like me Extended than Primary at the first one.
4)Create a Primary partition with label /
5)Resized the Primary partition, on step 4, to make a new partition with label /home
6)Finally resize the partition on step 5, the /home partition, to make a swap
7)Exit G parted and runt he installation
8)Choose manual
9)On the next page of installation, double click the the partitions you just made and click the option "format this partition" or whatever says, don't remember exactly. 

In general meaning, what i've been advised is that, you need a swap "/" and "/home" partitions to install Ubuntu. 

******Of course if your partition is already there and waiting, you don't have to do the step 2 ******


_**Don't miss this please:**_ However that was my first attempt to install Ubuntu so would be better to **wait** for more experienced to comment on your post or guide you, before doing the same. I'm just mention what I did.


Good luck with your installation mate.

Regards


[/COLOR]

---

### Post by Smithers37 on 2009-11-12
Thank you apostra, I will certainly try what you have said:)

The worst case scenario, is that I have to reload Xp and 7 all over.

I will let you know how it goes a bit later on when I get some time :-)

---

### Post by audiomick on 2009-11-12
Apostra is right, go into the manual bit, and you can tell it to do what you want.

Have a look at these

[http://ubuntuforums.org/showthread.php?t=1321649](http://ubuntuforums.org/showthread.php?t=1321649)
[http://ubuntuforums.org/showthread.php?t=1323935](http://ubuntuforums.org/showthread.php?t=1323935)

---

### Post by darkod on 2009-11-12
Just to add, if you already have free space left just boot with Ubuntu CD, start the installation process and when you select Manual Partitioning the partition manager will show up and allow you to use the free space.

In this case there is no need to boot with Live CD and use Gparted because you would need to use manual partitioning later anyway. So it's twice the same work and plus it can confuse newbies. :)

---

### Post by Bartender on 2009-11-12
It all depends on how many primary partitions have been placed on the HDD.  If you try to install Ubuntu and there are already four primaries, the installer gets two-blocked.  From what I've seen on the forums it will suggest wiping the drive and offer few if any other options.

---

### Post by audiomick on 2009-11-12
Probably a good idea to start Gparted from the live CD and have a look.
Bartender is right, if the two Windows have already got 4 partitions happening, you wont be able to make any more. You said you have a 50GB one for Linux?
I read that Windows 7 creates 2 partitions for itself.
Windows XP is also one for itself, I assume.
So if your 50GB one for Linux is a primary, you will have 4, and you will need to change it to an extended so you can create the necessary (what will then be logical) partitions for Ubuntu. They will be at least a swap and another one. A good idea is one for / (the system), and one for /home (all your personal stuff and configs), and  a swap that is a bit bigger than your RAM.

---

### Post by Smithers37 on 2009-11-12
Hello folks!

Just to update you, I'm all done and set up. Thanks all for your help.

Here is what I did (with your guidance):

1) Installed Windows XP, set it up on a 50GB partition and created 2 partitions, one 200gb partition and another 50gb partition.

2) Installed Windows 7 on 200GB partition

3) Loaded Ubuntu installer, filled in boxes etc

4) Selected Manual partitioning. Deleted 50GB partition that I made, created a 2GB swap partition and then created a new partition "/" and selected to install Ubuntu there.

5) Followed it through and now it's working perfectly the way I wanted it to be.

I'm chuffed guys, can't thank you all enough:popcorn:

---

