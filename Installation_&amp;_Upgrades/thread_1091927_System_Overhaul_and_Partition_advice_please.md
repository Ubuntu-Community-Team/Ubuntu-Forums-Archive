---
title: "System Overhaul and Partition advice please"
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by Roving Sign on 2009-03-09
Hi - I've been using Ubuntu 8.10 for a few months now...feeling like I've overcome my hardware issues. Running smoothly...

I have a new harddrive - and a few options for an overhaul...

I do have a legal XPpro license that I'd like to use - I still sort of need Dreamweaver from time to time - so I have to keep that.

This is an older system...Duron 1300/2GB RAM/ATI Radeon 9550

IDE drives:

120GB HD - Currently 50/70 With Ubuntu on the 50GB partition, no OS on the 70 - just FLAC audio.

250GB HD - New, unused

Im tending toward cleaning off the 70GB partition on the 120GB and using that for the XP install...and just going Ubuntu/Linux on the 250. 

My current Ubuntu on the 120GB will be just fine as a backup system.

How should I partition the 250GB drive? I want to use 8.10 as my main OS in this drive...any other partitions might just have other Linuxes just to satisfy my curiosity - or just storage.

Questions:

Any good partition strategies for the 250 GB drive? Format? ext3?

What format for the XP install on the 120GB drive? I usually use NFTS

What settings for the HD jumpers?

Any issues getting GRUB to recognize the drives/OS'es?

I have the Gparted Live CD

Thanks for any pointers...advice...shame...;)

Looking forward to being "settled"...

---

### Post by Redenbacher on 2009-03-09
My typical setup is 15 GB dedicated to Ubuntu and swap. I'm unsure of its exact size, and with package installs and whatnot I give it room to grow. 

I then dedicate the remainder to /home. All of it ext3, as its what I've been recommended as a far superior filesystem, though I don't know the technical reasons.

You can later shrink your /home partition to add other distros, but you'll always have that /home accessible. Hence why I like to keep it separate. Personally I haven't tried any other distrobutions, but prefer to keep it separate for the 6 month updates to Ubuntu :)

I too use NTFS for Windows, it seems to be default and I would gather most efficient for it.

From my understanding, GRUB will only have problems if you install Windows *after* a linux install, rather than first. Windows, the bully that it is, doesn't like to recognize any other operating systems. But I'm no expert.

---

