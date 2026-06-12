---
title: "fails to load on Dell 2600 server"
date: 2006-07-28
forum: Hardware &amp; Laptops
---

### Post by jmirick on 2006-07-28
I have a couple of Dell 2600s, I'm test loading on one of them.  The load gets to trying to partition and create, and it fails about 15% of the way through and just says, "failed to create file system."  When it tries to go back a step, it hangs up attempting to analyze the current partitions.

System has Red Hat EL4 on it right now, which runs (ran?) fine.

Partitioner sees:  SCSI 72.7 GB MegaRaid LD0 Raid 5 (its 3 physical drives), 69356R

Anybody have any idea what's wrong?  Its all hardware RAID, the system shouldn't even see it.

Thanks . . .

---

### Post by rbalfour on 2006-07-28
Use the Dapper Desktop LiveCD and check the drives with Gnome Partition Editor, That should give you an idea on how Ubuntu is seeing the drives.

---

### Post by jmirick on 2006-07-28
/dev/sda1     ext2            66.29 GB             boot
/dev/sda2     extended         1.43 GB
/dev/sda5     linux-swap       1.43 GB

sda1 line has a warning flag on it, which opens a window saying,

"unable to read the file system
"did you install the correct plugin for this filesystem?"

---

### Post by jmirick on 2006-07-28
The hardware boot says its a  perk4/Di RAID.
The drives are Seagate ST336753LC @ 35 GB each

How would I load another plugin for a file system?
Is there an issue with how large the partition is?

Update:  regarding the last issue -- partition size, I reset the main partition to be only 25GB, about 40% of the total available, and it appears to have been successful.

So can I go in later and assign that remaining disk space to another partition and hence access it?  I'm really unfamiliar with how Linux would do this, I'm an experienced newbie in this area (meaning I've loaded a couple of desktops with Ubuntu and that's about it.

---

### Post by rbalfour on 2006-07-28
sda1 should be ext3
You can assign the free space to another mount later. work on / and swap.

---

### Post by jmirick on 2006-07-28
I _thought_ it should be ext3.  A friend says that there's a formatting option when the RAID is configured that asks what operating system will be using it, he thinks he selected Windows, so maybe that's a reason it selected ext2; I'm not familiar enough with the whole thing to know.  RAIDed systems are always issue-laden, in my opinion!

Thanks for your help.

---

