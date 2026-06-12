---
title: "dual cpu both stay maxed at 100%"
date: 2010-02-12
forum: Hardware
---

### Post by neilevan814 on 2010-02-12
I am running ubuntu 9.10 on
asus m2n68-vm with 
amd 4850e 2.5Ghz cpu
6GB memory

I have checked the bios for voltages fluctuations, temperature ranges, and did a memcheck all came back fine.  I have shutdown and restarted several times and checked the other partitions ubuntu studio 64 cpu loads and they were fine.

What to do?

---

### Post by mikewhatever on 2010-02-12
Well, which process or processes are consuming the cpu cycles?

---

### Post by neilevan814 on 2010-02-12
there are quite a few, but the mb's each is consuming is low to maybe 6mb's for some applications.  I have some cronjobs set,  ssh setup client and server, nothing really unusual that i can pinpoint

---

### Post by neilevan814 on 2010-02-12
I think I found it.  I have rosetta running to do protein folding.  In top it shows 98% and 98%.  I think i will have to let it go.  Thanks for getting me hunting.

---

