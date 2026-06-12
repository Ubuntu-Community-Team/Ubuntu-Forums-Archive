---
title: "[SOLVED] Big Mistake In Partition Editor"
date: 2008-03-14
forum: Hardware &amp; Laptops
---

### Post by volkswagner on 2008-03-14
This user NEVER can leave well enough alone.  I was in the process of reclaiming some hard disk space.  Previously had two partitions /sda9 and /sda10, containing old Ubuntu file system and home partition.

In partition editor I deleted the partions, and created one new partition from the new free space.  I did not see where I could create a new mount point.  I mistakenly chose to create a new volume name.  Whoops!

When I go back into partition editor I see my whole hard drive as unallocated space.
This machine is a dual boot, winxp, UUE 1.6.

I am currently still logged in UUE.  I can browse all partions except the newly created.  I can no longer see the old ones, although don't care about them.  

I don't want to restart until I can get some advice what to do.

all partitions contain about 60gig of OS, and Data.

Can I fix this big mistake without loosing data?

---

### Post by ebe0 on 2008-03-14
I think your best bet would be to take back-up of all your critical data which are still accessible before trying any thing else.

found this link - [http://www.linux.com/articles/56588](http://www.linux.com/articles/56588) ... see if it helps.

If you find a solution to your predicament please share with us.

All the best.

---

### Post by sfink16 on 2008-03-14
You could try one of these tools:

[http://www.diskdoctors.com/software/linux-data-recovery/utility.asp](http://www.diskdoctors.com/software/linux-data-recovery/utility.asp)
[http://www.data-recovery-software.net/Linux_Recovery.shtml](http://www.data-recovery-software.net/Linux_Recovery.shtml)

I accidentially format my entire HD when installing Ubuntu and used Active@Undelete to recover my Windows XP files on my PC.  

It worked well!    I would think that the Linux tools will work well also.

Steve

---

### Post by volkswagner on 2008-03-14
I am in the process of backing up data.  
Is there anything I can do to undo my mistake?
Is there an option such as making a backup of /etc/fstab, other files, then rewriting after boot?
All my information is intact now.  I don't know what will happen after a reboot.  

Is there anything I can do prior to reboot?


:confused:

---

### Post by volkswagner on 2008-03-14
Google CAN be your friend.

Here is how I solved:
[LIST=1]
[*]sudo apt-get install testdisk
[*]sudo testdisk (was prompted sytems disks need to run in root)
[*]Analyze disk
[*]first showed as raw disk (diagnose/analyze cant remember)
[*]Magic showed all my partitions first showed a bootable
[*]Recreate partition table
[*]Exit
[*]Reopened gparted all my partions showed up
[*]Restart sytem to take effect of testdisk
[*]all is good!

[/LIST]

Hurray for testdisk and its creators!  Helping dumb folks like me!  :lolflag:

---

