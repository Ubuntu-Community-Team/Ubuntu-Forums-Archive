---
title: "How to troubleshoot suspend?"
date: 2008-09-23
forum: Hardware
---

### Post by mma8x on 2008-09-23
ok, i'm still having trouble suspending on my compaq c770.  it suspends once just fine.  second time i get a black screen with no hd activity.  this seems to be a common problem without a solution.  since upgrading to 2.6.27, hibernate works fine.  
i've tried unloading various modules prior to suspend (ehci, usbcore, ath5k, etc) without luck.  the -27 kernel uses the ath5k module out of the box for my atheros wifi, while the -24 used madwifi which needed compiling (both kernels had same issue w/suspend).  i've also tried disabling the apm setting on hdparm (per one suggestion) without difference.  i'm not using nvidia/ati adapters. 

anyways:
1. has anyone had this problem and resolved it?
2. how can i troubleshoot what's causing the hangup? i tried echo > 1 /sys/power/pm_trace, but wasn't really sure what i should be looking for in dmesg; nothing stood out, anyway.

i think that this is more frustrating because it works once...

---

