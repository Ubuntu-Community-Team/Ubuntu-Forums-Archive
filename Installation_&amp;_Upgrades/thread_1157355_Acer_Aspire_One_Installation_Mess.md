---
title: "Acer Aspire One Installation Mess"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by Holden99ca on 2009-05-12
Hi,

I hope you'll forgive me but I'm reposting this as I only got one answer last time which didn't really solve the problem.

I'll try to make this short. A quick scan of other posts seems to have revealed other similar problems.

After a successful experience with Ubuntu on my home desktop I decided to make my Acer Aspire One a dual-boot machine. I'm kind of regretting it. I installed as per instructions, i.e., download the file, confirm the hash, make a bootable USB drive, boot from the drive, install.

During the install process I'm quite sure it never asked me anything about how to partition the drive. It's now acting very buggy including things like: evolution just spins but consistently fails to load, firefox's back button is always grayed out and the google search engine does nothing after you enter data into it. Last, and perhaps most importantly, it reports no space available in the "/" drive when it runs update. Indeed when I load up the Home directory it reports 0 bytes available.

How did this happen and what can I do about it? All suggestions are welcome and appreciated.

Holden

---

### Post by sir_nasty on 2009-05-12
what size is the hdd?  If you have the space you can expand the root partion using partition manager and a live cd.

---

### Post by Holden99ca on 2009-05-12
Hmmm...good idea. I'm going to try that. Thanks! I realize there would be some measure of speculation here but do you think there's a chance it would rectify some of the buggy behaviour?

---

### Post by wabbalee on 2009-05-12
Have you considered using manually configuring partitions? I think that is one safe way to go as I explain [here]("http://ubuntuforums.org/showthread.php?t=1148982") in post #7. The problems you are describing seem like a lot more went wrong somehow.

---

### Post by mrtomservo on 2009-05-12
Most of the buggy operation you are experiencing is from a lack of hard drive space.  Partitioning the hard drive properly and setting up the swap partition properly should solve all of the problems you listed.  Make sure you've backed up recently, if you mal-partition you will lose your data.

---

### Post by Holden99ca on 2009-05-13
OK thank you. I'm trying to re-partition using the Live CD but it won't let me make ext3 larger even if I have unused ext3 space right next to it.

---

### Post by Holden99ca on 2009-05-13
Wait. Spoke to soon. Had to turn swap off in order to do it. Taking the plunge now.

---

### Post by Holden99ca on 2009-05-13
This seems to have been a successful strategy. Thank you to everyone for their suggestions.

---

