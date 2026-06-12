---
title: "resize root filesystem"
date: 2008-08-07
forum: General Help
---

### Post by rogier.de.groot on 2008-08-07
Hi all,

I've recently added extra RAM to my machine, and the 1 GB swap partition is now effectively useless. I'd like to remove it and add the free space to my root partition, growing the root partition, without reinstalling my machine.
I understand that can't be done from the regular system - but can you do it from liveCD (or winXP on the same machine)? And how do you do it?

TIA

---

### Post by hyper_ch on 2008-08-07
use the livecd... as it is swap now it will automatically be used... also the existing ext3 drives will be mounted.

So once you're in the live session disable swap, make sure you unmount the ext3 partitions, then open gparted, delete that swap and expand one of the partitions next to it.

P.S.: And make sure you have backups.

---

