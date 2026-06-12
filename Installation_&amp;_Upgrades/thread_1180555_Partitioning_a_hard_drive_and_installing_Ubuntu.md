---
title: "Partitioning a hard drive and installing Ubuntu"
date: 2009-06-07
forum: Installation &amp; Upgrades
---

### Post by stisoulreaper on 2009-06-07
I apologize if this topic is covered elsewhere, but I haved searched through the forums and have been unabe to locate the answers I was looking for.
 
I recently replaced my computer's harddrive with a 320 GB one. I had planned on installing both Ubuntu and Windows XP on the harddrive, and leaving some room blank for other purposes (I was considering installing another os, maybe the windows 7 beta). I had planned on allotting Windows XP 100GB of the harddrive, and another 100GB to Ubuntu and leaving 100GB free.
 
My first question is regarding my division of the partitions, as I am relatively new to this, I'm not sure if I am dividing the harddrive intelligently: I.e., is 100GB for each OS enough, is 100 GB free overkill? Would it be wiser to allocate more to one and less to the other?
 
My second question concerns the partitioning of the harddrive. How do you suggest I set up the partitions? I know XP needs to be a primary partition. I would like to reserve at least one primary partiton (for any future OS), leaving a primary and an extended. Which Ubuntu programs should I assign to each; I.e., root, /home, swap partitions. And finally, which Ubuntu programs should be assigned a partition, and how much space should I assign each one?
 
Thank you very much for the advice and assistance.

---

### Post by Sef on 2009-06-07
> My first question is regarding my division of the partitions, as I am relatively new to this, I'm not sure if I am dividing the harddrive intelligently: I.e., is 100GB for each OS enough, is 100 GB free overkill? Would it be wiser to allocate more to one and less to the other?

I would allocate 15 GB for XP and 10 for Ubuntu.

 
> My second question concerns the partitioning of the harddrive. How do you suggest I set up the partitions? I know XP needs to be a primary partition. I would like to reserve at least one primary partiton (for any future OS), leaving a primary and an extended. Which Ubuntu programs should I assign to each; I.e., root, /home, swap partitions. And finally, which Ubuntu programs should be assigned a partition, and how much space should I assign each one?
 

XP - Primary (15 gb)

Rest - extended

Ubuntu - root (10 gb)

Swap - 1 gb

Future os - 10 gb

Home - rest of disk

---

### Post by -kg- on 2009-06-07
What you're asking is hard to determine.  It would depend on your individual circumstances and what you anticipate doing with your computer.

Are you a (Windows) gamer?  You will need some space for your games if you are.  I run MS Flight Simulator X, and the installation folder alone takes up 14.7 GB.  Add a few more games, a collection of videos, and a decent music collection (mine is 24 GB and growing) and of course the space required for the OS itself, and the question quickly becomes:

"100 GBs?  Are you *kidding*?!":p

However, if you're only going to run and store a few things under Windows (and I won't even mention browsing the web and email...those are things best done with Linux), then 100 GB is likely *more* than enough...too much, even.

I don't know the space requirements for Windows 7, but if it's anything like Vista, you'll need a bit of room for it.  I know Vista has a rather large footprint.

100 GB is almost more than you need for Linux, but considering you might want to play around with other distros of Linux, it might not be enough, depending on how many other installations you might want to play around with and what you want to do with your main installation.

Browsing the web and email takes almost no room, and it will be desirable to use Linux for this, since it is almost immune to virus and trojan infections.  You *can* store your music and video files under Linux, though it is not necessary as Linux will access ntfs or fat partitions fine.

I personally would go ahead and use a 100 GB primary partition for XP.  I'm thinking you should use the XP installation disk create the partition and either set or limit it's size or resize it after the installation is complete.  This will create a MBR and partition table in the proper area and put XP's bootloader into it.

