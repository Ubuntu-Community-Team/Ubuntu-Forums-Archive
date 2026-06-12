---
title: "Correct mount point on installation"
date: 2009-01-15
forum: Installation &amp; Upgrades
---

### Post by waketech66 on 2009-01-15
I have a 120g hd with xp (ntfs), 2 fat32 and a reiserfs partition. I have Linspire on the reiserfs partition. I want to install ubuntu on the partition where Linspire is. I have changed the size of the reiserfs partition to 22.5g and created a swap partition of 5 gig. Should I install ubuntu from running the live cd or should I boot the ubuntu cd and pick install? When I go to install ubuntu (from install menu on bootup) it gets to 'prepare partitions'. When I pick the reiserfs partition and click on edit partition, I pick use as:reiserfs journaling file system. When I go to pick the mount point, there are many options. Which one should I use? / or /boot or some other?
What I want when I am finished is this,  dual boot to ubuntu with the option to boot to xp if I want. Can someone please advise me on this.
thanks....Paul

---

### Post by estyles on 2009-01-15
Sounds like you're almost there.  Select use as /
This will install everything for Ubuntu under that partition.  You might want a separate /home partition - it depends on a lot of things.  If you're considering it, you can do a search for "home partition" and I'm sure it should be helpful.

Any particular reason you want to use reiserfs on / ?  From what I've heard, reiser is very good with lots of small, frequently modified files, which is why I use it for a /var partition.  I feel like there's a reason that /ext3 is the usual standard choice for /.

---

### Post by cariboo on 2009-01-15
Reiserfs is basically dead, the creator, Hans Reiser is in jail for murdering his ex-wife, so there probably won't be any more development.

Jim

---

### Post by estyles on 2009-01-15
dude - you're using a murderer's filesystem?

---

### Post by waketech66 on 2009-01-16
Thanks for the history lesson! This really all started because I was not happy with the default partitioning that ubuntu suggested. I want to replace linspire with ubuntu not put it on half of the xp partition. So I picked manual partition. Are you suggesting that I format the partition? If so then what file type? ONce that is done, then I am back to my original question, what do I do about a mount point. Should I use / or /root or what. I cannot go any further until I set this up. What should I do?
Paul

---

### Post by estyles on 2009-01-16
> **estyles said:**
> Sounds like you're almost there.  Select use as /

> I feel like there's a reason that /ext3 is the usual standard choice for /.


I think your answers are somewhere in there.

---

### Post by waketech66 on 2009-01-17
Hi
Well a successful install! From the manual disk partitioner I made the old linspire partition to be /ex3 and the mount point / as was suggested. The install went fine and I am now installing the 220 updates. 
thanks for the help
Paul just outside Toronto

---

