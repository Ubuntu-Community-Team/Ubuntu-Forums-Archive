---
title: "Must RAID apply to entire drives?"
date: 2009-07-20
forum: Installation &amp; Upgrades
---

### Post by funnyav on 2009-07-20
I've been playing with this idea in my head, that I could have a Raid 0 partition for the OS and a Raid 1 partition for my home partition, using only two drives.

Can it be done?

---

### Post by kidders on 2009-07-21
Hi there,

You can make RAID arrays out of pretty much anything ... eg files, disk partitions, storage devices on other computers, RAM, etc. What you're describing would be slow and unreliable, but from a purely technological perspective, easy to do ...

Create two disk partitions on one of your disks, and do your best to create another identical pair of partitions on the other ... down to the nearest byte if possible. If you like, leave some disk space unallocated, so you can create space for swap filesystems & anything else you might want in the future. Then, you can use mdadm to create an array as you normally would. Just be sure not to have any accidents (eg pairing up the wrong partitions, or creating an array out of two partitions on the same physical disk).

---

