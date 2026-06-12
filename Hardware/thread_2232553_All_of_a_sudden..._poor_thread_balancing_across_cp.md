---
title: "All of a sudden... poor thread balancing across cpus"
date: 2014-07-02
forum: Hardware
---

### Post by mike-g2 on 2014-07-02
Hi,

I am running 12.04 on a 64 core AMD machine with the following specs (via lscpu)

Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                64
On-line CPU(s) list:   0-63
Thread(s) per core:    2
Core(s) per socket:    8
Socket(s):             4
NUMA node(s):          8
Vendor ID:             AuthenticAMD
CPU family:            21
Model:                 2
Stepping:              0
CPU MHz:               1400.000
BogoMIPS:              4799.98
Virtualization:        AMD-V
L1d cache:             16K
L1i cache:             64K
L2 cache:              2048K
L3 cache:              6144K
NUMA node0 CPU(s):     0-7
NUMA node1 CPU(s):     8-15
NUMA node2 CPU(s):     16-23
NUMA node3 CPU(s):     24-31
NUMA node4 CPU(s):     32-39
NUMA node5 CPU(s):     40-47
NUMA node6 CPU(s):     48-55
NUMA node7 CPU(s):     56-63

We are running parallel code that we've used recently, but all of a  sudden instead of a thread using ~100% of cpu it is using 33%.  Further, we see that the 15 threads are only running on 5 of the cores.Below is a screenshot of what htop returns.

[ATTACH=CONFIG]254404[/ATTACH]

Note that the load is about 15. From what I can tell cpufreq is not installed and none of the cpus are overheating.

Any thoughts as to what could be causing this behavior are appreciated.  Last update to the system was done on Monday after a reboot.

---

