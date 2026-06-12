---
title: "Where are the partitionson Mythbuntu 8.10?"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by dishbert on 2009-02-26
I installed Mythbuntu 8.10 and it seems to work fine.  It's the only Linux OS installed on a 250 G drive, but when I look at that drive there is no swap, only a single ext3 partition.  Also, I thought that Mythbuntu was going to install a none-ext3 file system for storing video files, but I don't see that either.

I'm in the habit of backing up all my partitions with Acronis from the XP side, but Acronis says "Some partitions contain errors and can only be backed up sector by sector.." when I try to back up the Mythbuntu drive.  Acronis has worked perfectly with other Linux partitions before.

I installed with a download, checked the md5sum was OK, but the CD I burnt never completed the "Check CD" test.  The progress bar finished, but I never got an "All OK" message.  The CD worked fine live, and the install went OK.  I deleted a few old partitions and installed manually into half of the unallocated space, using a / mount point.  Looking at this partition from my other Ubuntu partition it shows as /dev/sdb6  ext3 mount point = /media/disk.

As I say, it seems to work fine.

---

### Post by zvacet on 2009-02-27
> I deleted a few old partitions and installed manually into half of the unallocated space, using a / mount point.

That is the reason why you don't have swap.You didn't made partitions on that unallocated space.You can use live Cd to shrink existing partition and make space for swap.Size of swap partition depends of ram you have,but I don't think you will need more then 2GB of space max.It is a good thing to have separate home partition and if you want to create one [here]("http://www.psychocats.net/ubuntu/separatehome") is very good guide.

---

### Post by dishbert on 2009-02-27
Thanks for the reply zvacet.  I've looked around and Mythtv System info says the system is already using a swap file of 1.3 G.  This is the exact size of a swap file on another HDD that was created by a previous Ubuntu installation.  

Everything seems to work fine.  Do you see an advantage in creating a second swap file on the same device as Mythbuntu?

---

### Post by zvacet on 2009-02-28
Sorry for late replay.If you allready have swap there is no need for another one.

---

### Post by dishbert on 2009-02-28
Thanks again zvacet.

---

