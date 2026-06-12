---
title: "Does root need reserved space on every partition?"
date: 2008-11-23
forum: General Help
---

### Post by olavjunior on 2008-11-23
Root gets 5 % of the space reserved on every partition. I have ubuntu installed on a separate partition to home, so it has it's reserved 5 % on both of them. Is this really necessary? Could I free up all the space on home to my self or does root need space on home (using tune2fs)? 

I also have a external ext3 disk, does root also need the space on that one?

---

### Post by philinux on 2008-11-23
You can reclaim it.

[http://boncey.org/2006_11_18_reclaiming_ext3_disk_space](http://boncey.org/2006_11_18_reclaiming_ext3_disk_space)

---

### Post by olavjunior on 2008-11-23
Yea, I know I can reclame it, that's why I'm asking if root really need the space on my seperate home and external disk

---

### Post by Charlie708 on 2008-11-23
It also works as a buffer so you don't fill up the partition in its entirety.

---

### Post by philinux on 2008-11-23
> **olavjunior said:**
> Yea, I know I can reclame it, that's why I'm asking if root really need the space on my seperate home and external disk

Only on root really needed. My root is 12 gig currently using 3.2 gig. So not really need there either.

---

### Post by eldragon on 2008-11-23
well, if your /home partition gets full, the root account can use the extra 5% when doing a fscheck during boot.

aside from that, no, ive disabled the reserved space on my home partition and i havent felt any side effect (yet)

---

### Post by olavjunior on 2008-11-24
> **eldragon said:**
> well, if your /home partition gets full, the root account can use the extra 5% when doing a fscheck during boot.

aside from that, no, ive disabled the reserved space on my home partition and i havent felt any side effect (yet)

Nice to know! I can't see the reason why root needs space on my external hd. I've left it with 0,5 % at the moment, also just 1 % on my home

---

