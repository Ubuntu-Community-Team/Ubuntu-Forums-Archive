---
title: "Need help with a xp/ubuntu dual boot"
date: 2009-07-04
forum: Installation &amp; Upgrades
---

### Post by Bearbuntu on 2009-07-04
First of all want to say hello to you all and this is my first post.  I hope to learn alot about ubuntu hear on the forum.  I did some searching before posting and could not find the info i needed so I am sorry if this question may seem a bit nooobish of me.

A little background to the problem.  I had my 500gb hard drive in my desktop set up to dual boot xp and windows 7 beta.  I allocated 50gb to xp and 50 gb to Windows 7 and the rest stores all my files, movies, pictures and music.  I recently ran into a problem where malware tookover my xp partition and decided after a couple days of trying to fix to just reinstall the OS.  So what i did was took one over my collection of random xp cds and installed it on my partiton that had windows 7, I never used in anyways.  So i am all set with a fresh xp partiton.

Now I am trying to intall ubuntu 8.10 over the original malware infested xp partition.  I booted the ubuntu cd i made and made it all the way to the partion screen and got scared, this is my first time working with any linux based OS.  I decided to select manual partition and saw my 3 partitions and tryed deleting the original partiton and installing ubuntu on the free space and it doesnt seem to be working.  I honesly really have no idea what to do from there.  Rather than poke around and chance messing something up i decided to come here.  I just want to avoid loosing all my pictures and movies on my large partition.  At the moment i have no way of backing it up.  If somebody could help guide me it would excellent.

---

### Post by earthpigg on 2009-07-04
you want the target partition for ubuntu to have "/" as its 'mount point'. 

its filesystem can be ext3 or ext4 - if you think 4 is a cooler number than 3, pick that. think is 3 cooler than 4, pick that. ext4 is wave of the future, ext3 is tried and true.

if you aren't 100%, you can hit 'print screen', and attach the screen shot here on the forums and we can take a look to make sure you aren't doing anything silly before you hit 'apply'.

edit: resizing, creating, or deleting partitions is rather risky. simply reformatting an existing one, not so risky. naturally, you may still end up S.O.L. if the power goes out mid-partition.

---

### Post by earthpigg on 2009-07-04
i just realized something: since you are coming from dual boot windows, you probably do not have a 'swap' partition do you?

you have 2 options:

1) install without a swap partition. this will be simpler, and thus this is the safest thing for keeping your music/files/etc. downside: if you are running ubuntu and run out of RAM, your computer may lock up. you will have to keep an eye on that.

2) delete your target partition, create a new 'swap' partition of 2gb or so, and use the remainder for the 'ext3/4' partition with '/' mountpoint.


if you have 2 or 3 gigs of ram, and dont plan on doing anything crazy (virtual machines, 3d rendering) then you could potentially actually be perfectly fine without a swap partition, thus making #1 more appealing of the two options.


in an ideal world, you would be able to back up your music and other stuff and we would not need to be so worried about being careful.

---

### Post by ~sHyLoCk~ on 2009-07-04
Pick the drive where you want to install ubuntu. Partition it to keep meinimum 15Gb and mount it as " / " and the rest of the free space as you want,e.g. for /home. You may also like to have a swap space, since you didn't mention your RAM, I'd say just keep 1Gb.

---

### Post by earthpigg on 2009-07-04
here is an example gparted screen i found on google image search:

[http://www.techotopia.com/images/4/41/Ubuntu_linux_gparted_main.jpg](http://www.techotopia.com/images/4/41/Ubuntu_linux_gparted_main.jpg)

leave everything about your windows and multimedia partitions alone, dont worry about their mountpoint or anything.

he has a 400 meg swap partition in that example.

---

### Post by Bearbuntu on 2009-07-04
thank you so much for the quick replys  What i did go ahead and do just to play things safe is order a case for a hard drive i have laying around and will back up my files.  I should be doing that anyways.

---

### Post by Bearbuntu on 2009-07-04
Also, Since I have never run ubuntu outside of a live cd I think i need to do a bit more research.  The way I had my system set up before this I was able to select between xp(Cdrive) and windows 7(Edrive)  on boot up and they would run independently of each other and I was able to access my files from drive F.  Am I able to do this with xp and ubuntu

---

### Post by earthpigg on 2009-07-04
> **Bearbuntu said:**
> Am I able to do this with xp and ubuntu

yes, but they wont be called "C drive" or any other letter from within ubuntu. toss that entire way of thinking out the window :D

when you go to places-> computer, you will see all the partitions listed there. easiest way to recognise them is by the size.

if you are interest in knowing, however, the linux equivalent of c:\, e:\, etc is this:

first physical hard drive is sda. partitions on it are sda1, sda2, etc.

next one is sdb. partitions are sdb1, sdb2, etc.

edit: 

windows will _not_ be able to read your main ubuntu partition. 

ubuntu _will_ be able to read your main windows partition.

_both_ will be able to read your giant shared partition.

if you dont empty the trash when you log off of ubuntu, windows will see some funky folder that is your ubuntu trash.

if you dont empty the recycle bin when you exit windows, ubuntu will see some funky folder that is your windows recycle bin.

in both cases, you can ignore it... or delete it, if you want to empty the trash/recycle bin from the other OS.

---

### Post by presence1960 on 2009-07-04
for convenience sake when you use gparted you have the option of using "Label". Type in a name for that partition, then when using file browser in Ubuntu that name will identify the partition instead of just the size ( ex. 63.2 GB media) see my screenshot:

---

