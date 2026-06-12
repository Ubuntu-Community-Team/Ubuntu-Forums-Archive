---
title: "Installation can't detect free (unused) space on my hard drive"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by cthulhu_54 on 2009-01-09
During the past few weeks I have been trying to install Ubuntu on my laptop, without success. It's a 40 GB single partion (C:\) HD with Windows XP (NTFS) installed. I have cleared some 12 GB for Ubuntu, and done a complete defrag and scanned it for bad sectors and such. I have also read all the documentation on the home page about partitioning and installing Ubuntu. Yet when I start the live CD and run the installation it simply detects 39999 MB HD filled! (or unallocated I think) and a partition of 8 MB free (is this the system recovery?) and therefore it only offers me a installation of 100% ubuntu on the HD (in both guided and manual), but I want a dual boot. 

I have tried everything, both the Ubuntu CD (including the alternate text-based one) and the Kubuntu. I have also downloaded a system rescue CD with Gparted (I think it was called) and same thing there: is refuses to recognize my 12 GB free space at the end of my disk. When I enter the partition program and select my drive it says something in the line of "damaged drive, bad sectors yadda-yadda", but nothing shows up when I let windows do a complete system check.
Although I am a complete novice on the world outside win & Dos I don't think I'm doing anything wrong because once I had my external 250 GB (FAT) drive connected and the installation software could detect the free space on this one, and allowed me to resize the drive.

In summary: the free space on my computer is continuous at the end of the drive and have once been filled with crap now deleted. I have never done any partitioning in the past.

So please help me leave the horrible world of Windows, (without loosing it, though)!

---

### Post by Pumalite on 2009-01-09
Did you format those 12 GB?

---

### Post by cthulhu_54 on 2009-01-09
Umm, well, I am a noob, so probably the answer is no. I have access to the 12 GB through Windows, but I was under the impression the installer could do all that I need in order to get a new partition from a existing windows partition. I can't select the windows partition and resize it as I can with my external drive.

---

### Post by Pumalite on 2009-01-09
You are right. But since you have problems; try formatting it.

---

### Post by cthulhu_54 on 2009-01-10
OK, How can I do that without loosing Windows?
Alternately, without loosing the system recovery partition.

---

### Post by Pumalite on 2009-01-10
Vista or XP?

---

### Post by cthulhu_54 on 2009-01-10
It's XP.

---

### Post by Pumalite on 2009-01-10
Turn PageFile to '0' (later back to original size)
Use Gparted to shrink XP to desired size. (from right to left)

---

### Post by cthulhu_54 on 2009-01-10
You are forgetting I'm a noob, where do I turn PageFile to '0'?

---

### Post by Pumalite on 2009-01-10
Sorry, I'm not a Windows user:
[http://www.theeldergeek.com/paging_file.htm](http://www.theeldergeek.com/paging_file.htm)
[http://www.petri.co.il/pagefile_optimization.htm](http://www.petri.co.il/pagefile_optimization.htm)

---

### Post by cthulhu_54 on 2009-01-14
Thank you very much for your help, I think I have solved the problem, which is described on the site you mentioned under "Resizing An Existing Partition On A Single Hard Drive";

[http://www.theeldergeek.com/hard_drives_05.htm](http://www.theeldergeek.com/hard_drives_05.htm)

Although it is not as easy as turning the Pagefile to 0 (inactivating the virtual memory), which unfortunately, did not help. I will now give a short description of my findings in case there are more lost souls out there with the same problem.

After reading on the site I realized the problem has nothing to do with Ubuntu or the installation software, but rather, it can be found within Windows XP by entering the Disk Manager in the Microsoft Management Console, which is a part of every XP system. This can be done by clicking Start > Run and type diskmgmt.msc in the Open: line and click OK. Then click on the disk manager, alternately you can type diskmgmt.msc instead to get to the disk manager immediately. Here you can see the partitions on your hard drive and create new partitions. If your having the same problem as I you should see your entire disk as Blue, which corresponds to full, which is bizarre since in the partition table it clearly says that (in my case) 20 % is free. On a "normal" drive these 20% should be seen as Green in the bargraph and then you simply right-click on this and create the new partitions you want to have.

Unfortunately this built in partitioning tool in XP can not resize the existing partition, nether can the Ubuntu installer or Gparted, instead you have two options which are described on the site. I have taken the liberty of copying the excellent text in case the link should be broken.

"Method 1 - Reinstall XP from a bootable CD (exactly what I did in Partitioning A Blank Hard Drive During XP Installation) and create an install partition that is smaller than the total capacity of the hard drive. Of course this method has a very substantial downside; everything on the hard drive, including data and applications, will be lost when the drive is formatted. While this method is effective it's only practical in a limited set of circumstances, unless of course you enjoy wiping a hard drive totally, designing a partitioning scheme in your mind, and then setting it up from scratch.

Method 2 - Use a program that is designed to handle partitioning tasks from inside the existing Windows operating system. The best known program of this type is probably PartitionMagic by PowerQuest, although there are many others including PartitionExpert by Acronis and Partition Commander by V Communications. A Google search will turn up many others as well as some free utilities to accomplish the same results."


Well there you have it, the thing that still clouds my mind though is why not more people have encountered this problem as it seems to be a very common system set up.

---

