---
title: "update USB flash disk?"
date: 2009-05-09
forum: Installation &amp; Upgrades
---

### Post by iaw4 on 2009-05-09
I installed ubuntu 9.04 onto a USB flash drive using System->Administration->USB Startup Disk Creator.  Works nicely.

Alas, I would also like to run the updater on it.  unfortunately, when I do this, I am informed that I only have 64MB or so, and need about 100MB.  (I also want to install a few packages and software, such as skype.)

could someone please point me to the recommended way of doing this?

sincerely,

/iaw

---

### Post by Triptol on 2009-05-09
If it is full, it is full.

So if your installation does need 100Mb and you don't have it, you really cannot get it on the disk.

Now if you are sure you have that much room on the disk, we could look again.

---

### Post by iaw4 on 2009-05-09
well, its a 4GB flash stick, so I am pretty sure that there is another gig at least available.  I think it is more about how the free space is calculated in the overlay fs.

/iaw

---

### Post by Triptol on 2009-05-10
Could you please post the output of
```
df -h
```
It could be a partitioning problem, where your root partition (/) does not have enough room.

---

