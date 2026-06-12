---
title: "still cant format"
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by rogerrabbitsclone on 2009-05-10
so i installed ubuntu 8.10 on the computer im on now, but now i want windows on this one and ubuntu on another. i can install ubuntu fine on the other, but my bootable windows CD wont work on this one. so i want to reformat and start from scratch.

also, im sure its not the CD, ive tested it on several other windows computers.



cariboo907
Cariboo Cowboy Coffee...Mmmmm
 
cariboo907's Avatar
 
Join Date: Mar 2006
Location: Williams Lake
Beans: 7,998
Ubuntu Karmic Koala (testing)
	
Re: cant format
Have you swapped cd-rom drives between the two computers to see if that makes a difference?

 
Join Date: Mar 2009
Beans: 5
	
Re: cant format
no, but every other dvd or cd i put in works.

i have the ubuntu 8.10 cd, is there a way to start installing it, then yank out the power cord when it starts formatting the h/d so it can re-install? i know it sounds bad for the computer, but do you think it'll work?




Old 4 Days Ago 	  #4
el.norman
5 Cups of Ubuntu

Re: cant format
Maybe that one has a different HDD (hard disk) that is not currently supported under the win xp installation cd, mostly if it is SATA. If that the case you have to include the HDD drivers in the CD.

---

### Post by cariboo on 2009-05-10
Are you saying that your Windows install CD won't boot, or that once you get to the partitioning stage Windows won't repartition the hard drive? 

If thats the case, just boot from the LiveCD and once at the desktop go to System-->Administration-->Partition Editor and delete the ext3 partitions.

Once the ext3 partitions are deleted, you should have a bare hard drive and then Windows should be able to partition the drive.

As an aside Windows can't see or access ext3 partitions, but in cases where I've installed Windows on a hard drive that previously had Linux on it, I have been able to delete the unknown partions and then install Windows.

---

