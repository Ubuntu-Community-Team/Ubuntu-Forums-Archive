---
title: "is my HDD broke?"
date: 2008-02-10
forum: Hardware &amp; Laptops
---

### Post by TeasesTheBear on 2008-02-10
Hi there!

Recently i noticed, that my fileserver's RAID5 is running degraded. After reading the according log(s), i found out, that one dirve is out of sync, since mdadm didn't mount (i guess, that's not the correct term in this context, but you know what i mean ;)) it at startup for a while. Now, after a failed resync i did some research on how to diagnose HDDs.

dd if=/dev/sdb of=/dev/null
resulted in I/O errors. As well, badblocks told me i had plenty of bad blocks...
I did dd and badblocks on /dev/sdb and /dev/db1 to check for HDD and filesystem blocks (i did' get that right, didn't i?). Always the same results.

So, my questions are:
Is this enough information to know my HDD s broke?
Or does it make sense to hope, that reformating that one drive and resynching it with the array is enough?

I would have tried that myself already, but i was asked what i wanted to do with those four spare disks during ubuntu server installation. I told the installer to prepare it for raid, but what it did exactly, i don't know. Wether my HDD is broke or not, do you know, what the "RAID filesystem" is, and how to (re)create it?

Thanks in advance,
Teases the bear


P.S.: RTFM-Answers are ok, when you tell me where the M is ;)

---

### Post by TeasesTheBear on 2008-02-11
Ok, i guess i did some wrong asumptions.
There is no "raid filesystem", just a flag to set on a filsystemless partition. I always thouhgt there is no filesystem without a partition and vice versa.
I managed to add the "broken" disk to the array again with no errors

It seems that the bad blocks resulted from a bad recovery attempt or single raid drives a cluttered by bad blocks by nature ...

anyhow one question remains: How would i know that my drive is broken and needs replacement?

---

