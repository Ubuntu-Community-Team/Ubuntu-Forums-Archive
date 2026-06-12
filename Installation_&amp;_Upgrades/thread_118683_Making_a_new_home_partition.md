---
title: "Making a new /home partition"
date: 2006-01-17
forum: Installation &amp; Upgrades
---

### Post by Jessehk on 2006-01-17
I have a setup like this:

73 GB ntfs for windows
518 MB linux-swap
40 GB ext3 for /


To make upgrading disros easier, I'd like to make a /home partition from my / partition. 

I know how do to this, but I have a few questions about the affects/results:

1) Will anything on my Windows partition be in danger?

2) Will I have to make any changes to my setup, or can I just make the partition and reboot?

3) How much space should be allotted for / and /home?


Thanks greatly in advance, and yes, I am making a backup first. :)

---

### Post by earobinson on 2006-01-17
1) windows will not be in danger unless you edit the windows partition.

2) You might want to copy all the current files to the new partition (not 100% sure of this)

3) Check how much space you currently use and double it, do you save all your files to your desktop if then lots, you can always resize it later.

*extra points for pointing out that you will backup first*

Let us know how it goes never seen it done this way before, I always make my home partition with my first install.

---

### Post by lha on 2006-01-17
[QUOTE=Jessehk]I have a setup like this:

73 GB ntfs for windows
518 MB linux-swap
40 GB ext3 for /


To make upgrading disros easier, I'd like to make a /home partition from my / partition. 

I know how do to this, but I have a few questions about the affects/results:

1) Will anything on my Windows partition be in danger?

2) Will I have to make any changes to my setup, or can I just make the partition and reboot?

3) How much space should be allotted for / and /home?


Thanks greatly in advance, and yes, I am making a backup first. :)[/QUOTE]

0) Though you say you know how to do repartitioning, I want to point out you need a live cd (or something) to repartition. You should not try to repartition a drive which is in use. Because you say you are to make backups, I don't have to tell you to do that. ;) 

1) I'd say there's always risks when fiddling with partitions. You aren't doing anything to your Windows' partition, but there's only one partition table and it can get screwed. So, backups of files on Windows' partition are recommended. You can backup partition table and hope that if something goes terribly wrong, data on Win partition isn't overwritten and restoring partition table is enough.

2) You need to copy all files from old home to your new partition and edit /etc/fstab to reflect this change. Remember to keep file ownerships and permissions intact when copying.

3) My / has 7GB of total space, 1.6GB used. (I have /home, /tmp and /var on another partition and / is maybe a bit bigger than needed.) You can use
```
df -h
``` to find out how much space is needed for all files. Then
```
sudo du /home -sh
``` to find out how much space your /home uses at the moment. Subtract latter from former to find out the minimum you need for /. Make it atleast a couple of hundreds of MB greater than what it takes at the moment. You'll need space for stuff in /var and /tmp. 3-4GB will suffice if you don't  install much new software, but **don't make it too small**. I think it's worth waste 1GB too much to / than having to repartition to get that needed 1GB.

---

### Post by Jessehk on 2006-01-17
Okay, new plan. 

It would seem overly complicated to do this on an existing install, so I think that when
Dapper comes out, I will re-partition with a liveCD, and hopefully the installer will recognise my home partition, as I plan to overwrite Breezy with Dapper.

Will that work?

EDIT: And thanks to all of you for the advice!

---

### Post by Herman on 2006-01-17
There may not be any need to change your system, if you read these proposals for Dapper from the wiki:
[https://wiki.ubuntu.com/AutomaticUpgrade?highlight=%28apt-get%29%7C%28upgrade%29]("https://wiki.ubuntu.com/AutomaticUpgrade?highlight=%28apt-get%29%7C%28upgrade%29")

In addition to that, recently, a new stable version of GParted on its own live CD has been released just a few days ago. It makes it easy for anyone to do things that used to be a little advanced before. I have been testing it, and I can easily shrink even a reiserfs partition with it, make a back-up copy of the complete installation (including tweaks and added software), and paste it at the end of my hard disk as a back-up.
 Then I resize my working installation again afterwards and use it however I like.
All I need to do is make sure I keep a simple back-up of my regular files and e-mails. If I 'bork' my installation, I have a spare one sitting there on the last few Gigs of the hard drive waiting, all setup and tweaked, ready to go. It only takes a few minutes to put the GParted live-0.1 CD in and copy the backup back to the currently 'borked' install and I'm ready to go again! 
It really makes the need for multiple partition installs redundant for single user home desktops unless you have special requirements.
Try out GParted on its own CD for yourself, second sig link under here, the .iso for it is only about a 34 mb download, you won't regret it, I think it's great! :D (Herman)

---

### Post by Jessehk on 2006-01-17
[QUOTE=Herman]There may not be any need to change your system, if you read these proposals for Dapper from the wiki:
[https://wiki.ubuntu.com/AutomaticUpgrade?highlight=%28apt-get%29%7C%28upgrade%29]("https://wiki.ubuntu.com/AutomaticUpgrade?highlight=%28apt-get%29%7C%28upgrade%29")
[/QUOTE]


Those suggestions look great! What are the chances that they will be implemented by the time Dapper is released?

---

### Post by Sef on 2006-01-17
Herman:

When I clicked on your GParted link, I was taken to your Ubuntu Dual Boot website.

---

### Post by Herman on 2006-01-18
>  Those suggestions look great! What are the chances that they will be implemented by the time Dapper is released? jessehk, I have no idea, but I'll bet there is a pretty good chance they'll do something like that. Even if they don't, we can still dist-upgrade if we want, but it will probably depend each individual user to make up his or her own mind what will be easier and what we think is best for us. 

Sef,
>  When I clicked on your GParted link, I was taken to your Ubuntu Dual Boot website. Thank you very much for letting me know, I have that fixed now I think. :D (Herman)

---

