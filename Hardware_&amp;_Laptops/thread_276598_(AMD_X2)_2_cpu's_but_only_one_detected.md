---
title: "(AMD X2) 2 cpu's but only one detected"
date: 2006-10-13
forum: Hardware &amp; Laptops
---

### Post by kamikaze04 on 2006-10-13
Hello,

I have a AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ which is detected as 2 cpu's _by other Linux systems _(ubuntu 64 bits, fedora, gentoo) .

But here in ubuntu 6.10 686 with kernel 2.6.15-27-386 #1 PREEMPT only one cpu is detected (just doing a cat /proc/cpuinfo) . Also detected only one with 2.6.15.23-386.

I was wondering if it is not supported by the i386 branch or a missconfiguration of kernel because the ubuntu amd64 6.10 is detecting fine the two cpus.

Any information will give me a little spot light.

Thank you.

---

### Post by kamikaze04 on 2006-10-13
Just installed the smp kernel and "voilá" it is now supporting multiple cpu's

---

