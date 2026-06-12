---
title: "gap before initializing second cpu"
date: 2011-10-17
forum: Hardware
---

### Post by tcorneli on 2011-10-17
Hi,

I am experiencing something strange when booting up. At the start of the boot process, when the kernel is initializing the cpu cores, I sometimes get a delay of several minutes before the kernel continues the boot process, like this:

```
[    0.060567] CPU0: Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz stepping 02
[    0.164403] Performance Events: PEBS fmt1+, Westmere events, Intel PMU driver.
[    0.164409] ... version:                3
[    0.164410] ... bit width:              48
[    0.164411] ... generic registers:      4
[    0.164413] ... value mask:             0000ffffffffffff
[    0.164414] ... max period:             000000007fffffff
[    0.164415] ... fixed-purpose events:   3
[    0.164417] ... event mask:             000000070000000f
[    0.164747] CPU 1 irqstacks, hard=f74ce000 soft=f74d8000
[    0.164749] Booting Node   0, Processors  #1
[    0.164751] smpboot cpu 1: start_ip = 9b000
[  416.472742] Initializing CPU#1
[  416.569723] CPU 2 irqstacks, hard=f74e2000 soft=f74e4000
[  416.569725]  #2
[  416.569726] smpboot cpu 2: start_ip = 9b000
[  628.106915] Initializing CPU#2
[  628.203382] CPU 3 irqstacks, hard=f750e000 soft=f7514000
[  628.203384]  #3
[  628.203385] smpboot cpu 3: start_ip = 9b000
[  628.213419] Initializing CPU#3
[  628.311491] Brought up 4 CPUs
```

As you can see, I had to wait in this instance for about 10 minutes, before the boot continued normally. The problem occurred with every version of Ubuntu since my first install and with every Ubuntu upgrade (Karmic being the first). It appears to happen randomly: it does not matter if the battery is low or not, and the gaps themselves vary in duration. Lately I installed Arch next to my Ubuntu on a new partition and it happens there as well. To make make matters worse, Windows boots up in no time, quite galling for a linux fan.

I thought it might be hardware related, so that is why I posted it here. My system is an HP ProBook 4720s.

---

