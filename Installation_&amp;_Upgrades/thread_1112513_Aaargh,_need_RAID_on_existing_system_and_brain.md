---
title: "Aaargh, need RAID on existing system and brain"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by ToshiBoy on 2009-03-31
Ok, I've spent a few weeks trying to understand this but the more I read the more confused I get.

What I've got:

Server running Ubuntu Desktop edition (because I needed a head) on one HDD, SATA 500GB, plus one vacant HDD 500GB sitting in the box unused.

What I want:

RAID 1 or 5 over the two harddrives with the same system that I already have. I have a spare 500GB harddrive I could put in if required (eg for Raid 5). I need to be able to have one drive fail and not loose data.

What's the best approach? Should I just take the HDD with the working system out, put the spare HDD in, set up the RAID and then move the system back over? Or is there a way to just RAID the existing system with the extra harddrive?

Any thoughts much appreciated

Cheers

Toshi

---

### Post by WilliamJenningsBryan on 2009-04-01
[http://ascendwiki.cheme.cmu.edu/Installing_Raid_1_on_Existing_Ubuntu_Server](http://ascendwiki.cheme.cmu.edu/Installing_Raid_1_on_Existing_Ubuntu_Server)

This tells you how to do it, but trying to add it to the existing system might be more trouble than its worth. If I were to personally set this up, I would use the spare HDD and move it over.

---

### Post by ToshiBoy on 2009-06-09
> **WilliamJenningsBryan said:**
> [http://ascendwiki.cheme.cmu.edu/Installing_Raid_1_on_Existing_Ubuntu_Server](http://ascendwiki.cheme.cmu.edu/Installing_Raid_1_on_Existing_Ubuntu_Server)

This tells you how to do it, but trying to add it to the existing system might be more trouble than its worth. If I were to personally set this up, I would use the spare HDD and move it over.

The more I read, the more I think I agree with you. New HDD... set up RAID1 over the two new disks, then move everything over to the RAID... makes sense. :-) Thank you

---

### Post by ToshiBoy on 2009-07-02
Well, the main HDD died, so in the end I did set up 2 new HDDs and did it from scratch. Works like a dream. :-)

---

### Post by papenpj on 2009-07-02
I have found it easier to setup raid from the start rather than implement it. Lol helped a friend setup a server for his work.... they really like the "inexpensive" part of raid. they had three 80GB sata drives. because the one they originally had was full we removed everything important, and 140GV raid 5 for data. 9GB raid 1 for system files, 1 GB raid 1 for the swap.

Altough in retrospect we really didn't need to raid 1 accross all 3 drives because the important stuff is on the raid 5 which only allows 1 lost drive. but, eh I wanted to get out of there after 7hrs of working,

---

