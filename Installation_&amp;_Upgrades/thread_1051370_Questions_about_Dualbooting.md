---
title: "Questions about Dualbooting?"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by Paperfairy on 2009-01-26
I am looking to generally clean up and organize the entirety of my computer's hard drive. I want to repartition the hard drive, but as far as backing up and choosing file systems, I'm generally unsure as to how to proceed.

At the end, I would like to have three partitions; one for Windows Vista and its required files. The  second for Intrepid and its required files, and the third being a space for documents, music and videos accessible from both operating systems.



The computer I am using came pre packaged with Vista, with the hard drive partitioned into general space, and what appears to be a recovery/backup drive. Upon installing Linux, I split the general space drive and created the Linux partition.

I suppose my real questions are:

How do I go about backing up each of the partitions in order to maintain most, if not all settings/programs to restore of reinstall of Vista/Linux?
What file system do I use for the shared space? I know fat filesystems are generally obsolete, and Windows cannot read ext2/3 (in least for me), so that leaves ntfs?

Thanks.

---

### Post by Hobgoblin on 2009-01-26
Ubuntu is fine reading and writing to NTFS and there are EXT2/3 drivers available for Windows.

So it's your choice.

---

### Post by Mark Phelps on 2009-01-27
How are you planning on reinstalling Vista?  Do you have a DVD? (I would guess not).  

Your machine came preloaded, with a recovery partition.  If you have vendor-provided "recovery" media, when you go to use it, it will most probable competely reformat your drive (removing all but the recovery partition) and reinstall Vista to set the machine back to the state it was in when you unpacked it.

---

