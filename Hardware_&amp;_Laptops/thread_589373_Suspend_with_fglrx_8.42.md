---
title: "Suspend with fglrx 8.42?"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by mpiktas on 2007-10-24
ATI released new fglrx driver 8.42, does anybody know if it fixes the suspend problem on laptops? The original problem was the new SLUB allocator in kernel, apparently older fglrx drivers have a problem with it. Does this problem persist with new driver? This is the only thing holding me from upgrading to Gutsy, suspend/resume is essential for me.

---

### Post by parren on 2007-10-24
I tried it just now - no luck. I installed the whole thing on my custom-compiled SLAB kernel and there it works perfectly, including compiz (after I followed [these instructions]("http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support")).

With the default kernel, I could not even get into the desktop properly with compiz turned on. GDM complained about not being able to determine monitor sized and grayed out the entire screen after logon. (And, yes, I did build the kernel module again for the default kernel.)

Without compiz it worked, including the ATI config tools, but suspend would still hang the machine.

---

