---
title: "BadRam kernel patch fails to compile"
date: 2008-04-10
forum: Hardware &amp; Laptops
---

### Post by 1veedo on 2008-04-10
Hi I'm trying to install [badram](http://rick.vanrein.org/linux/badram/) support for the linux kernel but I keep getting a compile error.  I've tried this with 2.6.22 (current for ubuntu), 2.6.22.1 (what the patch for 2.6.22 specified) and 2.6.24.3 which is the lattest kernel badram supports.  All of them error like this,```
 mm/page_alloc.c: In function ‘badram_markpages’:
mm/page_alloc.c:4425: error: ‘mem_map’ undeclared (first use in this function)
mm/page_alloc.c:4425: error: (Each undeclared identifier is reported only once
mm/page_alloc.c:4425: error: for each function it appears in.)
mm/page_alloc.c: In function ‘badram_setup’:
mm/page_alloc.c:4447: error: ‘mem_map’ undeclared (first use in this function)
make[2]: *** [mm/page_alloc.o] Error 1
make[1]: *** [mm] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.24.3'
make: *** [debian/stamp-build-kernel] Error 2
```I am using intel 64.

---

### Post by jpr82 on 2008-05-05
I have the same problem. I have an AMD64 cpu.

---