If you have Windows 7, install it next, which will likely include XP in it's bootloader.  I'm not sure whether you need to hide the XP partition from the Windows 7 installer.  I know that you needed to with Vista so it wouldn't convert the partition to it's version of ntfs and render XP inoperative.  There should be further instructions on this elsewhere.

Then you need to launch GPartEd from whatever Live CD and create a 100 GB Extended partition around unallocated space.  You can install Ubuntu on Logical partitions within it.  Whatever space requirements you determine you'll need is how large you'll need to make these partitions.

> Which Ubuntu programs should I assign to each; I.e., root, /home, swap partitions. And finally, which Ubuntu programs should be assigned a partition, and how much space should I assign each one?

Now what you're asking here I'm not quite sure.  What programs are you talking about?  If you're talking about how much space you should assign to each partition, that again depends on what you anticipate installing.  Minimally, you will need a "/" (root) partition and a swap partition.  If you just create a root partition, /home and other directories will be included on it.

If you decide to create a separate "/home" partition, your /home directory will be mounted from that partition instead of the root directory.  Same goes with any other directory that you decide to create a separate partition for.

I see that Sef has already put an answer forward.  I would agree with most of what he says, except for a couple of things.  First, again depending on what you anticipate doing with your computer and the various OSes, I would think I'd go with a little more than 15 GB for XP, and most certainly more for future OSes.  The reason I say the second is that you mentioned Windows 7.  I know that Vista needs *way* more than 10 GB to install into, and I would assume that Windows 7 is not far behind it.

I would also adjust root up a bit, say to 15 GB at least.  Root is where you install software, and if you think you might install quite a bit of software you might want some more room.  I had a 15 GB root for my Hardy install, and I had 9 GB of files in root.  Under that scenario, 15 GB was about right.

Quite a few considerations, which is why I said at the beginning that such a thing is hard to determine.  Not to worry, though.  Partition resizing is relatively easy to do, though it is much more time consuming after you have data in the partitions.  If you find that you need more space in one partition and less in another, the sizes can be adjusted later.

Good luck!  Sounds like you're going to be having all kinds of fun the next few days/weeks!  (At least, *I* find doing things like that fun! :p )

---

### Post by stisoulreaper on 2009-06-08
First, I would like to thank you both for your insight. I have found your suggestions to be most helpful.
 
>  
Are you a (Windows) gamer? You will need some space for your games if you are. I run MS Flight Simulator X, and the installation folder alone takes up 14.7 GB. Add a few more games, a collection of videos, and a decent music collection (mine is 24 GB and growing) and of course the space required for the OS itself, and the question quickly becomes:
 
"100 GBs? Are you kidding?!"
 
