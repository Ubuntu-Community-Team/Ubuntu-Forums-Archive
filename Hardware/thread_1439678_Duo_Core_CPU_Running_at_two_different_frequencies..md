---
title: "Duo Core CPU Running at two different frequencies..."
date: 2010-03-26
forum: Hardware
---

### Post by sbrendtro on 2010-03-26
I have a Sony Vaio laptop (VGN-FZ140E) running Ubuntu Studio 9.10, kernel 2.6.31-20-generic-pae SMP i686.  I've been noticing some performance issues and was checking to make sure that both cores were active when I came across a discrepancy with the CPU core frequencies.  According to /proc/cpuinfo, one processor is running at 800 MHz and the other at 1801 MHz.  This laptop has very few settings in the BIOS, definitely not overclocking (let alone "underclocking").  The following is the abridged output of /proc/cpuinfo:

```
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
stepping    : 13
cpu MHz        : 800.000
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
.
.
.

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
stepping    : 13
cpu MHz        : 1801.000
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
.
.
.
```Is this a bug with the SMP part of the kernel?  Very confusing to me why on earth it would be reading this way...

Thanks,
Steve Brendtro

---

### Post by gordintoronto on 2010-03-26
Modern processors can be throttled back when they are idle or nearly so, in order to reduce the power consumption and heat. In a dual-processor, the two CPUs can be throttled back independently. If you do something CPU-intensive, like rendering a video, the CPUs will jump up to top speed. Intel's latest CPUs will even automatically overclock for a short time!

No bug, it's a good thing!

---

