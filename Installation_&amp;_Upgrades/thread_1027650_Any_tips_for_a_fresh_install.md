---
title: "Any tips for a fresh install?"
date: 2009-01-01
forum: Installation &amp; Upgrades
---

### Post by NEUR0M4NCER on 2009-01-01
So i've been using Ubuntu for a year & a half, and have learned a lot, but I keep seeing interesting posts about things like setting up /home as a separate partition and such.

I'm planning on getting a nice big 1.5tb drive next week, and want to put a fresh install of 8.10 on it (i've stuck with 8.04 'till now, after the upgrade nightmare last time). So does anyone have any tips for a better install? Is it worth keeping /home separate, or might it bork future upgrades?


Regards

---

### Post by Sealbhach on 2009-01-01
The idea of having a separare /home partition is that it preserves all your application settings e.g. your emails, desktop themes, bookmarks and msic library, documents etc. The /home and root partitions are usually formatted as an ext3 filesystem.

However, I understand that the next version of Ubuntu, Jaunty Jackalope, will support the ext4 filesystem, so for me, I will have to reformat my /home folder to upgrade to 9.04.

It is a good idea to have a /home folder, but we are coming to a change in filesystem so I don't know if it's worth it for you to do this if you intend to continue on to Jaunty.

However, it would be good to learn how to do it. What you do is select Manual Partitioning during the installation. There's some good screenshots of how to partition here:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)


.

---

### Post by wolfdale on 2009-01-02
For upgrading from Hardy to Ipex, I used the manual partition setting and keep my original root and home partitions and I just reformat and reinstalled.

I'm also sharing my HD with XP. I had some extra space and created FAT32 partitions (from the XP side) and used it for backing up my Linux data in case something went horribly wrong with my Ubuntu upgrade. This was a life saver. FAT32 partitions have a max size of 32GB so you may need to create several for large amounts of data.

---

### Post by NEUR0M4NCER on 2009-01-03
I really want to stay away from an upgrade (vs fresh install), due to the messy config of my drives (see [here](http://ubuntuforums.org/showthread.php?t=975366)). I've mucked about with the system so much that I don't think i'd know what to do if something went wrong - and I won't have a laptop for the next couple of months, so no checking the forums for a fix either...

TBH, it sounds like separate /home mounting may cause more trouble than it solves, so I think i'll just keep data on its own partition, and do a fresh install every six months (I may give the update route another go further down the line).

---

### Post by zvacet on 2009-01-03
>  it sounds like separate /home mounting may cause more trouble than it solves

having separate home is very good and practical thing.My home gone through upgrades,reinstalls,fresh install and allways remain the same.I will recommended to have one.

---