However, if you're only going to run and store a few things under Windows (and I won't even mention browsing the web and email...those are things best done with Linux), then 100 GB is likely more than enough...too much, even.

 
I don't really play games on my laptop all that often, simply because I've never gotten around to buying many (and I'd have to check if it could handle more demanding games). That being said, I do play Starcraft occasionally, and I am interested in expanding my game library.  On top of that I also have a few thousand songs, and a few dozen movies in my collection. I had previously kept these stored on an external as my old hard drive was only 100GB, but the external died a while ago. I still haven't decided if I want to replace it.

 
>  
Now what you're asking here I'm not quite sure. What programs are you talking about? If you're talking about how much space you should assign to each partition, that again depends on what you anticipate installing. Minimally, you will need a "/" (root) partition and a swap partition. If you just create a root partition, /home and other directories will be included on it.

 
At this point I was asking if it were advisable to assign directories besides root, /home and swap their own logical partitions. I had read elsewhere that this was a good idea, but as the installer displayed several other directories, I am unsure of which, if any, I should partition.
 
Thanks again for the help!

---

### Post by Bucky Ball on 2009-06-08
Get out a piece of paper and a pencil and start planning. Think about exactly what you are going to need. Write partition names (and separate disk names if you have them) on a piece of paper and allocate a size next to them until you've divided up your available disk space.

 As mentioned, this is a personal, custom thing you can design to fit your requirements.

One thing: In an extended partition, you can have as many Logical Drives as you like (partitions).
Two thing: If you don't have and extended partition, you can get four partitions on a single drive.
Three thing: If you like fishing videos, for example, and have a lot that equal quite a few gig, make a partition for them. Thinking about things this way makes it easy to selectively backup and backup generally.

```
/
/home
/fishingvids
/swap
```

In other words, use the default ones in the installer or make your own and call them what you want, but definitely:

```
/
/home
/swap

```
Good luck.

---

### Post by Polaris96 on 2009-06-08
First off, If you want a windows partition, I would cold install Windows onto the empty drive first.  The Win installer soesn't like sharing (surprise, surprise).  After that, load al the windows crap on that you'll want (for me it's autoCAD, B2SPICE, and FSX).

After you have that loaded up, you can use windows explorer to see how much space you have left.  This is where the advice you got before comes in handy, but you'll already have some idea of where you're at because your utilities are loaded.

Then use the Live install CD to do the partition magic, add grub, add ubuntu, etc, etc, etc.

So far as multiple partiions go, there's a lot of strong opinion.  Here's what I use:

/boot i keep on a 100Mb ext2 partition.  This is because there used to be problems booting from RAID arrays and I like RAID.  ext2 is great for small partitions like 100Mb  btw

/Var I keep on its own 3Gb partition.  This is because /Var get a lot of traffic and I used have a slick 15k SCSI U320 drive that was perfect.  Now that my whole system is SCSI Raid, I saw no reason to change things.

/home is nice to keep on it's own partition striclty for an added layer of abstraction from your system files

I used to keep /opt on its own partition when I compiled a lot of source code, but if you're using apt you probably won't need to.

PCs run really fast now and raid is working good, so the only real need for this kind of thing is data abstraction if you're really into security.  I keep doing it from force of habit.  Hope this helps

---

### Post by Therion on 2009-06-08
I've never understood all the hand-wringing over how to partition a hard drive.  With 320GB hard drive you've got an insane amount of space to play with. 

Keep it simple...

Split the drive down the middle and give half to each OS.  The default partitioning schemes for both OS'es will be fine for the typical user and if for some reason, six months down the road, or whatever, you find you need to adjust the partitioning scheme, fire up a gParted LiveCD and adjust the partition(s).  Why all this fuss and bother??

But again, that's me and I don't like to complicate things unnecessarily.

---

### Post by stisoulreaper on 2009-06-08
Thanks for the help, everybody. I just have one more question for you all. How should I divide the Extended partition among the linux directories? Most of you touched upon this- How many GB's should root, /home, swap, etc. each be given?

---

### Post by merlinus on 2009-06-08
You might refer to sef's post earlier in this thread....

---

### Post by ManiDhillon on 2009-06-08
May be it can differ from person to person but I share media partitions and have standalones only for OS installation.
Like 30 GB for Win XP
Then 50 GB for Visuals(pics, videos)
Then 50 GB for Music
Then 30 Gb for keeping softwares/deb files or for saving my html work
Then 10 Gb for Ubuntu jaunty
Then 1 Gb for Swap

Rest of hard disk is free I use it to test other Linux distros!

And I am sharing the Visuals, Music and Others files partitions in both XP and Jaunty.

---

### Post by stisoulreaper on 2009-06-08
I read sef's post, and it was very helpful. I simply didn't understand the wording the first two times I read it (I can be a little thick sometimes). Thank you for drawing my attention to it again, as I realized that I was misreading it.

---

### Post by stisoulreaper on 2009-06-08
Thank you all for your advice! I greatly appreciate the assistance, and you have helped me resolve this problem

---

### Post by merlinus on 2009-06-08
Excellent!  Happy ubuntuing, and post back if you experience other difficulties.

---

