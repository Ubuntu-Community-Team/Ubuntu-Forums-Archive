---
title: "[SOLVED] TP X30 Suspend Broke after 8.04-&amp;gt;8.10 upgrade"
date: 2008-12-06
forum: Installation &amp; Upgrades
---

### Post by iponeverything on 2008-12-06
I upgraded and my wife's thinkpad X30 from 8.04 to 8.10. Everything came off great except that it broke suspend to RAM.

So -- 
   -- Does anyone know of a fix?

Thanks.

---

### Post by iponeverything on 2008-12-06
panic was being caused by rt61pci.  having it unload before suspend solves the problem.

---

