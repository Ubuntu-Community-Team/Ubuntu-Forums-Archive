---
title: "NEWBIE partitioning drive"
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by JBL121 on 2009-04-19
I am trying Ubuntu for the first time.

Using a AMD 1600+ that was running WIN XP pro on a 160gig hd.

MY HD was partitioned into 1 primary drive and 3 logical drives.

I want to use this computer for only Ubuntu and booted to the CD.

I get through everything fine until step 4 of 7.

It asks me for partitioning info. 

How should I partition my drisk drive for Ubuntu when I am going to use it for internet and to try it out to see if I like it.

I get this box with a Before and after picture of my HD in Blue/Green and orange,

The after is all blue and says Ubuntu 8.1 100% below it. Then below that is Guided - use entire disk, SCSI (0,0,0) SDA 163.9GB ATA and below that it says Manual.

Help, I want to get this installed.

THanks

Joe

---

### Post by drs305 on 2009-04-19
Welcome to the ubuntu forums.

The 'all-blue' option will place ubuntu on the device and wipe out everything else.

The Guided with the blue/orange will allow you to have multiple partitions and you can adjust the partition sizes (I think you can even slide the bars) to adjust the size.

Manual partitioning is very useful if you have already partitioned your drive in preparation for the installation.

Here is the ubuntu documentation with good graphics:
[https://help.ubuntu.com/community/GraphicalInstall]("https://help.ubuntu.com/community/GraphicalInstall")

Added: If you are up to manually partitioning your drive, this site has some good advice for planning your installation:
[_http://www.psychocats.net/ubuntu/partitioning_]("http://www.psychocats.net/ubuntu/partitioning")

PS: To try ubuntu, you can run it from the LiveCD without installing it.

---

### Post by upchucky on 2009-04-19
ok first i noted that you said you wanted to try ubuntu to see if you like it. I suggest that you set it up to dual boot your existing windows and ubuntu even though you said that you only want the pc to have ubuntu.

with a dual boot you can still have windows and be able to learn linux at your own pace, there is a learning curve and everyone loves to learn new stuff right?

now since I may have convinced you to do a dual boot the first thing is to prove to your self that the ubuntu live cd you are going to use to install will indeed function with your system.

boot the pc using the live cd, if the live cd boots to a graphical display, then you will be able to actually do an install to the hard drive either with no problems at all, or a couple of minor problems that are easily fixed.

the version 8.10 is not a long term supported release thus it may or may not work well with some systems.

8.04 is a long term release and is use-able without problems on most systems.

if the 8.10 live cd does not boot to a graphical display, then you should use the 8.04 live cd since you are "trying" ubuntu. the less fussing you have to do when learning the better chance you have to actually learn.

8.10 usually has to be adjusted to run on many systems.

since you are "trying" leave about 40 gig for windows, defrag the windows partition before doing any partiton adjusting and make sure you only do one partition job at a time to avoid confusing the partitioner.

ubuntu only needs about 10 gig including the swap partition, the swap should be about half the size of your system ram size.

I allow 25 gig for windows, 25 gig for ubuntu, 1 gig for swap, and the rest of the drive for a separate home partition.

the separate home partition is very handy cause you can save all your files and settings there and they will be safe even if you ever decide to reinstall. or make an error that cripples the install.

so you can do a manual partition, read each step, google what you do not understand, and lastly give linux an honest run, it is a very powerful os and is only limited by the person using it.

---

### Post by JBL121 on 2009-04-19
Thanks for the info.

I have Ubutu running on the machine but I dont know where to see how my drive is set up. (My Computer in XP). With Ubutu installed can I start Gparted and decrease the origional partition to say 20 gb and breakup the rest into other partitions?

If so I see drives on linux sites such as "home/swap/...etc".

What drives do I need.

In Xp I had a System(C:) for XP, Applications (D:) for apps and Data (E:) for data.

Started with 160 gb before operating system install.

THanks for any information.

Joe

---

