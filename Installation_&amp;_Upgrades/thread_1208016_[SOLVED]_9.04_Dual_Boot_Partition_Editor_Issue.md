---
title: "[SOLVED] 9.04 Dual Boot Partition Editor Issue"
date: 2009-07-08
forum: Installation &amp; Upgrades
---

### Post by Zizuph on 2009-07-08
Today I am installing 9.04 on a clean system with two SATA drives and XP installed on the main drive, with the second being used for storage.

I got the error "gparted can't resize partitions managed by windows dynamic disk", while attempting to allow gparted to resize the main drive.

I googled this error, which brought me to a lengthy 2007 post in these forums.  I then defragged and used Partition Magic from within XP to resize the partition.  No change.

Then I ran chkdsk /f on both drives.  No change.

Finally, and for the temporary purpose of installation only, I unplugged the storage drive, and everything worked just fine.

It should be noted that the contents of that drive were compressed under XP.  My guess is that gparted saw that and didn't like it.  Perhaps something which could be looked into.

Anyway, just posting this here, for anyone else who might be going through the same thing.

---

