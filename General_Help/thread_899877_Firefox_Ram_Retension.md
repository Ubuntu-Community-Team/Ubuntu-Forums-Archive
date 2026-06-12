---
title: "Firefox Ram Retension"
date: 2008-08-24
forum: General Help
---

### Post by pizzavortex on 2008-08-24
Earlier today, I had a dozen flash video pages in tabs in firefox, it took up 542MB, this is disturbing enough.  However imagine my horror when I closed them all, using only one tab with my bland wikipedia homepage loaded.  This still used the same amount of memory.  This is applies for everything else I do, not just flash video.  What kind of excessive caching is firefox 3 using which causes 542MB to be an acceptable footprint with wikipedia loaded. While open firefox's memory usage can only go up.  How can I disable this sinister and scelerate waste of my computer's 1GB of RAM and 1GB of swap?

---

### Post by mssever on 2008-08-24
> **pizzavortex said:**
> Earlier today, I had a dozen flash video pages in tabs in firefox, it took up 542MB, this is disturbing enough.  However imagine my horror when I closed them all, using only one tab with my bland wikipedia homepage loaded.  This still used the same amount of memory.  This is applies for everything else I do, not just flash video.  What kind of excessive caching is firefox 3 using which causes 542MB to be an acceptable footprint with wikipedia loaded. While open firefox's memory usage can only go up.  How can I disable this sinister and scelerate waste of my computer's 1GB of RAM and 1GB of swap?
In about:config, you can fiddle with the setting browser.cache.memory.capacity. Google the key name for documentation. Note that this has to effect in Firefox 2, contrary to the documentation. I haven't been too concerned in FF3, since I now have so much RAM that I really don't care anymore. It is an annoying bug, though.

---

### Post by pizzavortex on 2008-08-24
It seems to work, it was at over 65000 before! I set it to -1: the default, managing the cache as firefox sees fit. I also re-enabled browser.cache.disk.enable.  I must stop messing with about:config now. No matter how awesome or amazing it is.

---

