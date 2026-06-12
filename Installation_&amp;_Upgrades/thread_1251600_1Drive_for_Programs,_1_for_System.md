---
title: "1Drive for Programs, 1 for System"
date: 2009-08-27
forum: Installation &amp; Upgrades
---

### Post by kmclaren on 2009-08-27
I have 2 hard drives in my computer and I would like to run a dual boot with Win XP and Ubuntu.  I want to partition each drive in half so that I have 4 partitions, two with 40gb and two with 60gb.  I want to install the system files for each OS onto their own 40gb partiton and then have the program files for each OS on their own 60gb partition.  This way the program files are pulling from one hd and the system is pulling from the other.  Hopefully by doing this I can get my old computer to be a teeny bit faster.

I know how to create the partitions and how to seperate the files in XP but with Ubuntu I have absolutely no clue how to seperate those files.  So, my question is, how do you place the system files on one partition and have all of the program files on a second partition.

Also, I'm thinking that 40gb for the system and 60gb for the programs may be a little bit excessive for ubuntu, how much do they normally take up?  I need space for my games on XP so if Ubuntu isn't very hungry then I will partition more for Windows.

PS I am open to any suggestions on other ways to divvy things up.

---

### Post by raymondh on 2009-08-27
Since you're open to suggestion ;)

Drive 1

XP
Ubuntu
- root (/)
- home (/home) > where your confg settings, files, etc reside
- swap

* the value of having /home separate from root (/) is that should you need to reinstall ubuntu, you install and reformat just root hence keeping your config files and settings intact.
* Ubuntu does not care whether it resides in a primary or logical partition ... does not care for boot flags ... is not picky whether installed first or last.

Drive 2

Data, pics, music, videos, movies, etc .... in NTFS format so that both windows and ubuntu can access.

---

### Post by presence1960 on 2009-08-27
> **kmclaren said:**
> 

I know how to create the partitions and how to seperate the files in XP but with Ubuntu I have absolutely no clue how to seperate those files.  So, my question is, how do you place the system files on one partition and have all of the program files on a second partition.

You don't. Linux doesn't put all the files for software in a "Programs" directory as windows does. Different parts of software are in different directories.

---

### Post by kmclaren on 2009-08-27
So, I should just leave ubuntu in it's own partition? That sounds easy enough.  How big should I make the partition for ubuntu? Is 40gb plenty?

About using the second drive as a media drive, I have an external hdd (1tb) that I use for media right now so I don't need it for that.  I just knew that I could split the program files away from windows to speed it up.  I was thinking that I should do the same to Ubuntu but I guess it is fast enough without it.

Thanks for the help.

---

### Post by presence1960 on 2009-08-27
> **kmclaren said:**
> So, I should just leave ubuntu in it's own partition? That sounds easy enough.  How big should I make the partition for ubuntu? Is 40gb plenty?

About using the second drive as a media drive, I have an external hdd (1tb) that I use for media right now so I don't need it for that.  I just knew that I could split the program files away from windows to speed it up.  I was thinking that I should do the same to Ubuntu but I guess it is fast enough without it.

Thanks for the help.

I would try what raymond suggests. For Ubuntu: root (/), swap and /home partitions. / 10-15 GB should be plenty, swap = to installed RAM if you want hibernation, the rest to /home. If you need help with setting that up post back.

---

### Post by kmclaren on 2009-08-28
> **presence1960 said:**
> I would try what raymond suggests. For Ubuntu: root (/), swap and /home partitions. / 10-15 GB should be plenty, swap = to installed RAM if you want hibernation, the rest to /home. If you need help with setting that up post back.

And how do you force it to do these things? I got the partitioning part down but how do I make ubuntu use it as you said?

---

### Post by presence1960 on 2009-08-28
I would set up the partitions before installation. Then when you install choose the manual option (see screen shot below). Then highlight each partition one at a time and click edit. set the parameters: for / set Filesystem ext 3 or ext 4, tick the format box and set mount point to /.

For swap set the filesystem to linux-swap.

For /home set the filesystem as ext 3 or ext 4. Tick the format box. Set mount point to /home. Proceed with the installation

---

