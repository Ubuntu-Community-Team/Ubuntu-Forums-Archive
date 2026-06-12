---
title: "ext2ifs stoped working after upgrade from Hardy to Intrepid"
date: 2008-11-03
forum: General Help
---

### Post by eks on 2008-11-03
Hellos,

I've update from Hardy to Intrepid this weekend but [ext2ifs]("http://www.fs-driver.org/") stoped working. I've tried to unistall and install it from scratch without success. It actually installs and map the ext3 formated partitions, but when I try to open them inside windows exploder it simply asks to format them. :-#

Anyone every saw anything like that?


eks

---

### Post by eks on 2008-11-03
Ok, just found my own solution with some searching

> 
C:\Users\amministratore\Desktop\incoming>mountdiag U:
The volume has an Ext2/Ext3 file system, but the Ext2 IFS 1.11 software did not
mount it because there is at least one incompat feature flag set. The Ext2
IFS software does not implement:
* needs_recovery *
Here we have an Ext3 file system which has transactions left in its journal. A
pure Ext2 driver must not access such a volume which is in that state (to
prevent data loss!).
You may solve it by mounting it on Linux (which has a kernel with Ext3
support). Be sure that you cleanly dismount it, before you shutdown Linux.
After that the Ext2 IFS software should be able to access the volume.


mountdiag.exe was at [http://www.fs-driver.org/troubleshoot.html](http://www.fs-driver.org/troubleshoot.html)

But why is Intrepid leaving drives mounting??

---

### Post by nikopol on 2008-11-05
it seems to only do that with my home and / partitions - my external hard disk is fine. I'm wondering if they work as they are not hardwritten into the fstab file?

---

### Post by Kulgan on 2008-11-14
Also having this problem. Unsure whether it has anything to do with upgrades (I only just got the computer), but the external hard drive works fine with the fs-driver. 

I have another ext3 partition that has never been mounted on Ubuntu, and will try that. 

I tried the diagnistics tool, to no avail. I don't know if I'm doing anything wrong (not all that familiar with Vista, after all), but it seems that I don't have required permissions... While being the only account on the computer...


Edit:
The non-ubuntu related partition doesn't seem to work, either. So why does the external drive work..? Interesting...

---

### Post by psusi on 2008-11-14
Did you cleanly shut down Ubuntu?  You didn't hibernate did you?

---

### Post by Kulgan on 2008-11-14
Don't think I've hibernated at all since getting this computer. Which was three days ago, so I hope I'd remember.

Ubuntu seems to shut down nicely, though I haven't checked any logs. Any idea where I should check for that?

I was planning to install Hardy on the spare partition, to see whether it was the installer that hosed it (used the 8.10 installer to make the partition in the first place), but that will have to wait till I have time. Which I don't at the moment. Horrible IB :/

~K

Edit:
Just noticed that the "spare" partition was in fact being mounted by Ubuntu 8.10. I had set it to mount "in case" I ever needed it. So that's still a likely option.

---

### Post by kacian on 2008-11-26
Hi

Inodes that are larger than 128 bytes are not supported, so you have to resize inodes to 128 b.

---

### Post by Kulgan on 2008-11-26
Cool, that's the problem identified. 

So how is this done? 
:D

---

### Post by nikopol on 2008-11-26
Backup all of the data away from the partition you want to access then format it 
```
mkfs.ext3 -I 128 /dev/your_device
```
After you have this new parition, transfer the data back across.

THIS IS A DESTRUCTIVE FORMAT SO YOU MUST BACKUP BEFORE FORMATTING THE PARTITION

---

### Post by Kulgan on 2008-11-26
K, thanks ;)

I'll give that a go, when I have time... Get the impression I've said that before, though :roll:

---

### Post by Kulgan on 2008-11-26
Yup, tested with an empty partition. It works indeed. Yay!

Thanks, nikopol! :)

---

