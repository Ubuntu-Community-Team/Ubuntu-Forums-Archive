---
title: "Old software RAID-0 won't go away"
date: 2007-07-03
forum: Hardware &amp; Laptops
---

### Post by kizzle on 2007-07-03
Hey everyone. First, I wanna thank everyone who posts on this forum. I am new to Linux, and the resources here have been invaluable to my transition.

Here's my problem. I installed Ubuntu 7.04 Desktop onto a brand-new built computer, which had three harddrives - one PATA (boot drive) and two SATA. After Ubuntu installed, I downloaded mdadm and manually (via terminal) set up a 2-drive RAID-0 on the SATA drives. It worked fine.

A few days ago, the rest of my computer stuff came, including four more harddrives. I installed them, made sure they were all being picked up, and tries to set up the new RAID, this time to be a 6 drive RAID-5. I kept getting permission errors and device not found errors, so I finally downloaded the Alternative Ubuntu install CD. That's when I found out that the old RAID was still there. Duh!

But here's where it's not-so "duh." I have done everything I can think to remove the old RAID. I tried to delete the old RAID in the install, and it says that the device cannot be deleted, and that maybe it is busy. I tried to go into the shell and manually stop it, then delete it. No luck. 

I have repartitioned the drives. I have repartitioned and formatted the harddrives in ext3. I have formatted the drives in fat32. I even took the drives out and tried formatting them in NTFS on a W1nd0ws system; one wouldn't read, the other formatted, but still no luck. I just can't seem to get rid of the old RAID.

I can set a RAID up between the four new drives, so the RAID driver/install disc doesn't seem to be screwed up. And when I take the two original RAID devices out of the computer, Ubuntu doesn't pick up the old RAID any more.

What can I do? I just downloaded a boot CD with a zero-ing program, but these are 500 GB harddrives, and if there are any alternatives to zero-ing these two drives I would love to hear them.

Thanks!

---

