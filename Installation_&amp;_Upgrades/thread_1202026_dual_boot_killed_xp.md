---
title: "dual boot killed xp"
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by happygizmo11 on 2009-07-01
I set up a dual boot with ubuntu and xp. I got ubuntu working fine. When I restart my computer and choose xp from grub it goes to a black screen that says just starting up. It never makes it to windows. I am not sure what to do. I couldn't find any clear reason as to why this is caused. If any of you could tell me that would be great. I am looking for a way to fix this. I have an xp install cd I just don't know what to do with it. I have gotten into the repair console and run fixboot, but that did not help. I have an external hard drive that will hold every single windows file I have if reinstallation is necessary, I can just install then paste in all my other files somehow so it will be the exact same as before can't I? Also I do not know exactly how to reinstall it with the cd so simple directions would be great. I am not the most computer savvy but I know a little. Basically what causes the error, how do I fix it, and how do I go about doing it?

---

### Post by Geoff918 on 2009-07-01
Did XP ever do a chkdsk operation when you first attempted to boot into it? Had you defragmented your hard disk before partitioning the hdd?  In my experience Windows (both Vista and XP) are usually confused a bit by the new dimensions of the drive they find themselves on and run a chkdsk to make sure everything is okay. You may want to use XP install disc as a rescue item and run a couple of system checks.  Don't panic. I had this same situation happen to me with a friend's machine. GRUB may be misconfigured, or there could be something else amiss. Sometimes reinstalling Ubuntu with special attention to the partitioning setup works without too much hassle. I won't tell you to do so because if something else is wrong that could result in data loss, or sadly more data loss if something was done incorrectly the first time.  First step I'd take is to back up all of the data you can get access to, then go from there with whatever seems right. Easiest, but potentially dangerous options are to use either the XP or Ubuntu CD to correct the MBR.  Also, is your dual boot something you did with partitioning software like PartitionMagic in Windows, or something you did with Ubuntu's install program?

---

### Post by happygizmo11 on 2009-07-01
I backed up everything I feel is important, and that is all of windows. I have not backed up my ubuntu stuff because I don't feel that is of that much importance. I used gpartition or whatever it is called on the live cd to create a space for ubuntu to install to. I defragmented a couple of days before the install. If anyone could tell me at least a first step to getting it back up and running that would be awsome.

---

### Post by Geoff918 on 2009-07-01
I would try the XP install disc, and then select "rescue system", it may be able to fix your MBR (master boot record).

---

### Post by tvtech on 2009-07-01
Try booting into windows again but hit F8 to go into the safe mode selection screen.  It should boot into safe mode even if the check disk is borked.  You can even boot into safe mode command prompt and run chdsk manually "highly recommended."  I had this problem today on a virtual disk that I used parted magic to resize.  

The moral of the story just use clonezilla parted magic is borked.

---

### Post by happygizmo11 on 2009-07-01
where would I find rescue system? I have booted from it a few times and never noticed that option?

---

### Post by tvtech on 2009-07-01
> **Geoff918 said:**
> I would try the XP install disc, and then select "rescue system", it may be able to fix your MBR (master boot record).

I wouldn't touch your windows install cd it's evil and filled with evil spirits stay away far far away.!

---

### Post by tvtech on 2009-07-01
> **happygizmo11 said:**
> where would I find rescue system? I have booted from it a few times and never noticed that option?

I think you hit R  when it asks if you want to install. but like I said pull that damn thing out and hide it some place safe.  once your in the rescue mode you can do a chdsk from there too. 

But do what I told you hit F8

---

### Post by happygizmo11 on 2009-07-01
I unfortunately cannot even get into windows at all so F8 did not work but I tried it I am currently rinning chkdsk off the installation cd I and typing this on my phone which explains the misspellings and poor grammar. Anyway I couldnt find the recovery thimg by the name I was given but I foumd the auto system recovery if that is what i should run. Thank you guys for helping this far hopefully we can figure this out. chkdsk just finished and said it found one or more errors but nothing else and didnt do anything about it.

---

### Post by Geoff918 on 2009-07-01
Hmm, I'm trying to think. I can agree with what was posted by the other individual, BUT there is a recovery option, pay attention to the screens where it says something to the effect of "Install Windows XP" there are some other options, like "Run Recovery" or something to that effect. I am positive of this, I did it maybe a month ago because I had some similar issue. Mine was a MBR issue. XP did fix it. Also, I had success with reinstalling a linux partition (in this case it was SUSE) with the problem and configuring GRUB through that. You can manually edit GRUB, but I'm not really ready for that. I have a book that explains the commands, but that's still fairly foreign to me as a novice linux user.

---

### Post by happygizmo11 on 2009-07-01
well I ran fix mbr and now it won't even open GRUB so i am gonna try reinstalling ubuntu

---

### Post by happygizmo11 on 2009-07-02
I gave up and reinstalled windows now I uave a backup of my old xp partition using an external hard drive can i just copy and paste those files or do I need to do something else

---

