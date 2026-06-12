---
title: "ubuntu 9.04 and xp &quot;no side by side option&quot;"
date: 2009-06-09
forum: Installation &amp; Upgrades
---

### Post by pendolino on 2009-06-09
Hi,

I have just reformatted my computer HP ze5400 and reinstalled the original windows xp. After having done so, I have tried to install ubuntu 9.04 (release:
Suite: jaunty
Version: 9.04
Codename: jaunty
Date: Mon, 20 Apr 2009 13:36:22 UTC
Architectures: i386
Components: main restricted).

I wanted to have it side by side with xp and I was indeed expecting to choose the "Install them side by side, choosing between them each startup" option.........but I did not find such an option......only the other three: "use the entire disk", "use the largest continuous free space" and "specify partition manually".

Does anybody knows why?

Thanks

---

### Post by presence1960 on 2009-06-09
> **pendolino said:**
> Hi,

I have just reformatted my computer HP ze5400 and reinstalled the original windows xp. After having done so, I have tried to install ubuntu 9.04 (release:
Suite: jaunty
Version: 9.04
Codename: jaunty
Date: Mon, 20 Apr 2009 13:36:22 UTC
Architectures: i386
Components: main restricted).

I wanted to have it side by side with xp and I was indeed expecting to choose the "Install them side by side, choosing between them each startup" option.........but I did not find such an option......only the other three: "use the entire disk", "use the largest continuous free space" and "specify partition manually".

Does anybody knows why?

Thanks

There should be an option "guided resize" on the Prepare disk space window of the partitioner. if you only have a windows partition on your hard disk use this. You can drag the corner of the partition graphic to resize for Ubuntu.

If you already have a partition or free space for Ubuntu on your hard disk use the "manual" option. 

**_Prior to resizing Windows always defrag your Windows at least once or twice or you run the risk of errors._**

check this out : [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

P.S. I see this is your first post so I am assuming you are brand new to Linux. You may want to read the above link and these also to familiarize yourself with the install process and prep prior to install. It is best to know what you are going to do and have all your ducks in a row.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
Go here : [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)  to get the free pdf Ubuntu pocket guide. It has step by step description and instructions on how to install

**Again it is best to read and study before undertaking the task of setting up a new OS.**

P.S. I see you just restored Windows. I would definitely defrag that puppy. Some of the worst fragmentation occurs after a Windows install...go figure but that is Windows for you. It can't even get it's own install right!

---

### Post by YldGuy on 2009-06-09
> **pendolino said:**
> Hi,

I have just reformatted my computer HP ze5400 and reinstalled the original windows xp. After having done so, I have tried to install ubuntu 9.04 (release:
Suite: jaunty
Version: 9.04
Codename: jaunty
Date: Mon, 20 Apr 2009 13:36:22 UTC
Architectures: i386
Components: main restricted).

I wanted to have it side by side with xp and I was indeed expecting to choose the "Install them side by side, choosing between them each startup" option.........but I did not find such an option......only the other three: "use the entire disk", "use the largest continuous free space" and "specify partition manually".

Does anybody knows why?

Thanks

because the installer is changed. you can use the manual installation mode and choose the partition you have kept for ubuntu.

---

### Post by diesal3 on 2009-06-09
install side by side works if you have two partitions on your hard disk, if i remember correctly, though that was in intrepid. specifying partitions is easier though

---

### Post by pendolino on 2009-06-09
Thanks everybody,

I am going to defrag and try the manual partitioning......let's see!!!!

---

### Post by monguin61 on 2009-07-19
I'm in a similar situation - trying to install 9.04 over a brand new XP install. I have only two options at the partition step of the installation - use entire disk and specify manually. I tried to follow instructions at [https://help.ubuntu.com/community/HowtoPartition/ResizingPartition](https://help.ubuntu.com/community/HowtoPartition/ResizingPartition), but I am unable to resize the partition in gparted either. I can click the resize toolbar button, but the "resize/move" button in that dialog is grayed out, so I can never actually do it. The Partition->Unmount option is also grayed out, so I assume the disk is not mounted. 

Did I do something wrong installing XP? I don't understand why every possible option I have for resizing my partition is always grayed out. Would I have more luck using a different partition editor?

Thanks

edit: i asked the exact same question a year ago... [http://ubuntuforums.org/showthread.php?t=857058](http://ubuntuforums.org/showthread.php?t=857058)

---

### Post by SyAu on 2009-11-18
I'm also in a similar situation. When i tried to install ubuntu in my laptop which has xp, i'm not getting the 'Install them side by side ...' option but all the other 3 options. **pendolino** did you find a solution to this problem.

---

### Post by raymondh on 2009-11-18
> **SyAu said:**
> I'm also in a similar situation. When i tried to install ubuntu in my laptop which has xp, i'm not getting the 'Install them side by side ...' option but all the other 3 options. **pendolino** did you find a solution to this problem.

Help us visualize.  Are you in liveCD/live session?  If yes, access a terminal (applications > accessories) and type:

sudo fdisk -l

small letter L.  Copy/paste back results in your next post. 

In the meantime, I'll boot my jaunty disc.

---

### Post by SyAu on 2009-11-19
> **raymondhenson said:**
> Help us visualize.  Are you in liveCD/live session?  If yes, access a terminal (applications > accessories) and type:

sudo fdisk -l

small letter L.  Copy/paste back results in your next post. 

In the meantime, I'll boot my jaunty disc.

Thanks raymondhenson, I solved this. Please have a look at this thread,

[http://ubuntuforums.org/showthread.php?t=1327151](http://ubuntuforums.org/showthread.php?t=1327151)

---

