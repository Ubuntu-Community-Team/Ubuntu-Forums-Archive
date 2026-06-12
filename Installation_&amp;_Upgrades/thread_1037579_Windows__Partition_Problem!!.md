---
title: "Windows / Partition Problem!!"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by Lukehluke on 2009-01-11
Hello,

I can't seem to resize the partition as it has bad sectors I think or something (My guess).

I tried a Check Disk but didn't help.

So I can't make a partition for Ubuntu as on my primary partition is Windows XP.

I don't want to remove XP as there are some things that I need it for etc.

I can't use my Windows XP disk as I have moved over 100 miles away (to live with someone and the disk is missing somewhere in my parents house 100 miles away).

I really want to use Ubuntu but I don't want to have to run it off a disk as it makes it real slow.

Any iedas?

---

### Post by kranny on 2009-01-11
Why dont you try the second option(_Allocate the largest continous space on the hard disk_) while the partition setuo comes.

---

### Post by Lukehluke on 2009-01-11
> **kranny said:**
> Why dont you try the second option(_Allocate the largest continous space on the hard disk_) while the partition setuo comes.

Wouldn't that kill XP?

There is only one partition on the HD (Well to support an OS).

Are you able to install more than one OS on a single partition?

I also don't want to wipe any of my files.

---

### Post by Mark Phelps on 2009-01-11
Your fears are well grounded.  Unless you are able to create a second partition area (which will, in fact, include two partitions), a standard Ubuntu install is likely to overwrite XP.

A second option is to install INSIDE XP, using Wubi.  For details on that, please see the Wubi subforum.

---

### Post by Lukehluke on 2009-01-11
Wubi sounds good.

The size of it though its tiny compared to Ubuntu.

How is it different?

Do I loose features?

Can I always replace it with normal Ubuntu later?

---

### Post by kranny on 2009-01-11
> **Lukehluke said:**
> Wouldn't that kill XP?

There is only one partition on the HD (Well to support an OS).

Are you able to install more than one OS on a single partition?

I also don't want to wipe any of my files.

No you dont loose any data With that option.The thing here done is partitioner automatically resizes your single partition and installa copy into the new partition

---

### Post by Rhyader on 2009-01-12
Hi Luke.

You should really ask your parents to mail you that disk!

Windows Vista and I *think* XP and 2000 have a Disk Manager
(control panel/admin tools/computer management/storage/disk management)
That lets you expand or shrink (in your case shrink) the one partition making a new unused space. Then you could boot ubuntu from the install CD and let it create its partition(s) in the unused space. 

But you are right to be worried - this is inherently dangerous!
Don't even try to change your partition table unless your existing windows file system is completely free of errors. And, preferably, backed up. I had no problem  making free space by reducing my windows vista partition (in vista of course) but before doing this I ran a diskcheck, defrag, and diskcheck again. 

But from what you said in your first post:
*"I can't seem to resize the partition as it has bad sectors I think or something (My guess)."*
If you do have errors you should do this before you install anything:
Schedule a windows disk check in intense mode (check both boxes) and reboot.
Wait for it to get finished (and wait, and wait, and wait...)
When it is done let Windows analyze your drive to see if it needs defrag.

---

