---
title: "Threadripper 1950X - Incorrect boost speeds"
date: 2019-02-23
forum: Hardware
---

### Post by admiral-code on 2019-02-23
I'm on Ubuntu 18.10.  I've noticed that my base/boost clocks are being listed incorrectly.

Base is being listed as 2.2 GHz
Boost is 3.4 GHz
The CPU runs at 3.7 GHz or lower, it never approaches 4.0 or 4.2 (with XFR)

I've tried playing with CPUFreq with no luck.  I am running Kernel 4.20.12 due to a bug in the 4.18 series (no timeout for a PSP error hangs the system, it's fixed in newer kernels), however this is kernel independent.  I've tried under various kernels.

Any guidance here?

---

### Post by QIII on 2019-02-24
Hello!

What are you doing to stress test the CPU?  How are you measuring the frequency?

The CPU will not likely ever achieve that sort of speed in the aggregate.  That is a limited per-core maximum value and if you are observing the CPU value rather than all the individual cores/threads you wouldn't see it - unless you are OC'ing, in which case you'd best have a very aggressive cooling solution.

---

