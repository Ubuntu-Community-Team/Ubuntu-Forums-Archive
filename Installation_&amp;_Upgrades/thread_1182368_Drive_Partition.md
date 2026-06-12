---
title: "Drive Partition"
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by Shibblet on 2009-06-08
I am going to do a clean install of Ubuntu Jaunty this evening, and I was wondering what would be a good way to partition the HD?  

I've heard all sorts of stories about Kernel Swap, and Root Swap, and such.  And to be honest, it doesn't make that much sense.

My plan was to do a 10g Root, and a 110g Home, with a 8g Swap (I have 4g of Ram)

I definitely want my root to be separate from Home, because I will undoubtedly upgrade, and want to do a clean install without losing my schtuff.

Is there a more efficient way to partition?

---

### Post by merlinus on 2009-06-08
No more than 1.5G for swap, with 4G RAM.  Otherwise, looks good.

Are you using the entire hdd, or dual-booting?

---

### Post by Shibblet on 2009-06-08
> **merlinus said:**
> No more than 1.5G for swap, with 4G RAM.  Otherwise, looks good.

K.  I am curious as to why though?

> **merlinus said:**
> Are you using the entire hdd, or dual-booting?

I'm dual booting.  Is there something else I need to know?

---

### Post by merlinus on 2009-06-08
I assume windows, but what version? 

In any event, be sure to delete temp and other unneeded files and defrag before shrinking its partition.  And if it's vista, use its disk management tool to do the resizing.  Otherwise you will have a huge mess.

---

### Post by Shibblet on 2009-06-08
> **merlinus said:**
> I assume windows, but what version? 

In any event, be sure to delete temp and other unneeded files and defrag before shrinking its partition.  And if it's vista, use its disk management tool to do the resizing.  Otherwise you will have a huge mess.

No problem.  I am going to load Vista tonight first anyway.  But, just out of curiosity, what kind of mess are we talking about?

---

### Post by merlinus on 2009-06-08
If you do not use vista's disk management tool to shrink its partition, then not only will ubuntu not install correctly, but there is a good chance it will mess up vista as well.

Meaning, you will not be able to access any os, and your computer will be dead in the water.

So install vista using the entire hdd, and then proceed as outlined.

---

### Post by Shibblet on 2009-06-09
Whats the reason I only need 1.5g of Swap?

---

### Post by merlinus on 2009-06-09
Swap is only used when all of your ram is being used by the os and apps.  It makes the system faster because there is less hdd activity.  With 4G ram, 1.5 swap is more than enough.

---

