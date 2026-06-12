---
title: "increasing page size in swap file system"
date: 2008-12-02
forum: General Help
---

### Post by em3ry on 2008-12-02
I'm running ubuntu 8.10 on an older 800 mhz celeron (coppermine) with 256 mb memory.  I only use it for surfing the web but I often have 10+ tabs open at once and firefox uses quite a bit of memory (10 MB per page).  my computer ends up using 200 MB of the swap file system. I can see on system monitor that my computer spends a lot of time waiting for data from the disk.  

would it be possible for me to increase the size of the individual pages in the swap file system? would this be likely to have much of an effect?  is it safe to do so?  reinstalling would be a big nuisance but not critical.

---

### Post by sdennie on 2008-12-02
Even if you could do this (I don't think you can), it would actually have the opposite effect.  Increasing swap page size necessarily increases memory page size.  That has the effect of making fewer pages able to fit into physical memory which increases memory pressure and so increases swapping.  This has some good information about memory management in linux: [http://www.linuxhq.com/guides/TLK/mm/memory.html](http://www.linuxhq.com/guides/TLK/mm/memory.html)

---

