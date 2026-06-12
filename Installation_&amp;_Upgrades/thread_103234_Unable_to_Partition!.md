---
title: "Unable to Partition!"
date: 2005-12-13
forum: Installation &amp; Upgrades
---

### Post by kopolee11 on 2005-12-13
Hello, I recently ordered 5 CDs of Ubuntu Version 5.10 (Breezy Badger) When I first received the disk, I quickly put in the Live disk. It worked 100%, however, I didn't explore it much, because I was anxious to install the real version. After reading a few in depth documents, I felt pretty prepared to install Ubuntu. Boy was I wrong...;) 

When I got to the Partition part, I clicked "Manually edit partition table" Using both this [guide ]("https://wiki.ubuntu.com/Installation/I386")and this [guide]("http://users.bigpond.net.au/hermanzone/p2.htm"), I carefully followed the step. However, when I started trying to shrink the partition, an error came up, saying that it could not resize the partition. Puzzled, I checked both of the guides I used earlier and noticed that neither of them mention this error. I quickly looked through the wiki and found [this]("https://wiki.ubuntu.com/forum/installation/Partitioning"). At the bottom it states. 

> If, when you are trying to shrink your partition, you are not given the option to enter a smaller size, it is because the installer does not feel it is able to resize the partition. Possibly because it thinks it is full, is corrupt, or has some other problems that it cannot solve.

Not knowing what this problem was, I looked through the forums, and couldn't find this same problem in either the "Installation and Upgrade" or the "Absolute Beginner Talk". If you guys could help me figure out what the problem is with my partition that would be great. I'll give you the specs I know.

Microsoft ME
AMD Athlon Processer
368 MB of Ram
Video Card 16MB (Although I don't think that matters for installing Ubuntu)
19 GB Hard drive and I played to give the Linux partition to be 6 GB (Just for testing purposes)

Anyway, thank in advance. If you need more detail or more specs, I'll try to tell you to the best of my ability.

---

### Post by WanderingStar on 2005-12-13
Well, since its Windows ME it would be fat32.  The first thing I would do is run a defrag / scandisk on it and try again.  Parted seems to not like fragmented disks, and scandisk should tell you if there is anything physically wrong that would be preventing this.  If it fails again, try pressing <ctrl>+<alt>+F2 to switch to the next VT that should give a more detailed error.  

Hope that helps a bit
Jeff

---

### Post by Mission 10 on 2005-12-14
I just installed for the first time a few days ago and I did have the same problem, except that I have XP home and after a check disk it fixed the problem. Did you cancel the partition process while it was running? I had a power issue and my computer blinked out during it, and upon the reinstall it would not partition. So your file structure may be a little bit wacky for it not to allow the partition.

---

### Post by atoponce on 2005-12-14
It's been so long since I have performed a Linux install, I have forgotten.  Can you partition an NTFS drive?  Even after degragging it first?  When I installed Ubuntu on my laptop, I first partitioned the drive using Partition Magic, then install the OS.  With the kernel not supporting the ability to write to an NTFS drive, I wonder if it is possible to partition it?

---

### Post by Dhanagopal, R on 2005-12-14
I too have similar problem. I am trying to install ubuntu 5.10 in my system already having Windows XP and Mandriva LE 2005 multibooting with Grub.
Everything went smooth upto paritioning. I choose to manually edit partition. Ubuntu installer did not list the already existing NTFS, FAT, EXT3 partitions. I am unable to proceed further. I need help.

---

### Post by kopolee11 on 2005-12-14
Sorry for not responding for practically a day, I was very busy. I'll try not to let this happen again.

> Well, since its Windows ME it would be fat32. The first thing I would do is run a defrag / scandisk on it and try again. Parted seems to not like fragmented disks, and scandisk should tell you if there is anything physically wrong that would be preventing this. If it fails again, try pressing <ctrl>+<alt>+F2 to switch to the next VT that should give a more detailed error.

Hope that helps a bit
Jeff

I did run a disk defrag, but I did not run scandisk. I'm running both of those right now, so it might take a while. ;) 

After I do that again, I'll try again, and if I get the same error I'll press <ctrl> + <alt> + F2, (Question is that the "ctr-alt-delete" of Linux.) and I'll post the error message. Thanks.

> I just installed for the first time a few days ago and I did have the same problem, except that I have XP home and after a check disk it fixed the problem. Did you cancel the partition process while it was running? I had a power issue and my computer blinked out during it, and upon the reinstall it would not partition. So your file structure may be a little bit wacky for it not to allow the partition.

I didn't cancel the partition process while it was running, instead I just clicked "Size" and it came with the error. However, I do agree my file structure is probably really screwed up. :( 

> It's been so long since I have performed a Linux install, I have forgotten. Can you partition an NTFS drive? Even after degragging it first? When I installed Ubuntu on my laptop, I first partitioned the drive using Partition Magic, then install the OS. With the kernel not supporting the ability to write to an NTFS drive, I wonder if it is possible to partition it?

Although this is my help thread, I'll try to help you as best as I can. :)  I believe you can partition a NTFS drive and some instructions to do so are [here]("http://users.bigpond.net.au/hermanzone/p3.htm"). Have fun. :cool: 

I don't know how to fix your problem Dhanagopal, sorry . :confused: 

Thank you all for the advice.

---

