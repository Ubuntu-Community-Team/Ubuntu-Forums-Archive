---
title: "Update to 8.04 LTS"
date: 2009-06-14
forum: Installation &amp; Upgrades
---

### Post by boondocks on 2009-06-14
This is an older Ubuntu  7.10 system.
I am trying to use Update Manager to update it to 8.04 LTS.

But it says that I do not have enough free space in "/".
I have about 500 Mb free on the disk.
So  I did  "sudo   apt-get   clean" but that did not clean up enough free space.

I have a spare 4Gb USB Flash Drive.

Is it possible to use this Flash Drive to temporarily increase the available space?
So that the update to 8.04 can be done.

Even if I have only 100 Mb on this system after the 8.04 update, that is just fine.
I use the USB Flash Drive for storing my data.

---

### Post by tgalati4 on 2009-06-14
You probably need 3-5 GB of free space.  If you fill up the file system during an update, bad things will happen.

A better plan is to get another hard disk.  Leave your current, working system intact.

Put 8.04 on the new disk.  Now you can boot into either version.  Keep 7.10 until you get everything working in 8.04.  For me, it's usually a few months of tweaking and updates to get a solid system.

Linux needs some breathing room.  Stuffing the hard disk will lead to problems.

---

