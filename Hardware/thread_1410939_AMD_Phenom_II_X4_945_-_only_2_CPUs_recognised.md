---
title: "AMD Phenom II X4 945 - only 2 CPUs recognised"
date: 2010-02-19
forum: Hardware
---

### Post by yogurtu_ctes on 2010-02-19
Hi Everyone,
I'm having trouble with my ubuntu distro. I have a quad core CPU (AMD Phenom II X4 945), but it only uses two cores.
I'm using ubuntu karmic, fully up to date. I upgraded my BIOS yesterday to see if that is the problem.
My mother board is a Gigabyte GA-MA790FXT-UD5P

Here's my "dmesg | grep -i cpu":
> [    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] KERNEL supported cpus:
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] **SMP: Allowing 4 CPUs, 2 hotplug CPUs**
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages at ffff880028022000, static data 90720 bytes
[    0.000000] Initializing CPU#0
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.009146] HPET: 4 timers in total, 1 timers will be used for per-cpu timer
[    0.011799] Initializing cgroup subsys cpuacct
[    0.011814] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.011816] CPU: L2 Cache: 512K (64 bytes/line)
[    0.011818] CPU 0/0x0 -> Node 0
[    0.011821] CPU: Physical Processor ID: 0
[    0.011822] CPU: Processor Core ID: 0
[    0.011824] mce: CPU supports 6 MCE banks
[    0.125847] CPU0: AMD Phenom(tm) II X4 945 Processor stepping 02
[    0.010000] Initializing CPU#1
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU 1/0x1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.280829] CPU1: AMD Phenom(tm) II X4 945 Processor stepping 02
[    0.280835] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.290008] **Brought up 2 CPUs**
[    0.290099] CPU0 attaching sched-domain:
[    0.290106] CPU1 attaching sched-domain:
[    0.500794] Switched to high resolution mode on CPU 1
[    0.510018] Switched to high resolution mode on CPU 0
[    0.710788] processor LNXCPU:00: registered as cooling_device0
[    0.710816] processor LNXCPU:01: registered as cooling_device1
[    1.350552] cpuidle: using governor ladder
[    1.350553] cpuidle: using governor menu
[    1.351358] powernow-k8: Found 1 AMD Phenom(tm) II X4 945 Processor processors (2 cpu cores) (version 2.20.00)
[   23.773319] CPU0 attaching NULL sched-domain.
[   23.773323] CPU1 attaching NULL sched-domain.
[   23.811315] CPU0 attaching sched-domain:
[   23.811324] CPU1 attaching sched-domain:
Here's my: "cat /proc/cpuinfo":
> processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 4
model name    : AMD Phenom(tm) II X4 945 Processor
stepping    : 2
cpu MHz        : 3000.000
cache size    : 512 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
bogomips    : 6042.58
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor    : 1
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 4
model name    : AMD Phenom(tm) II X4 945 Processor
stepping    : 2
cpu MHz        : 3000.000
cache size    : 512 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
bogomips    : 6042.62
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate
Please help :)
Thanks in advance

---

### Post by yogurtu_ctes on 2010-02-19
After updating my BIOS, there was a new option, which by default **DISABLED** two CPUs.
Thank you all.

---

