---
title: "Upgrade and save home dir"
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by jetsaredim on 2009-10-20
I want to reinstall my system, but need to save my home dir.  I have just enough disk space that I can run the installer and have it partition my hard drive and put the new install on half and keep the old install on the other half (with enough space to xfer all the data).  Is it possible to then re-size the main partition (and fs) and re-claim the old os partition once the files have been transferred?

Basically, just wondering if this will mess up my os at all to resize the partition like this...

---

### Post by drs305 on 2009-10-20
Yes, you can do it this way. The expansion to recover the entire old space may take some time, and you always risk the loss of data whenever you change partitions. 

Here is the link to a post I wrote about expanding the / partition. Most of it applies to your situation.

[http://ubuntuforums.org/showthread.php?t=1219270]("http://ubuntuforums.org/showthread.php?t=1219270")

Would both the new and old be on primary partitions? If one is on a primary and the other in an extended it will require a few more steps.

After you have expanded the new partition I would advise checking the fstab and menu.lst settings and UUIDs before you reboot to make sure they still point to the correct location.

Added: Another option is just to make a /home partition at the 'far right' of the partition, reinstall the OS using all the remaining space.

---

### Post by jetsaredim on 2009-10-20
Yes, both primary.  I'd rather like to not lose the data if possible, so maybe this isn't the best idea.

---

### Post by drs305 on 2009-10-20
> **jetsaredim said:**
> Yes, both primary.  I'd rather like to not lose the data if possible, so maybe this isn't the best idea.

Data loss is very rare but it can happen. The second option would minimize the risk, since you could copy your /home (and data), verify it was intact, then perform the reinstall, then copy back if you didn't want the separate /home partition.

The main thing to make sure of if you do this is that you designate a separate /home during the (manual) partitioning setup and DO NOT FORMAT /home during the installation.

---

