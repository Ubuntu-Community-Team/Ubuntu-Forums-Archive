---
title: "Multiple SWAP partitions: what is priority number??"
date: 2007-05-01
forum: Hardware &amp; Laptops
---

### Post by elijahclarity on 2007-05-01
Of late, I've been doing some reading that having multiple swap partitions can speed perfomance a bit.

I have 256MB memory and would like to do this. (I can't afford more RAM right now)

But all the guides and howtos I've seen seem to set a priority number to each swap partition and they say that setting the SAME priority number to each swap partition is more beneficial.

But none of them explain why they set a particular priority number to the swap partitions.
 I understand that they all should have the same priority number, but what determines what that priority number should be??? 
In some example fstabs (where priority number is the SAME for every swap partition), I've seen pri=3 , in some pri=8, in some pri=5 and so on. What priority number should I use? Are they putting these numbers just like that? Does it really matter what number I put here, even if all swap partitions have the same number?

I understand that swap partitions with the lowest priority numbers would get used up first, but here I'm ONLY talking about fstab's where the SAME priority number is allotted to EACH swap partition.

I hope I have been clear enough. Thanks for your time and help.

---

### Post by dcstar on 2007-05-02
> **elijahclarity said:**
> Of late, I've been doing some reading that having multiple swap partitions can speed perfomance a bit.
........

Only if they are on separate physical hard drives, otherwise it is a complete waste of time.

---

### Post by elijahclarity on 2007-05-02
Yes I've 2 hard drives. But u didnt answer my question? What priority number should I set??

---

