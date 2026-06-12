---
title: "Recurrent fsck errors"
date: 2011-12-31
forum: Hardware
---

### Post by Actorclavilis on 2011-12-31
Hello all,

Just yesterday my laptop running 11.10 lost power and as a result was shut down unexpectedly. When it started up it attempted to run fsck on my ext3 main partition, but failed and mounted it read-only. I plugged the drive into a Mac and tried to run a e2fsck -v on the partition, which started to report "short read", "zero dtime", "incorrect refcount", and other such errors. I answered "yes" to all "fix?" questions but it reported "Filesystem still has errors" at the end of the run. I ran it again, and received even more such problems but e2fsck exited normally and I was able to boot. I did not find any missing data.

Several hours later my kernel panicked and I was forced to restart, where I encountered the same fsck error. Currently I am running e2fsck on the Mac again and getting more errors and "fix?" prompts which weren't there the first time around. 

I know that this sounds like a hardware error, but my disk is only three months old so I'm suspecting something else may be the problem with my OS. If it is a hardware error I'll send it in for warranty replacement but I selected ecryptfs when I installed Ubuntu so I think I may need to use the actual OS to recover my data. Question is, does this sound like a hardware or software error; if software, how do I fix it, and can I recover an ecryptfs volume on a different OS?

Thanks in advance,
--Actorclavilis

---

### Post by 2F4U on 2012-01-01
Since subsequent fsck runs still return errors I would indeed suspect a hardware problem. Depending on how you are using your laptop, a laptop hdd is much more likely to fail than a desktop hdd, since the laptop is moved around. First thing I would do is make a backup as long as you are able to access the data.

---

