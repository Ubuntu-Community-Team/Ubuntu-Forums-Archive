---
title: "Help Installing 9.04"
date: 2009-10-14
forum: Installation &amp; Upgrades
---

### Post by megaman2000 on 2009-10-14
Installing 9.04 on a laptop with XP already installed on it. 

For some reason, I am unable to make a new partition even though there are 19 gigabytes free...it says they're all taken up by the windows partition :\

---

### Post by zkriesse on 2009-10-14
Did you shrink your hd before installing ubuntu? Go here... [http://doc.gwos.org/core:dualbooting:ubuntu](http://doc.gwos.org/core:dualbooting:ubuntu)

---

### Post by tuxxy on 2009-10-14
Did you create a new partition using the free space first

---

### Post by raymondh on 2009-10-14
> **megaman2000 said:**
> Installing 9.04 on a laptop with XP already installed on it. 

For some reason, I am unable to make a new partition even though there are 19 gigabytes free...it says they're all taken up by the windows partition :\

Hi,

First of all, a caution.  Try not to maximize/use up all space for windows.  What I mean is that if you have 100GB set aside for windows, make sure you leave about 10% of that (10GB) free as "breathing room" for windows.

back to your issue:

1.  back-up your files.  No guarantees.
2.  Defrag windows (2x if you have time) if you are taking space from windows
3.  When you get to the install, in step 4, you can choose side-by-side and USE THE SLIDER to allocate partition sizes.  Remember to use the Slider.  See attached.

[http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874](http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874)

If you want to create an empty space beforehand ... you can:

1.  defrag windows
2.  shrink windows and leave space unallocated
3.  install (step 4) choose "install in largest continuous free space"

If you want to create the partition beforehand ....

1.  defrag windows
2.  Shrink windows
3.  Use gparted to create and format the space you freed up
4.  In install, step 4, choose manual ... highlight the partition you just created > edit > use as > mountpoint > format

XP's disk utility will not shrink partitions.  You can use gparted.  I suggest you just try the side-by-side install as it is the easiest to accomplish.

Regards,

---

### Post by megaman2000 on 2009-10-14
Okay...the first time I was trying to install, installing side by side wasn't even an option...will this change when I shrink the main partition?

---

### Post by PrePenguin on 2009-10-14
> **megaman2000 said:**
> How do I shrink the partition in XP? That guide is for Vista....
 
 
Dont believe XP has the shrink option therefore you have to manually or use software to create the partition or let gparted doit on install however you may have a hidden recovery Partition on your Hard Drive to re-install windows if needed be so watch for that.

---

### Post by megaman2000 on 2009-10-14
Gparted isn't letting me touch the windows partition at all....Or am I doing it wrong?

---

### Post by raymondh on 2009-10-15
> **megaman2000 said:**
> Gparted isn't letting me touch the windows partition at all....Or am I doing it wrong?

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

Boot into the liveCD and access Gparted.  It ought to unmount partitions.  It also wouldn't hurt to double-check.  Rt. Click on partitions and if given the option to unmount, do so. 

In reference to your previous post, I just booted into my 9.04 liveCD and in step 4, I see the side-by-side option.

---

### Post by jimbo160 on 2009-10-15
I am very unfamiliar with ubuntu, and a lot of questions come about. When i surf the forum to find some answers, and you post makes me confused. I do not know about proportios, slides, and things you are talking about here. I made my ubuntu disc, and just tried ubunt from the disc before i decided i wanted to install. I have an older computer that has 1.24Gb, useing windows xp. When i decided to install, i just turned my computer on, and when windows finished loading, i put mu ubuntu disc in. After a moment, i was ask with 3 options to choose, one being to set up a dual boot. I new that was what i wanted, so, i clicked. I was ask to create a size for ubuntu, i made 8Gb, and added a username, and pass word, clicked install. It run a moment, ask me to reboot, and when started, give me option to choose windows, or ubuntu. Clicked ubuntu, and it comenced to downloading files, and everything i assumed it needed to run. After it got thru, i entered my user name, and password. My ubuntu loaded, i clicked my wireless network, it found, and i was on line........my question, did i do it wrong? are there things i need to do in order for ubuntu to work? If anyone understands what i am saying, please assist me.          Jimmy

---

### Post by jarame on 2009-10-15
> **megaman2000 said:**
> Installing 9.04 on a laptop with XP already installed on it. 

For some reason, I am unable to make a new partition even though there are 19 gigabytes free...it says they're all taken up by the windows partition :\


> **jimbo160 said:**
> I am very unfamiliar with ubuntu, and a lot of questions come about. When i surf the forum to find some answers, and you post makes me confused. I do not know about proportios, slides, and things you are talking about here. I made my ubuntu disc, and just tried ubunt from the disc before i decided i wanted to install. I have an older computer that has 1.24Gb, useing windows xp. When i decided to install, i just turned my computer on, and when windows finished loading, i put mu ubuntu disc in. After a moment, i was ask with 3 options to choose, one being to set up a dual boot. I new that was what i wanted, so, i clicked. I was ask to create a size for ubuntu, i made 8Gb, and added a username, and pass word, clicked install. It run a moment, ask me to reboot, and when started, give me option to choose windows, or ubuntu. Clicked ubuntu, and it comenced to downloading files, and everything i assumed it needed to run. After it got thru, i entered my user name, and password. My ubuntu loaded, i clicked my wireless network, it found, and i was on line........my question, did i do it wrong? are there things i need to do in order for ubuntu to work? If anyone understands what i am saying, please assist me.          Jimmy

Hello Jimmy & Megaman. I just partitioned my drive last night using a .ISO file and PowerISO program to install Ubuntu 9.04. I've yet to create a USB Stick, but my CD drive is broken so I can't help you out with the CD part. But when I partitioned my drive with the ISO program a window popped up telling me how much space on my HD there was, and I then could choose a certain amount of space to install Ubuntu on. I believe I chose 15 Gigs out 24 free GBs free space. Then I created my username and password, rebooted and then I was good to go. I plan to replace my Windows OS completely with Linux, so when I start that process I'll make screen shots for you. But that's the process I went through to get Linux.

If the CD/USB methods don't work you can always go through it the ISO way. I hope I helped you out somewhat ;)

---

### Post by raymondh on 2009-10-15
For Jimbo160 :

You did fine. You have a wubi-installed ubuntu.  That is one way to have ubuntu installed and working.  The other way is to have ubuntu in it's own partition.

In a wubi-install, Ubuntu resides AS A FILE within windows. Remember that as a "file" within windows, you have to keep windows healthy and defragged.

Here is the [wubiguide]("https://wiki.ubuntu.com/WubiGuide").

Happy ubuntu-ing.

---

