---
title: "Magical hardware upgrade"
date: 2009-04-28
forum: Hardware
---

### Post by dargaud on 2009-04-28
OK, nothing to do with Ubuntu, but I thought I'd share. I recently bought a mobo with an AMD Phenom II X3 710 processor. You know, it's one of those quadcores where one of the cores doesn't work, and it gets fried by AMD and sold as a triple-core for about half the price of the quad-core.

Anyway, it worked as advertised, and then after a few days it magically turned into a quad-code:
```

$ sudo lshw -C cpu
  *-cpu
       description: CPU
       product: AMD Phenom(tm) II X4 10 Processor
       vendor: Advanced Micro Devices [AMD]
       physical id: 4
       bus info: cpu@0
       version: AMD Phenom(tm) II X4 10 Processor

```
All 4 CPUs show in the system monitor and seem to work fine. Should I be worried ?

---

