---
title: "mdadm -- potential blunder"
date: 2008-01-15
forum: Hardware &amp; Laptops
---

### Post by moogle10000 on 2008-01-15
Hello!

I've been playing around with a raid 5 on 4 - 400gb hds ... There's some data on there, but I suppose I can back it up. 

Anyway, I'm having a persistent drive failure (which I'm pretty sure is caused by a bad SATA port on the motherboard). During the diagnosis of that problem I noticed that when I originally set up the array, I didn't create linux raid partitions on the drives but instead just used the drives at the block level. (mdadm --create .... /dev/sda /dev/sdb ....)

I've been looking around and have been trying to find the disadvantages to this method. Every tutorial I see for mdadm says to create the partitions... Which I'm not opposed to doing, but if I don't *have* to, then I won't. 

Thoughts? :)

Thanks!

---

