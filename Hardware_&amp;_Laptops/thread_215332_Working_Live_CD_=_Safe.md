---
title: "Working Live CD = Safe?"
date: 2006-07-13
forum: Hardware &amp; Laptops
---

### Post by oxboy on 2006-07-13
Hi All!

I've been wanting to try ubuntu by dual booting on my laptop (Dell Latitude D600), but I've been reading about so many problems that I'm honestly scared to try it.  

I'm in a situation where I might need to format my drive because for some reason, the ubuntu partitioner tells me I don't have enough space to create a new partition even though I have 17 gigs of free space.  If I format my drive though,  I might not be able to get windows working because I'm not sure I have all the software I need.  So if windows doesn't work,  I really need ubuntu to.

I tried the Live CD ( Dapper) and it seems to work ok.  Screen resolution is alright, programs seem to work fine... but I haven't been on it for long.  Both my LAN and WAN are not working though.

In any case, are there things I need to check for during my Live CD trial so that I know with a higher probablity that Ubuntu will also work with the installation?  Thanks so much!

---

### Post by didobuntu on 2006-07-14
I am sure the Latitude D600 is ubuntu capable ... google it and see .. also look at the Ubuntu Wiki where Dell laptops are intensively tested as they are the most popular ...

About the partitioner, try again and again to create new partitions for linux ... I personally have always this proplem when I install Drapper from LiveCD (I did it with my two laptops and one desktop) ... 

In the installer ... at step 5 I think ... when you have to choose your partitions to create ... try again ... if there is an error, go back then go forward ... it always works for me like that.

You have to follow the stairs, first format the system partition (that where you install in the / partition), then if any, format the /home partition, then format the swap space partition .

Good Luck

---

### Post by T700 on 2006-07-14
Try doing all the things you normally do.  If you play music, play it with the Live CD.  Try OpenOffice.  Browse the net.  You get the idea.

Once you decide to install, don't forget to backup your data, even if you're doing a dual boot!

Paul

---

### Post by meatbop on 2006-07-14
> **oxboy said:**
> ..the ubuntu partitioner tells me I don't have enough space to create a new partition even though I have 17 gigs of free space.

When you say free space do you mean free space visible on your on your hard drive in windows explorer or unallocated space with no partition?

---

### Post by oxboy on 2006-07-14
free space in windows explorer.  When I got my laptop I didn't know that I should have format the presettings that it comes in and start fresh.

Thanks for your advice! I'll post in the network section to see if anyone can help me figure out why my network card can't connect to LAN...

It's actually strange cause I can't do it in windows either!  I can only use wireless right now.. which has me worried.  I hope my network card isn't fried =).

---

### Post by meatbop on 2006-07-15
> **oxboy said:**
> I didn't know that I should have format the presettings that it comes in and start fresh.

You don't.

There are a number of programs, both free and non free, which can non destructively resize your windows partition.  You can then create a new partition in the *unallocated* space.

If the installer for some reason either isn't presenting you with the option to do this or failing to do so when you ask, use another utility to resize your Windows FAT32/NTFS partition and create a new ext2/ext3/ReiserFS/whatever partition for Ubuntu to be installed to, and a swap partition of about 512MB.

You may wish to have a third partition as (I think) writing to an NTFS partition is not yet fully supported in Linux except through "experimental" software, though I'm sure Fedora, for example, has writing to NTFS volumes enabled by default. 

Forum member aysiu has a useful resourse that is informative regarding dual boot partitioning [here]("http://www.psychocats.net/ubuntu/separatehome.html")

---

### Post by oxboy on 2006-07-15
Thanks for the tip.  I never thought of using another partitioner.  I just assumed that all of them would give me an error, but I'll give it a try!

---

