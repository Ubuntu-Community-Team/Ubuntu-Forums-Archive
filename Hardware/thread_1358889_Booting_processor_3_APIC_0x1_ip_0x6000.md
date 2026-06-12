---
title: "Booting processor 3 APIC 0x1 ip 0x6000"
date: 2009-12-18
forum: Hardware
---

### Post by houdodu on 2009-12-18
Just wanted to add some more support behind this thread:

[http://ubuntuforums.org/showthread.php?t=1289119](http://ubuntuforums.org/showthread.php?t=1289119)

My startup would often get stuck on "Booting processing 3 APIC .." and various other places, but mostly here. Thanks to the forum users and a closed thread, I confirmed that it was caused by a USB hub built into my Dell monitor?! Strange but true. Unplugging the USB hub portion of the monitor ceased all boot problems instantly. Plugged in, it would get through boot maybe 1/20 times.

$ uname -a
Linux theden 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:02:15 UTC 2009 
x86_64 GNU/Linux

$ cat /etc/issue
Ubuntu 9.10 \n \l

Running under a Shuttle box with AMD quad core.


> Dec 16 22:18:05 theden kernel: [    0.010000] CPU: L2 cache: 6144K
Dec 16 22:18:05 theden kernel: [    0.010000] CPU 2/0x3 -> Node 0
Dec 16 22:18:05 theden kernel: [    0.010000] CPU: Physical Processor ID: 0
Dec 16 22:18:05 theden kernel: [    0.010000] CPU: Processor Core ID: 3
Dec 16 22:18:05 theden kernel: [    0.010000] mce: CPU supports 6 MCE banks
Dec 16 22:18:05 theden kernel: [    0.010000] CPU2: Thermal monitoring enabled (TM2)
Dec 16 22:18:05 theden kernel: [    0.010000] x86 PAT enabled: cpu 2, old 0x7040600070406, new 0x7010600070106
Dec 16 22:18:05 theden kernel: [    0.441573] CPU2: Intel(R) Core(TM)2 Quad  CPU   Q9450  @ 2.66GHz stepping 07
Dec 16 22:18:05 theden kernel: [    0.442519] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
Dec 16 22:18:05 theden kernel: [    0.450070] Booting processor 3 APIC 0x1 ip 0x6000


---

