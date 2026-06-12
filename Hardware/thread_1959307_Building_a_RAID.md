---
title: "Building a RAID"
date: 2012-04-15
forum: Hardware
---

### Post by Messyhair42 on 2012-04-15
I'm thinking of rebuilding my computer and including a RAID 1 as my primary HD. Storage has gotten so cheap I think it's feasible. Since Ubuntu 12.04 comes out soon I was thinking of starting there (my current HD has failed and I want to start with a LTS). a few questions first.

1. Does RAID reliably offer consistent data mirroring? I'm not concerned about speed, more concerned about stability.

2. Does Ubuntu support RAID systems?

3. Will the rest of my current hardware work with a RAID? I built a middle of the road system 2.5 years ago (Intel Core 2 Duo, Intel DG43NB MB)

---

### Post by gordintoronto on 2012-04-15
I'm pretty sure that the answers are: yes, yes, yes. 

My personal approach is that RAID is one more thing that can go wrong, and I will live with manual backup.

This: [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID) 
may be out of date, but still is worth reading.

---

### Post by Messyhair42 on 2012-04-16
In the event of a drive failure, what has to go into replacing it and the backup system? if I remove a RAID drive and plug an identical drive in its place will backup be automatic or is a lot of work involved? considering the cost of data storage today it seems reasonable for me.

I've been using manual backup since I built my desktop and I have data spread across four different devices and it's hard to keep track of what's where. my most important stuff is copied to everything so I'm not worried about it. simpler, widely available data i've been less consistant about backing up. I don't stand to lose a lot from my drive failure but it'll take time to replace.

Edit: after reading your link I've learned that you need the alternate installation CD, I've used them before so that isn't a problem. I like having my installation separated by partitions ( /,/tmp,/usr,/var,/home); is this still possible with this method?

---

### Post by Messyhair42 on 2012-04-17
Doing some research through official Ubuntu documentation leaves me wondering; what notifications does Ubuntu provide whena drive fails under RAID.? I can't find a definitive answer. and what is the recovery procedure if you have to replace a drive?

---

### Post by Messyhair42 on 2012-04-24
bumping b/c I'd like a couple of my questions answered. I need to make a decision before I buy hardware.
First, can you separate partitions like I used to have under a RAID (/,/home,/usr,/tmp,/var are all separate)
Second, are there notifications about a drive failure and what is the procedure if you do have to replace a drive?
Thank you, any help is appriciated.

---

### Post by ahallubuntu on 2012-04-24
Ubuntu has some ability to tell you when a drive is failing or at least has experienced errors - it's called S.M.A.R.T., and it's built into almost every hard drive (and can be used in Windows or any other OS).  But that has nothing to do with RAID.  You can use S.M.A.R.T. with or without a RAID.  S.M.A.R.T. isn't foolproof either; Google has released studies showing that S.M.A.R.T. can't be relied upon to predict imminent drive failure.

I concur with gordintoronto's approach:  I have used RAID in the past, but I rely on good old-fashioned backup these days instead of RAID.  A RAID MIRROR provides you ONLY one benefit: protection against drive failure.  It doesn't help you with file system corruption, accidental deletion, etc.  So you still need a backup scheme in place even if you have a RAID.  And S.M.A.R.T. is very useful (even if not foolproof) in my experience in monitoring hard drive health in any scenario.

My backup scheme (since you may ask?) is to backup data files (not the operating system) on a file level on two separate devices, either using rsync or rdiff-backup (which is rsync but with differential backup).  "Differential backup" means changes are saved since my last backup.  If I backed up last week and then delete a file the day after and backed up again last night, and then today realized I deleted that file, my simple rsync backup won't help me - but an rdiff-backup would have kept a copy of the file at each point, so I'd be able to go retrieve it.  You can setup rsync and/or rdiff-backup to run automatically, every day, several times a day, whatever you want.

For my operating system partitions (Ubuntu, Windows, etc.), I backup the partitions as image files.  I put my operating systems on separate partitions from my data files, so the OS partitions are small and the image files are also not that big.  Having an OS partition backup just saves me the time of needing to re-install it from scratch in case of a crash.

If you do file backups regularly, say every night, you can lose at most one day's worth of files.  So if your hard drive fails on a day you do a lot of work and saved a lot of new files to your hard drive, you can curse yourself for not having had a RAID, since you lost that day of work.  If you can live with that scenario, don't bother with the RAID - just use a reliable backup scheme that protects your against file system corruption, accidental deletion, and hard drive failure.

---

### Post by ahallubuntu on 2012-04-24
To answer your other question: yes, you can use any partition scheme you wish with a RAID - it's  mirrored so it doesn't matter. 

Here's a little primer on using RAID in Ubuntu:

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

---

### Post by sezession on 2012-04-24
Yes, some of us are the "link building crowd", and some of us are the "SEO" crowd. 

I agree with you.

Lets just agree to disagree. The two groups will never come into being "one", so its pointless to discuss. Its not just the link stuff that the two groups disagree with. Its over many different things. 
Àêòóàëüíûå [Âåêòîðíûå èçîáðàæåíèÿ](http://www.vectory.ru/) áåñïëàòíî 
[Ëîæêè-ïëîøêè](http://www.vectory.ru/index.php?productID=276)  
[Ïåòðèêîâñêàÿ ðîñïèñü](http://www.vectory.ru/index.php?productID=11486)
 ðåãèñòðèðóéñÿ è ñêà÷èâàé

---

