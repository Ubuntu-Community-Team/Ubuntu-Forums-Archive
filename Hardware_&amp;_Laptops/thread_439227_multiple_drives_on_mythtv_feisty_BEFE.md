---
title: "multiple drives on mythtv feisty BE/FE"
date: 2007-05-10
forum: Hardware &amp; Laptops
---

### Post by Panhead Bill on 2007-05-10
I'm trying to install myth feisty on my test mule using the community guide. [https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend)

Instead of using one drive for everything, i'd like to use my smaller 10 Gig drive for the / and swap partitions, and the larger 120 Gig drive for the /var/lib partition listed in the guide.

Is this as simple as just partitioning the second drive per the guide instructions as if it were part of the first drive?  in other words as xsf primary with a mount point of /var/lib, or do I have to do a symlink? (or something else)

TIA

Nevermind, I ran with the setup and it worked.

---

