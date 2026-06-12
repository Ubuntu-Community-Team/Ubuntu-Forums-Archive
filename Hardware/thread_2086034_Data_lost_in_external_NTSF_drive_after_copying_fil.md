---
title: "Data lost in external NTSF drive after copying files from Ubuntu"
date: 2012-11-19
forum: Hardware
---

### Post by jnmdon on 2012-11-19
Hi everyone,

I was trying to copy a folder of about 80 MB into my external 1 TB drive to back up when the problems started.

First of all, it did not start to copy right away, but stayed for a couple of minutes with a "Preparing to copy" sign (even though it was only 80 MB).

After some minutes it started to copy with an extremely low speed, and took more than 10 minutes to copy the 80 MB.

When I tried to access the copied folder in my external drive it took a while until it finally entered, only to show that it was completely empty (there was already data in that folder before I started copying).

I also noticed that another external unit appeared connected but not mounted (volume of 4 GB). When I tried to access it, it gave an error something like:
Error mounting:  /dev/mmblk08: can't read superblock

I unmounted the external drive and then this 4 GB unit was also gone.

I mounted again the external drive, and I can still access most of the folders, but many of them are now empty, and the data is gone.

Besides this, a couple of new folders appeared, whith names such as Thrash, and so on.

I have no idea what should I do:confused::confused::confused::confused::confused:. Appreciate your help in this.

Greetings

---

### Post by ahallubuntu on 2012-11-19
First of all, check the S.M.A.R.T. status of the drive.  Maybe it has begun to fail.  In Ubuntu, install smartmontools (or GSmartControl for the graphics version) and check the drive's Attributes.  If the raw number of pending sectors is more than 0, you've got problems.

Otherwise, connect the drive to a Windows machine and run chkdsk on it.  That may fix the filesystem and allow access to your data again.  I'm not sure if you'd be able to boot a Windows disc to run chkdsk on an external drive.  Could be that a Windows 7 disc might work for that; XP probably not.

---

