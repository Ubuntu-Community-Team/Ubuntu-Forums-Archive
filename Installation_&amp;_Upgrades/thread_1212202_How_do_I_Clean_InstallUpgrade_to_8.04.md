---
title: "How do I Clean Install/Upgrade to 8.04"
date: 2009-07-13
forum: Installation &amp; Upgrades
---

### Post by Sherina on 2009-07-13
I've been using 7.10 for a while and now I feel its time for me to upgrade to 8.04. Currently I dual boot 7.10 with windows xp. How can I do a clean install upgrade on my dual booted system without erasing my windows xp partition? 

Thank you

---

### Post by merlinus on 2009-07-13
At the partitioning screen, use manual and make certain not to select your xp partition.  It should find the existing ubuntu partitions, and you will need to select to use them as ext3, and the mountpoints.

If you have room, you may wish to create a separate /home partition as well, if you do not already have one.

And back up important data first!

---

