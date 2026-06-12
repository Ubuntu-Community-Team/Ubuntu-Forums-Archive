---
title: "How to mocify for peak RAM usage."
date: 2010-02-06
forum: Hardware
---

### Post by clicker4721 on 2010-02-06
I have a 64-bit dual-core running with an NVIDIA 8900 GTX XXX edition and 4 GB of RAM. What concerns me is that, whenever I watch the system monitor, only 1 GB (give or take 5 MB) of my RAM is being used. Where to I go to pick up the pace on my RAM?

---

### Post by lloyd_b on 2010-02-06
> **clicker4721 said:**
> I have a 64-bit dual-core running with an NVIDIA 8900 GTX XXX edition and 4 GB of RAM. What concerns me is that, whenever I watch the system monitor, only 1 GB (give or take 5 MB) of my RAM is being used. Where to I go to pick up the pace on my RAM?

Linux *will* use every bit of RAM if it can find a use for it.  Go into a terminal window, and type "free" - this will show all of the memory usage, including cache and buffers.

Over time, you should wind up with almost all of your 4GB used, either by programs or by cache/buffers.  The system monitor is probably just showing what's in use by *programs*.

Note that when you first start the machine, it may not have had a chance to fill up the cache, so don't be surprised if it's not using all the memory at first.  Use the computer for a while, and then check it again.

Lloyd B.

---

