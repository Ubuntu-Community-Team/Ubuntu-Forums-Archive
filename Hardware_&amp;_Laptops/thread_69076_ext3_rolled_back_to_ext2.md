---
title: "ext3 rolled back to ext2"
date: 2005-09-25
forum: Hardware &amp; Laptops
---

### Post by art2003 on 2005-09-25
I have 2 IDE hard drives.
The second one /dev/hdd1 has just one large partion (160 gigs) that I mount on /home
This partition has been working happily for months with EXT3

Today when booting ubuntu informed me there was a problem with the journal and the partion was converted to ext2 in a few seconds. 

Naturally it didn't mount automatically as ext3 anymore and I was very worried.

I tried mounting it as ext2 and ... it works!

So my question is ...

What is the difference in practical terms between ext2 and ext3?
Given the size of the partion, should I seek means of transforming it back to ext3 or should I leave it as ext2?

---

### Post by mlomker on 2005-09-25
> What is the difference in practical terms between ext2 and ext3?
Given the size of the partion, should I seek means of transforming it back to ext3 or should I leave it as ext2?

Nothing but the journal.  If the journal is corrupt then it'll operate as ext2.  

A journal is a transaction log that every write to the disk is recorded in prior to actually being written to the drive.  If the system dies prior to the save being completed then the journal can be 'replayed' and your drive will not become corrupted.  Ext2 is prone to damage when you have a power outage/hit your power switch due to a lock-up, etc.

**sudo tune2fs -j /dev/hdd1** to add a journal, thereby making the drive ext3.

I personally prefer reiser, which is an alternative journaling filesystem.  You'd have to reformat the drive to use it, though.

---

