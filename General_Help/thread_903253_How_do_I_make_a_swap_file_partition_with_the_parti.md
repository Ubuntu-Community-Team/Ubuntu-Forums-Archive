---
title: "How do I make a swap file partition with the partitioner?"
date: 2008-08-28
forum: General Help
---

### Post by Timberwolf5578 on 2008-08-28
I am going to use the manual choice in the partitioner.  I have Win XP on one partition, and I am installing Ubuntu on the other one.  I know I am supposed to choose "primary", "ext3", "beginning", and "/" for the Ubuntu partition, correct? but exactly how do I make the swap partition and what options do I choose?

Thanks.

---

### Post by Crafty Kisses on 2008-08-28
This link may help you > [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by justleen on 2008-08-28
instead of "ext3" you can select "swap" as type.

---

### Post by Timberwolf5578 on 2008-08-28
> **justleen said:**
> instead of "ext3" you can select "swap" as type.

but how bout the other options such as "primary", "beginning", and "/"

What should those be set to?

---

### Post by mcduck on 2008-08-28
> **Timberwolf5578 said:**
> but how bout the other options such as "primary", "beginning", and "/"

What should those be set to?

it makes no diffeecne if it's a primary partition or logical one.So this depends on how many partitons you already have on the disk. (youc an only have 4 primary partitions, or 3 primary partitions + one extended, which can contain as many logical partitions youw ant. The only important thing here is that Windows needs to be on a primary partition, Linux works fine on both.)

With "beginning" you are probably referring to where the partition should be located on the disk? Some say beginning is the best, some say end is the best, reality is that you won't get any noticeable performance difference where ever you put the swap.

"/" would be for mount point (the root partition is mounted into "/". Swap partitions aren't really mounted in that sense, so it doesn't have a mount point.

---

