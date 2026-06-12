---
title: "joining ntfs and ext3"
date: 2008-12-25
forum: Installation &amp; Upgrades
---

### Post by admalledd on 2008-12-25
have been using ubuntu allot and love it! unfortunately, some programs i use require windows.(they kinda work in Linux)
recently i got fed up with my lack of HDD space and got a 500 Gb drive. my old drive is partitioned as such: [10 gb windows, 10 gb ubuntu, 30 gb share] because i don't use windows much, my new hard drive is for ubuntu! but, because i am no longer needing all of 10 gigs being unused on my current, i was wondering if there is a way to merge my 10 gb linux and 10 gb windows giving me (on my old drive) [20 gb windows, 30 gb share]

any ideas on merging the partitions?
i know i can get another 'drive' as windows sees it, but would rather merge it with my C:\

extra info(if needed)
install process went like this:
install windows to 10 gb partition, do all updates (up to SP2)
boot ubuntu live cd (8.04)
partition remaining into 10,30
install ubuntu to 10 gb
format 30 to ntfs

Thanks in advance for any help i get! go linux!

---

### Post by Partyboi2 on 2008-12-25
Once you have moved ubuntu over to the new hard drive and no longer need anything from your  old 10 gig ubuntu installation you can delete it and increase  your ntfs partition to use up the space. You can do this by booting a ubuntu live cd and opening gparted (System>Admin>Partition Editor) and delete your ext3 partition then use the resize feature to increase the size of your ntfs. Make sure  the partitions are unmounted before working on them and that you have backed up all your important stuff.

---

