---
title: "Wich partition should be primary and wich should be logical?"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by pedramslhr on 2008-12-24
At present time I have 3 primary partitions on my dell vostro 1510 laptop. And seems that it is not possible to have more than 4 primary drives.
Now I'm going to install ubuntu 8.04 on this laptop and set up the partition manually.
I will create  a swap partition an a root(ex3) partition.
which one should be primary and which one should be logical?(or maybe they should be both logical or both primary.)

Help me please!
Thanks

---

### Post by taurus on 2008-12-24
You can leave / as primary and swap as logical.  Remember, you cannot have more than 4 primaries so you need to make one of those primaries into extended partition first before you can create any logical partition under it.

---

### Post by pedramslhr on 2008-12-24
> **taurus said:**
> You can leave / as primary and swap as logical.  Remember, you cannot have more than 4 primaries **so you need to make one of those primaries into extended partition first before you can create any logical partition under it**.

This should be done before installing ubuntu?

---

### Post by taurus on 2008-12-24
If you choose.  Then, pick the Manual when you get to the partition screen.  Tell installer to use whichever partition that you have set up as root filesystem and don't forget to mount it to / or it will complain about no root filesystem.  You don't have to do anything to swap partition since it knows how to handle it, if you have formatted that little partition as linux swap.

---

