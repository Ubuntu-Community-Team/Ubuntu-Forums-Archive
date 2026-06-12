---
title: "Boot unexpectedly stalled"
date: 2011-09-03
forum: Hardware
---

### Post by sergio-bobillier on 2011-09-03
Hello,

Well today I turned on my computer like I always do but it was hanging up at boot time. Normally if this should happen I just reset it and then it boots but this time was different it just keep hanging up at boot time.

The boot messages showed something like this:

```
[    0.116022] CPU0: Intel(R) Core(TM) i5 CPU         650  @ 3.20GHz stepping 02
[    0.232623] Performance Events: PEBS fmt1+, Westmere events, Intel PMU driver.
[    0.232791] ... version:                3
[    0.232841] ... bit width:              48
[    0.232887] ... generic registers:      4
[    0.232937] ... value mask:             0000ffffffffffff
[    0.232986] ... max period:             000000007fffffff
[    0.233037] ... fixed-purpose events:   3
[    0.233086] ... event mask:             000000070000000f
[    0.233473] Booting Node   0, Processors  #1
```And the system hangs.

Under normal conditions it would look like this:

```
[    0.233473] Booting Node   0, Processors  #1 #2 #3
[    0.771041] Brought up 4 CPUs
...
...
```Any ides on what could be causing this behavior? A Live CD boots normally on the same machine. Yesterday I installed some 32 bits libraries in /usr/lib32 to try and run a 32 bits version ePSXe in my 64 bits system but I cannot think of a connection between that and that strange behavior specially in that phase of the boot process.

Should I be worried about my hardware?

---

