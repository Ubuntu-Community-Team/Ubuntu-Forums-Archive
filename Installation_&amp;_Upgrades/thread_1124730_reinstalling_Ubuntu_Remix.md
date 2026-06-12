---
title: "reinstalling Ubuntu Remix"
date: 2009-04-13
forum: Installation &amp; Upgrades
---

### Post by SVWander on 2009-04-13
A few days ago I installed Ubuntu Remix on my MSI WIND laptop. I was so impressed with the interface when it was running live that I went ahead and installed it. However, I am having trouble with it and think the only cure is to reinstall the entire OS. The problems started with hard drive clicking (something it isn't doing now running URN live) strange behavior in Firefox, automatic update not working and other problems.

I ran a check disk off the opening menu on the USB drive and it found 1 error. So I downloaded another copy of the Remix and "burned" it to another USB drive. I did check disk again and 1 error was found. Now I don't know if the freshly download copy is okay or not.

What I would like to do is reinstall Ubuntu Remix to dual boot between XP and Ubuntu. I need to know whether I should use the installation USB drive or spend another hour downloading another copy. Most important of all I need to figure out how to delete the existing copy of Ubuntu Remix without messing up XP. There are lots of partitions on this disk and I am not sure what to do. Can anyone help me with these problems?

---

### Post by antikristian on 2009-04-13
Use bittorrent to download the image if possible, that will ensure that the image is allright once downloaded to your computer. 

And if you: 
-start the download with bittorrent
-wait a few seconds for the container image to be created 
-shutdown the bittorrentprogram 
-copy the corrupt image into the folder you are downloading to (replacing the unfinished image with the corrupt one) rename it if the name is diffrent
-And finally restart the torrent software

Then bittorrent will repair the corrupt image without downloading the entire thing all over again.

Clicking noices and corrupt images does sound a bit like a hardware issue though, maybe the hard drive is bust, or the memory... run memtest86 just to be sure about the RAM

---

### Post by SVWander on 2009-04-14
> **antikristian said:**
> Use bittorrent to download the image if possible, that will ensure that the image is allright once downloaded to your computer. 

And if you: 
-start the download with bittorrent
-wait a few seconds for the container image to be created 
-shutdown the bittorrentprogram 
-copy the corrupt image into the folder you are downloading to (replacing the unfinished image with the corrupt one) rename it if the name is diffrent
-And finally restart the torrent software

Then bittorrent will repair the corrupt image without downloading the entire thing all over again.

Clicking noices and corrupt images does sound a bit like a hardware issue though, maybe the hard drive is bust, or the memory... run memtest86 just to be sure about the RAM

I have been messing around with Linux for years so I am ashamed to state that I have never been able to understand bittorrent. I guess I will have to look into it again. 

The clicking and problems with software only shows up in Ubuntu. In Windows XP it works perfectly and in the Live Session of Ubuntu it worked well. Anyway, I will try messing around with bittorrent but I still have to figure out how to rid my hard drive of the Remix installation.

I was able to solve the problem by running Ubuntu Remix Live, installing partition software, deleting the partition with Ubuntu on it and reinstalling the operating system. There still was an error on the USB installation 'disk'as reported by the check disk in Ubuntu setup but it didn't seem to matter. Ubuntu Remix now runs quietly and is a must better interface for MSI WIND that XP. If it were not for needing MS Streets and Trips I would completely abandon XP.

---

### Post by odinb on 2009-04-18
> **SVWander said:**
> 
The clicking and problems with software only shows up in Ubuntu. In Windows XP it works perfectly and in the Live Session of Ubuntu it worked well. 


Could it be a driver issue? When running OS X on the wind, the clicking is caused by OS X trying to activate power management and is not able to do so.

See this: [http://wiki.msiwind.net/index.php/Stopping_hard_drive_clicking_(OSX](http://wiki.msiwind.net/index.php/Stopping_hard_drive_clicking_(OSX))

Looking forward to getting mine, ordered one today (this one: [http://snipurl.com/g6f55](http://snipurl.com/g6f55)). Planning on dual booting it between OS X and Ubuntu.

---

### Post by circut1 on 2009-06-18
Hi , am sort of a new ubuntu user. Have the desktop cd ver but only have my Inspiron laptop to work on. It all boots from the cd okay and runs but no network drivers. 
i found the link for notebook remix ubuntu , and have been trying to download it for days. Everytime it runs for an hour or so (maybe more) and then fails ??? Only get part of the file. So  *tried Bittorrent . Installed it and can download the cd version. But notebook remix ver *seems to be a whole  different install ( use jump drive to install it) and I want that for the computer I have. When I open a torrent file for REmix url , and try to start , bit torrent doesn't do anything. I waited about 5 minutes but no start???
What I am asking here , if you know, is , how do I get a good download of Remix ubuntu that installs to the thumb drive ? Or if it doesen't matter , do I just use the " alternate " ubuntu ver on cd that I can download ?
Thanks for any info you can provide. Really want to get networking with ubuntu.

---

