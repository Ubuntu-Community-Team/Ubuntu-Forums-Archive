---
title: "urgent help needed xfs cannot read superblock"
date: 2007-01-22
forum: Hardware &amp; Laptops
---

### Post by edemark on 2007-01-22
Hi 
I would need some urgent help. I had an emergency shutdown and now the system is unable to load my home directory that is in /dev/hda3 with xfs file-system. I use ubuntu dapper and now i am on ubuntu edgy live-cd.

How can i get all my data back
please help

when i try to mount /dev/hda3 i got the following message>

sudo mount -t auto /dev/hda3 /mnt/hda3
mount: /dev/hda3: can't read superblock

xfs_check gives this

sudo xfs_check /dev/hda3
ERROR: The filesystem has valuable metadata changes in a log which needs to
be replayed.  Mount the filesystem to replay the log, and unmount it before
re-running xfs_check.  If you are unable to mount the filesystem, then use
the xfs_repair -L option to destroy the log and attempt a repair.
Note that destroying the log may cause corruption -- please attempt a mount
of the filesystem before doing this.

but of course i cannot mount it.

Is there any other way to repay this log?

xfs_repair gives this error 

sudo xfs_repair /dev/hda3
Phase 1 - find and verify superblock...
Phase 2 - using internal log
        - zero log...
ERROR: The filesystem has valuable metadata changes in a log which needs to
be replayed.  Mount the filesystem to replay the log, and unmount it before
re-running xfs_repair.  If you are unable to mount the filesystem, then use
the -L option to destroy the log and attempt a repair.
Note that destroying the log may cause corruption -- please attempt a mount
of the filesystem before doing this.

Shall I just go forward with the -L option? Would that mean that i will lose data?
What is actually corruption means here?
Is there any other way to get out my data first in some safe way?
Actually this is a hp nx 9010 notebook

Please help

---

### Post by edemark on 2007-01-22
Partially it is a bump 

But on the other hand some advances. I have read on an other forum (google helped) that i can mount this filesystem with -o ro,norecovery option. That works, at least i am now trying to save my valuable data.
After I will try xfs_repair

but still help is needed to find out answers to the questions of the earlier post

thanks

---

### Post by edemark on 2007-01-25
ok so to finish up this thread

After saving all my data i issued the xfs_repair -L command then it recovered i guess all my data (i think this as there were no files in lost+faund and those files that reported error when i was making the back up are there and work). Then i removed the user directory cdeated on my / partition (as my real user dir. was no mountable) when i was trying to log in without superblock on hda3. Then I rebooted and now everithing works just like before.

---

