---
title: "Temporary One Core at a Dual Core"
date: 2010-02-12
forum: Hardware
---

### Post by H(a)iFlo on 2010-02-12
Hi,

since some weeks i have the problem, that my system sometimes is working with only one core of my Dual Core. The other core is not detected by the system. If i do a reboot, sometimes my system is able to work with both cores.

I tried to downgrade my Bios and get another linux core(2.6.31 to 2.6.32). Nothing :(

Here some facts about my system:

    description: Desktop Computer
    product: GA-MA770-UD3
    vendor: Gigabyte Technology Co., Ltd.
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop uuid=30303234-3144-3836-3643-4130FFFFFFFF
  *-cpu
       description: CPU
       product: AMD Athlon(tm) II X2 245 Processor
       vendor: Advanced Micro Devices [AMD]
       physical id: 4
       bus info: cpu@0
       version: AMD Athlon(tm) II X2 245 Processor
       slot: Socket M2
       size: 2900MHz
       capacity: 3200MHz
       width: 64 bits
       clock: 200MHz
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt cpufreq

**_With one Core_**

cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 16
model           : 6
model name      : AMD Athlon(tm) II X2 245 Processor
stepping        : 2
cpu MHz         : 800.000
cache size      : 1024 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
bogomips        : 5826.38
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

_**With two working Cores**_

  	 	 	 	 	 	  cpuinfo  processor       : 0                                                                                                                             vendor_id       : AuthenticAMD                                                                                                                  cpu family      : 16                                                                                                                            model           : 6                                                                                                                             model name      : AMD Athlon(tm) II X2 245 Processor                                                                                            stepping        : 2                                                                                                                             cpu MHz         : 2900.000                                                                                                                      cache size      : 1024 KB                                                                                                                       physical id     : 0                                                                                                                             siblings        : 2                                                                                                                             core id         : 0                                                                                                                             cpu cores       : 2                                                                                                                             apicid          : 0                                                                                                                             initial apicid  : 0                                                                                                                             fpu             : yes                                                                                                                           fpu_exception   : yes                                                                                                                           cpuid level     : 5                                                                                                                             wp              : yes                                                                                                                           flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt bogomips        : 5826.32 TLB size        : 1024 4K pages clflush size    : 64 cache_alignment : 64 address sizes   : 48 bits physical, 48 bits virtual power management: ts ttp tm stc 100mhzsteps hwpstate  processor       : 1 vendor_id       : AuthenticAMD cpu family      : 16 model           : 6 model name      : AMD Athlon(tm) II X2 245 Processor stepping        : 2 cpu MHz         : 800.000 cache size      : 1024 KB physical id     : 0 siblings        : 2 core id         : 1 cpu cores       : 2 apicid          : 1 initial apicid  : 1 fpu             : yes fpu_exception   : yes cpuid level     : 5 wp              : yes flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt bogomips        : 5824.76 TLB size        : 1024 4K pages clflush size    : 64 cache_alignment : 64 address sizes   : 48 bits physical, 48 bits virtual power management: ts ttp tm stc 100mhzsteps hwpstate 
It would be nice, if someone is able to help me.

Thanks!

---

### Post by jimbob on 2010-02-17
When I run the command I get the same output every time.  How did you get the one core output?

/home/jaspmatt# cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 6
model name	: AMD Athlon(tm) II X2 240 Processor
stepping	: 2
cpu MHz		: 800.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
bogomips	: 5600.59
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 6
model name	: AMD Athlon(tm) II X2 240 Processor
stepping	: 2
cpu MHz		: 800.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
bogomips	: 5600.09
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

---

