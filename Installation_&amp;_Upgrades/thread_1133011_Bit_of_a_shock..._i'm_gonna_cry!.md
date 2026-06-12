---
title: "Bit of a shock... i'm gonna cry!"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by mastubbs on 2009-04-22
Hi all,

Trying to install ubuntu and had a bit of a shock!

1. I downloaded ubuntu.
2. wrote to cd,
3. booted cd,
4. went to install but at partitioning told me i had only one partition on my disk, and that it was unallocated :-( [although actually i have a dell xps with vista partition and extended partition with dell media direct on it]
5. rebooted vista and searched the web no problem, someone suggested using gparted to manually partition running ubuntu from cd.
5. rebooted and tried manually from gparted, told me the same thing: one disk, dev/hda 100% unallocated.
7. went to reboot vista again but this time error, it wants a boot disk...
8. Stuck in the OS boot disk from dell, but no dice, just the same error over and over!!

Any suggestions from anyone to get back vista and/or install ubuntu as partition, preferably duel boot?

Thanks all - sorry im a TOTAL linux nube.

Matt

---

### Post by snowpine on 2009-04-22
(edit) Check out the post below from someone who has more Vista experience than I.

---

### Post by calrogman on 2009-04-22
I resized my Vista partition from 120 GiB to 35 GiB without any problems, I just rebooted into Vista afterwards so it could ensure the integrity of the file system because it is smart enough to realize that its partition has been resized, just not smart enough to figure out that it was intentional.

If Vista is no longer booting, chances are something went horribly wrong during resizing.

---

### Post by Mark Phelps on 2009-04-22
You're both going to need to boot from a Vista DVD and run Startup Repair to get Vista working again.

If you don't have such a DVD, you can download and burn a recovery CD from the NeoSoft forums -- but you have to torrent it because they shutdown their direct downloads.

---

