---
title: "processor upgrade"
date: 2007-12-07
forum: Hardware &amp; Laptops
---

### Post by _DjScrew_ on 2007-12-07
I googled a bit and I'm sure I missed something, so flame as you wish. The questions being asked are exactly related to ubuntu, but linux in general, this just happens to be my forum of choice :) ... We have a couple of poweredge 1950 servers running centos one has dual dual cores and the other has dual quad cores. So, long story short someone got mixed up and the installs got swapped. The easiest way to resolve, would be to just swap the cpus... but I'm not sure what that entails on the os side... would I just need to recompile the kernel? Thanks for any help guys.

---

### Post by jespdj on 2007-12-07
No, Linux detects the CPUs at boot time, you will not need to recompile the kernel or do anything special. To see what CPUs Linux has detected, type:
```
cat /proc/cpuinfo
```

---

### Post by _DjScrew_ on 2007-12-07
beautiful. Thank you, sir.

---

