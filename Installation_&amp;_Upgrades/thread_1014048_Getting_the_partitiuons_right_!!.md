---
title: "Getting the partitiuons right !!"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by Zickar on 2008-12-17
So I'm back again with my heart set out to install Xubuntu again, Last time I did I dleted my Windows but this time I wanna make sure I do it right so I read this tutorial on Softpedia : [http://news.softpedia.com/news/Installing-Ubuntu-8-10-97417.shtml](http://news.softpedia.com/news/Installing-Ubuntu-8-10-97417.shtml) that is very illustrative and easy and I think I'm ready and I think I will be able top install it without deleteing windows again but the thing is I wanna make sure when I choose "Guided - resize the partition and use the freed space" what exactly will Xubuntu do ???

I Basically have two partitions C and D ... I have devoted one for my WIndows and the other for my everyday work and all my files and programs so basically the C partition (with WIndows on it) has a lot of free space so I'm thinking of using it to install Xubuntu Is that a good idea ???

How ill Xubuntu deal with my partition ?? I mean can it install itself alongside WIndows on the same partition ?? For example can I install Xubunutu and Windows on C ??? When Xubuntu is installed will its folders appear when I'm running windows in C and how will they appear ?? as one big folder ???

Any help is greatly appreciated as I can't stand to even look at windows anymore and I wanna make the switch ASAP

---

### Post by RomanIvanov on 2008-12-17
you cant install Xubuntu on Fat32 or NTFS, create empty partiotion onthe same HDD and install Xubnutu on free space.

---

### Post by Zickar on 2008-12-17
> **RomanIvanov said:**
> you cant install Xubuntu on Fat32 or NTFS, create empty partiotion onthe same HDD and install Xubnutu on free space.

How do I do that ?? I've been told to use partition magic , Will that do ?? Will this help me resize partitions too ??

---

### Post by theozzlives on 2008-12-17
use the live [GParted]("http://gparted.sourceforge.net/livecd.php")  to resize your C: drive so you can install Xubuntu on the free space and Dual Boot.

---

### Post by Zickar on 2008-12-17
> **theozzlives said:**
> use the live [GParted]("http://gparted.sourceforge.net/livecd.php")  to resize your C: drive so you can install Xubuntu on the free space and Dual Boot.

OK Downloading it as we speak .. Its 90+ Mb so I'll download it over night and I'll fiddle with it tomorrow 

Thanks for the pointer , Thanks for the help

---

### Post by oldos2er on 2008-12-17
> **RomanIvanov said:**
> you cant install Xubuntu on Fat32 or NTFS, create empty partiotion onthe same HDD and install Xubnutu on free space.

 Actually you can; it's called Wubi, and was designed for Win* users who want to try out Ubuntu without altering their partitions.

---

### Post by Zickar on 2008-12-18
Yeah, Looks like Its gonne be Gparted live CD, I gave it a spin and the GUI looks very easy but I just want to know what do you think should be the size of my Ubuntu partition ??

30Gb for Ubuntu and 30Gb for Windows is enough right ???

---

### Post by wowgold5hk on 2008-12-18
Many economists and commentators have expressed worries that China might overreact to the crisis and veer away from reform and opening up. For example, this point of view was expressed by Fred Hu of Goldman Sachs, who wrote in the Wall Street Journal Asia of the "danger" that "Beijing is extracting the wrong lesson from recent events at home and abroad."Judging from China's recent macroeconomic moves, especially speeches by its top leaders, it is unlikely that China will change course.At a ceremony on Thursday marking the 30 years of reforms, President Hu Jintao attributed all the country's achievements in economic and social development to the policies, which he vowed to continue.___________[Wholesale](http://www.yoocart.com)[China Wholesale](http://www.yoocart.com)[Wholesale Central](http://www.yoocart.com)[Buy Wholesale Products](http://www.yoocart.com)[Chinese Wholesaler](http://www.yoocart.com)

---

### Post by Zickar on 2008-12-18
I Tried resizing the partitions using Gparted but when I try to apply the changes it keeps giving me an error, I tried using the Ubuntu paritioner and you are right its very easy to use, Just a slider but after I resize the partitions with the slider and press forward it gives me this error message : "An error occurred while writing the changes to the storage devices. The resize operation has been aborted) and takes me to another window that says " Prepare partitions" and has all these options to edit partitions or delete partitions !!

Any idea why I'm getting the error ??

---

### Post by oldos2er on 2008-12-18
The partitions you want to change need to be unmounted. You don't have them mounted while you're running gparted, do you?

---

### Post by Zickar on 2008-12-18
> **oldos2er said:**
> The partitions you want to change need to be unmounted. You don't have them mounted while you're running gparted, do you?


What do you mean by unmounted ???

Eitherway I managed to manipulate partitions while on Windows using EUSEUS , The partitions are now resized and my C partition says 30 Gb (Just like I resized it to be) and D still says 60- Gb like it used to be so everything is fine and I know have 30 Gb of free space

I reboot from Xubuntu live CD and start the installation, when I get to the partition editor (Step 4 of 7) Ubuntu doesn't detect my C partition and instead in the Guided resize option the D partition (dev/sda5) is shown ... Now ofcourse I can install it on D but I just freed 30 Gb for Ubuntu and I want to install it there on the free 30 Gb !!!

Unhappy with this fact I choose the manual option and see what I can figure out about it, I see a list of the contents of my disk which basically shows C and D as dev/sda1 and dev/sda5 respectively and shows "Freespace" 31453 Mb between them and at the end it also shows freespace 8 Mb (which it always did) ... I choose freespace (30Gb) one and press forward then I get this error message

"No root file system is defined.
Please Correct this from the partitioning menu"

I tried going back to see where this menu is but couldn't find it, tried to look at it everywhere but couldn't find it .. Does anyone have any idea what is the cause of this ??

---

