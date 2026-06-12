---
title: "AMD and Intel L1 and L2 cache size"
date: 2008-11-27
forum: Hardware
---

### Post by tashe on 2008-11-27
I've been reading today about the different types of AMD and Intel processors, cause I want to help a friend make a choice about his new computer. I've noticed that AMD seem to have smaller L1 and L2 caches than Intel's. Does anyone know why is this so, cause I know that it's a very important part of the performance of the CPU. 
Thank you in advance

---

### Post by sdennie on 2008-11-27
I haven't looked at the differences between current Intel and AMD offerings but, caches are used to hide latencies.  The size of the cache is important but the way it's utilized is equally important.  I don't know much about Intel/AMD chips but, some chips/OSs/compilers will understand how data is being accessed and automatically prefetch things to L2 cache before they are used.  Essentially, basing a buying decision on the size of L1 and L2 cache is meaningless unless you have a target software in mind and can benchmark it.  A smaller L2 cache doesn't necessarily mean a slower machine.

---

