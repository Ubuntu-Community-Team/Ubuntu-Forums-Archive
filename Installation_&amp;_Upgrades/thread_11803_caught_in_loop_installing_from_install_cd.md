---
title: "caught in loop installing from install cd"
date: 2005-01-19
forum: Installation &amp; Upgrades
---

### Post by menahem on 2005-01-19
I have an existing partition (hda1) devoted to slackware, hda2 devoted to swap, and an unused hda3 with 90gig available.  

During installation with the install ubuntu cd, I am asked for choice of partition for my newly installed ubuntu, and I choose hda3, but then Ubuntu seems to want to repartition my entire drive, which I do not want to do.  How do I get through the partition selection and then on to the rest of the installation?

Thanks for any  help.

sam

---

### Post by az on 2005-01-19
Just before you tell the partitionner to go, you should have selected 

hda3 to be /
and hda2 as swap.


It should have detected hda1 as ext3 (or whatever filesystem you put there), but there be no mountpoint (if you select that partition, you see the words "do not use partition")

To go back to the beginning, you are chosing manual partitioning, aren't you?

---

