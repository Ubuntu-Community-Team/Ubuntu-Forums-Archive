---
title: "How much space should I leave for each partition?"
date: 2009-03-25
forum: Installation &amp; Upgrades
---

### Post by aceplayer97 on 2009-03-25
I want to install Ubuntu but I also want to keep a separate partition for Windows XP which I can use for gaming. How much space does a Windows XP install take up? How much space ahould I leave for Windows XP? I have a small 60 GB hard-drive :(. 

And this is just a random question but I noticed that when I use Ubuntu I have a smaller battery life then when I use Windows XP. Usually on Windows XP I have 2.5 to 3 hours of battery life whereas in Ubuntu my battery just dies in 40 minutes. Is there anyway I can fix that?

---

### Post by Major Groove on 2009-03-25
I am doing something like that on a 60Gb right now.  I've got 50 for XP, 9 for Ubuntu and 1 for the swap partition.

Of course it depends on your purpose.  In my case the computer will be a roaming wireless access PC.  Since I will need Office and the like, I left plenty of room for that.  The extent of the gaming will be Minesweeper.

As for the battery life, I get a message in Ubuntu that says (basically) "your battery is going to die" - not an exact quote.

On this machine I don't really care, though.  I can always plug it in.

---

### Post by TiredBird on 2009-03-25
I have been dual booting for several years now although it is getting where I rarely use XP anymore.

As has been said, it depends a great deal on how you will use it. 

Personally, I generally set up the XP install on a 5GB partition. (XP itself will generally run in less than 3GB but with all the extras that get added to your system, first by the manufacturer, then clicking yes to all of the many things that are 'recommended' on the internet, can chew up many gigabytes of space.) That partition gets formatted with NTFS and should have enough room for any XP type programs you use regularly.

Then I usually throw in a 5GB Fat32 partition. I use that as space for any additonal win32 programs that didn't go in the NTFS partion, and for data needed for any of the win32 programs. (I put the 'My Documents' folder on that partition. 

The reason for the Fat32 partition is that it is usable by both XP and Linux without any special softare. It gives you a place to put things that you want to access from both systems.

I would stick in a 1GB partition for Linux swap. You'll probably need 4 GB for your Linux partition. (Ext3 is a good format.)

You can use the other 45GB anyway you choose. Put in a separate partition for your Linux 'home' directory. (I use ext3 for this) That will make it easier to upgrade distributions in the future. 

You might even want to leave some of the space unformatted. That way you can turn it into FAT32 or Ext3 or both as needed.

I personally have one machine that only has a 20GB harddrive. It has XP and two Linux distributions and works just fine. At last check, I was only using about 50% of the drive.

Hope this helps!

---

### Post by Mykle87 on 2009-03-25
Dual booting is a great idea. I just set up a dual boot last week. I split my 40 gig hard drive right in half for ubuntu and xp. I'm not sure what kind of gaming you are going to be doing but when I look at some games I have like steam (counter-strike and left 4 dead) and command and conquer red alert 3 that is a total of 15 gigs. Modern games take up tons of space quickly. If you want to do heavy gaming, I would give more space to xp. Good luck.

---

