---
title: "AMD A8-3500M Turbo Boost Doesn't Work - How to Enable?"
date: 2013-05-11
forum: Hardware
---

### Post by ugurbor on 2013-05-11
Hi,

I have recently replaced my A4-3300M with a A8-3500M. The APU's default speed is 1.5GHz. However it can overclock itself to 2.4GHz when needed. 

I was testing this feature with cpuburn (cpu stress test -makes cpu usage 99) and cpufreq-aperf (to see real speed of cores). But it never goes further than ~1.5GHz. I don't know how to enable it.

Oh, and I am not a complete beginner on Ubuntu. I have been  using it for 8 months for programming (Java, C/C++, Perl etc.) and daily  usage like office and internet. But I am a real noob at this kind of  hardware/kernel related stuff.

Here's my cpuinfo:
```
ugur@ugur-K53TA:~$ cat /proc/cpuinfo 
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 18
model        : 1
model name    : AMD A8-3500M APU with Radeon(tm) HD Graphics
stepping    : 0
microcode    : 0x3000027
cpu MHz        : 1500.000
cache size    : 1024 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 4
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 6
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt arat cpb hw_pstate npt lbrv svm_lock nrip_save pausefilter
bogomips    : 2994.54
TLB size    : 1536 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate cpb

processor    : 1
vendor_id    : AuthenticAMD
cpu family    : 18
model        : 1
model name    : AMD A8-3500M APU with Radeon(tm) HD Graphics
stepping    : 0
microcode    : 0x3000027
cpu MHz        : 1500.000
cache size    : 1024 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 4
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 6
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt arat cpb hw_pstate npt lbrv svm_lock nrip_save pausefilter
bogomips    : 2994.54
TLB size    : 1536 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate cpb

processor    : 2
vendor_id    : AuthenticAMD
cpu family    : 18
model        : 1
model name    : AMD A8-3500M APU with Radeon(tm) HD Graphics
stepping    : 0
microcode    : 0x3000027
cpu MHz        : 1500.000
cache size    : 1024 KB
physical id    : 0
siblings    : 4
core id        : 2
cpu cores    : 4
apicid        : 2
initial apicid    : 2
fpu        : yes
fpu_exception    : yes
cpuid level    : 6
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt arat cpb hw_pstate npt lbrv svm_lock nrip_save pausefilter
bogomips    : 2994.54
TLB size    : 1536 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate cpb

processor    : 3
vendor_id    : AuthenticAMD
cpu family    : 18
model        : 1
model name    : AMD A8-3500M APU with Radeon(tm) HD Graphics
stepping    : 0
microcode    : 0x3000027
cpu MHz        : 1500.000
cache size    : 1024 KB
physical id    : 0
siblings    : 4
core id        : 3
cpu cores    : 4
apicid        : 3
initial apicid    : 3
fpu        : yes
fpu_exception    : yes
cpuid level    : 6
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt arat cpb hw_pstate npt lbrv svm_lock nrip_save pausefilter
bogomips    : 2994.54
TLB size    : 1536 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate cpb
```

and cpufreq-aperf on stress:
```
ugur@ugur-K53TA:~$ sudo cpufreq-aperf 
[sudo] password for ugur: 
CPU    Average freq(KHz)    Time in C0    Time in Cx    C0 percentage
000    1335000            00 sec 998 ms    00 sec 001 ms    99
001    1335000            00 sec 998 ms    00 sec 001 ms    99
002    1335000            00 sec 998 ms    00 sec 001 ms    99
003    1335000            00 sec 998 ms    00 sec 001 ms    99

000    1320000            00 sec 998 ms    00 sec 001 ms    99
001    1320000            00 sec 998 ms    00 sec 001 ms    99
002    1320000            00 sec 998 ms    00 sec 001 ms    99
003    1320000            00 sec 998 ms    00 sec 001 ms    99

000    1335000            00 sec 998 ms    00 sec 001 ms    99
001    1335000            00 sec 998 ms    00 sec 001 ms    99
002    1335000            00 sec 998 ms    00 sec 001 ms    99
003    1335000            00 sec 998 ms    00 sec 001 ms    99
```

---

### Post by mörgæs on 2013-05-12
You might get a better response in a dedicated forum for AMD.

---

### Post by Yellow Pasque on 2013-05-12
cpufreq doesn't show Intel's turbo boost (need a special utility called i7k to see it). It may be the same for AMD turbo.

---

### Post by ugurbor on 2013-05-12
> **Temüjin said:**
> cpufreq doesn't show Intel's turbo boost (need a special utility called i7k to see it). It may be the same for AMD turbo.

Normally nobody can see the real frequency of the cpu on cpufreq-info, but cpufreq-aperf shows the real frequency and if it's working i should be seeing it.

---

