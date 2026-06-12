---
title: "kernel upgrade - howto?"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by waveman on 2009-01-09
I upgraded from 8.04 to 8.10. The kernel remained at 2.6.24-22 after the upgrade. This is causing all kinds of problems with my video card driver (nvidia) after the 8.10 patch I installed yesterday.

My life would really be a lot easier if I could upgrade the kernel to 2.6.27. Is there a HOWTO lying about somewhere?

I looked in the package manager, but didn't see much in the way of kernel upgrades, just the kernel headers.

Thanks...

---

### Post by zvacet on 2009-01-09
Does upgrade went as it should? Check your installed release with this

```
lsb_release -a
```

---

