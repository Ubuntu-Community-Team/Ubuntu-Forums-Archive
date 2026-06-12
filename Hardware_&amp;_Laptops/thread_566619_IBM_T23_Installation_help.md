---
title: "IBM T23 Installation help"
date: 2007-10-03
forum: Hardware &amp; Laptops
---

### Post by Fran89 on 2007-10-03
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=499518](http://ubuntuforums.org/showthread.php?t=499518) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I've searched the forums and have found people with the same problem, but no solution. First I tried to boot up with the Live CD but have found that it takes forever for my T23 IBM, P.III, 256MB RAM laptop to even present the desktop, after that I downloaded the alternate and tried to install here is my problem... I have a ~20GB HD and I  have my windows taking up 1/2 ~10Gb, I have tried with the Alternate CD to make a 6GB partition( I read you need 2Gb for the install, 1GB more for the updates and I've been wanting to leave 3 for misc. stuff) but I cant partition it, it says I need more room... do I really need more room? can't I just make a partition from windows and then choose to install it there?

Any help is appreciated.

---

### Post by gn2 on 2007-10-03
It's possible that there's data in the area of the drive you want to set aside for Ubuntu.

If you have a Windows based partitioning utility, use it to reduce the size of the partition(s) to leave free unallocated space, then install into that space using the installer to create the partitions for Ubuntu.

Xubuntu would perhaps be a better option for your laptop.

7gb should be plenty.

My Xubuntu / partition has 2.7gb in it, including quite a few additional programs.

Remember to leave about 20% free space in your Windows partition so that the defragmenter can work properly....

---

### Post by Fran89 on 2007-10-03
Hmmm. i tried using the ubutu included partitioner, in the alternate CD, any partition manager you would recommend so i can make the partition in WIndows and use the CD For installing only

---

### Post by gn2 on 2007-10-04
There are free ones available but I've never used one.
Search the net, you're bound to find one.

I have Partition Magic 8.0 which is excellent for this job.

I would suggest though that your money would be better spent on a bigger new hard drive, as you're going to strugglw with just 20gb available.

If you do get a new larger drive and install from your Windows CD, you can choose the size of the partition to install to and leave the rest blank.

---

### Post by Fran89 on 2007-10-04
ok.. but i currently have no money, I use it for college. so ok I'll just try to find a partitioner, thanks for your 
help tho.. :)

---

### Post by trippinnik on 2007-10-04
What kind of partition is you windows partition?  If it's NTFS it'll be difficult to resize, but if you use Knoppix or another lightweight LiveCd you should be able to resize it but you'll need the liveCD to have ntfs-3g.  
My theory is that you have Windows installed using ntfs and it takes up the whole drive.  You have 4Gb of free partitioned space you want to use for Ubuntu.  
Have you backed up your data?  If not do so before continuing.

---

### Post by Fran89 on 2007-10-05
Yeah Its NTFS and yeah i checked its taking up the entire drive, is it such a risk to resize? im having second thoughts.. Ive been wanting to make a 6Gb partition but the live CD wont boot...Its supposedly has a problem with IBM thinkpads T20-T23 refer to the thread i pointed out([http://ubuntuforums.org/showthread.php?t=499518](http://ubuntuforums.org/showthread.php?t=499518)). I really want ubuntu but a few programs on windows i really need too.

---

### Post by Fran89 on 2007-10-06
Hmmm Ive been thinking and found that maybe Wubi is the answer, anyone it used before? is it safe? is it just as fast? or should i resize the NTFS?:confused:

---

### Post by Fran89 on 2007-10-07
Ok so i resized, and installed, to my surprise everything went flawlessly. there is just one problem. Whenever I try to Hibernate the computer hibernates but within seconds it turns on again? im running Festy and I'll possibly upgrade to Gutsy soon but if anyone has a fix, please help.. thanks in advanced! :)

---

### Post by lank23 on 2007-10-09
I also have a dual boot T-23 laptop setup the same way but with a 40gb drive.  When I am in Ubuntu I do not use the Hibernate instead I just close the lid and the laptop will go into standby, but sometimes the video does not come back after opening the lid and I have to press and hold the "Fn" key while cycling the "F7" key to get the video back to the LCD screen instead of the S-video.

lank23

---

### Post by Fran89 on 2007-10-09
yeah i found that mine is 27Gb not 20, still i rather hibernation I have only so much battery (100% = 30~25min run) and no money for a new battery,

---

