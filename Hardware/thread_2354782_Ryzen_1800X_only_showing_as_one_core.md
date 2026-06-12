---
title: "Ryzen 1800X only showing as one core"
date: 2017-03-06
forum: Hardware
---

### Post by mgilbertnz on 2017-03-06
Hi there,

I've got an AMD Ryzen 7 1800X Eight-Core Processor and I'm running kubuntu 17.04-beta1.

I've upgraded the kernel to 4.10.1-041001-generic
Motherboard is GA-AX370-Gaming 5 with F3 BIOS.

Previously, Intel CPU's would show one entry per core for cat /proc/cpuinfo.  

My Ryzen chip only shows as one core / thread.  Is this normal?  It doesn't seem to be performing like an 8 core but more like a single core running at 3.6GHz.  Any insights into what's going on would be appreciated.

[FONT=monospace][COLOR=#000000]cat /proc/cpuinfo[/COLOR]
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 23
model           : 1
model name      : AMD Ryzen 7 1800X Eight-Core Processor
stepping        : 1
microcode       : 0x8001105
cpu MHz         : 3592.792
cache size      : 512 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb 
rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c
 rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw skinit wdt tce topoext perfctr_core perfctr_nb bpext perfctr_l2
 mwaitx hw_pstate vmmcall fsgsbase bmi1 avx2 smep bmi2 rdseed adx smap clflushopt sha_ni xsaveopt xsavec xgetbv1 xsaves clzero irperf arat npt lbrv svm_lo
ck nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic overflow_recov succor smca
bugs            : fxsave_leak sysret_ss_attrs null_seg
bogomips        : 7185.58
TLB size        : 2560 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 48 bits physical, 48 bits virtual
power management: ts ttp tm hwpstate eff_freq_ro [13] [14]

[/FONT]

---

### Post by mgilbertnz on 2017-03-06
Searching the internet I see that cat /proc/cpuinfo is reported as 16 separate CPU's for others.

[http://openbenchmarking.org/system/1703021-RI-AMDZEN08075/Ryzen%207%201800X/cpuinfo](http://openbenchmarking.org/system/1703021-RI-AMDZEN08075/Ryzen%207%201800X/cpuinfo)

Could this be a hardware issue?  Any suggestions on how to troubleshoot this would be greatly appreciated.

Cheers,

Matt

---

### Post by cariboo on 2017-03-06
I'd suggest trying a newer kernel. Have look here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.11-rc1/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.11-rc1/)

btw, Ubuntu's 4.10 kernel is actually based on the 4.9 kernel

---

### Post by P-I H on 2017-03-12
Works quite OK with Unity on an updated Zesty. Sensors are missing.

```
p-i@pi-MSI-B350-Tomahawk-Kingstone:~$ uname -r
4.10.0-11-generic
p-i@pi-MSI-B350-Tomahawk-Kingstone:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Zesty Zapus (development branch)
Release:    17.04
Codename:    zesty
p-i@pi-MSI-B350-Tomahawk-Kingstone:~$ 

p-i@pi-MSI-B350-Tomahawk-Kingstone:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 23
model        : 1
model name    : AMD Ryzen 7 1700 Eight-Core Processor
stepping    : 1
microcode    : 0x8001105
cpu MHz        : 1550.000
cache size    : 512 KB
physical id    : 0
siblings    : 16
core id        : 0
cpu cores    : 8
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw skinit wdt tce topoext perfctr_core perfctr_nb bpext perfctr_l2 mwaitx hw_pstate vmmcall fsgsbase bmi1 avx2 smep bmi2 rdseed adx smap clflushopt sha_ni xsaveopt xsavec xgetbv1 xsaves clzero irperf arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic overflow_recov succor smca
bugs        : fxsave_leak sysret_ss_attrs null_seg
bogomips    : 7186.10
TLB size    : 2560 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm hwpstate eff_freq_ro [13] [14]

processor    : 1
vendor_id    : AuthenticAMD
cpu family    : 23
model        : 1
model name    : AMD Ryzen 7 1700 Eight-Core Processor
stepping    : 1
microcode    : 0x8001105
cpu MHz        : 1550.000
cache size    : 512 KB
physical id    : 0
siblings    : 16
core id        : 0
cpu cores    : 8
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw skinit wdt tce topoext perfctr_core perfctr_nb bpext perfctr_l2 mwaitx hw_pstate vmmcall fsgsbase bmi1 avx2 smep bmi2 rdseed adx smap clflushopt sha_ni xsaveopt xsavec xgetbv1 xsaves clzero irperf arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic overflow_recov succor smca
bugs        : fxsave_leak sysret_ss_attrs null_seg
bogomips    : 7186.10
TLB size    : 2560 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm hwpstate eff_freq_ro [13] [14]

processor    : 2
vendor_id    : AuthenticAMD
cpu family    : 23
model        : 1
model name    : AMD Ryzen 7 1700 Eight-Core Processor
stepping    : 1
microcode    : 0x8001105
cpu MHz        : 1550.000
cache size    : 512 KB
physical id    : 0
siblings    : 16
core id        : 1
cpu cores    : 8
apicid        : 2
initial apicid    : 2
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw skinit wdt tce topoext perfctr_core perfctr_nb bpext perfctr_l2 mwaitx hw_pstate vmmcall fsgsbase bmi1 avx2 smep bmi2 rdseed adx smap clflushopt sha_ni xsaveopt xsavec xgetbv1 xsaves clzero irperf arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic overflow_recov succor smca
bugs        : fxsave_leak sysret_ss_attrs null_seg
bogomips    : 7186.10
TLB size    : 2560 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm hwpstate eff_freq_ro [13] [14]

processor    : 3
vendor_id    : AuthenticAMD
cpu family    : 23
model        : 1
model name    : AMD Ryzen 7 1700 Eight-Core Processor
stepping    : 1
microcode    : 0x8001105
cpu MHz        : 1550.000
cache size    : 512 KB
physical id    : 0
siblings    : 16
core id        : 1
cpu cores    : 8
apicid        : 3
initial apicid    : 3
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw skinit wdt tce topoext perfctr_core perfctr_nb bpext perfctr_l2 mwaitx hw_pstate vmmcall fsgsbase bmi1 avx2 smep bmi2 rdseed adx smap clflushopt sha_ni xsaveopt xsavec xgetbv1 xsaves clzero irperf arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic overflow_recov succor smca
bugs        : fxsave_leak sysret_ss_attrs null_seg
bogomips    : 7186.10
TLB size    : 2560 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm hwpstate eff_freq_ro [13] [14]

processor    : 4
vendor_id    : AuthenticAMD
cpu family    : 23
model        : 1
model name    : AMD Ryzen 7 1700 Eight-Core Processor
stepping    : 1
microcode    : 0x8001105
cpu MHz        : 1550.000
cache size    : 512 KB
physical id    : 0
siblings    : 16
core id        : 2
cpu cores    : 8
apicid        : 4
initial apicid    : 4
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw skinit wdt tce topoext perfctr_core perfctr_nb bpext perfctr_l2 mwaitx hw_pstate vmmcall fsgsbase bmi1 avx2 smep bmi2 rdseed adx smap clflushopt sha_ni xsaveopt xsavec xgetbv1 xsaves clzero irperf arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic overflow_recov succor smca
bugs        : fxsave_leak sysret_ss_attrs null_seg
bogomips    : 7186.10
TLB size    : 2560 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm hwpstate eff_freq_ro [13] [14]

processor    : 5
vendor_id    : AuthenticAMD
cpu family    : 23
model        : 1
model name    : AMD Ryzen 7 1700 Eight-Core Processor
stepping    : 1
microcode    : 0x8001105
cpu MHz        : 1550.000
cache size    : 512 KB
physical id    : 0
siblings    : 16
core id        : 2
cpu cores    : 8
apicid        : 5
initial apicid    : 5
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw skinit wdt tce topoext perfctr_core perfctr_nb bpext perfctr_l2 mwaitx hw_pstate vmmcall fsgsbase bmi1 avx2 smep bmi2 rdseed adx smap clflushopt sha_ni xsaveopt xsavec xgetbv1 xsaves clzero irperf arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic overflow_recov succor smca
bugs        : fxsave_leak sysret_ss_attrs null_seg
bogomips    : 7186.10
TLB size    : 2560 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm hwpstate eff_freq_ro [13] [14]

processor    : 6
vendor_id    : AuthenticAMD
cpu family    : 23
model        : 1
model name    : AMD Ryzen 7 1700 Eight-Core Processor
stepping    : 1
microcode    : 0x8001105
cpu MHz        : 1550.000
cache size    : 512 KB
physical id    : 0
siblings    : 16
core id        : 3
cpu cores    : 8
apicid        : 6
initial apicid    : 6
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw skinit wdt tce topoext perfctr_core perfctr_nb bpext perfctr_l2 mwaitx hw_pstate vmmcall fsgsbase bmi1 avx2 smep bmi2 rdseed adx smap clflushopt sha_ni xsaveopt xsavec xgetbv1 xsaves clzero irperf arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic overflow_recov succor smca
bugs        : fxsave_leak sysret_ss_attrs null_seg
bogomips    : 7186.10
TLB size    : 2560 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm hwpstate eff_freq_ro [13] [14]

processor    : 7
vendor_id    : AuthenticAMD
cpu family    : 23
model        : 1
model name    : AMD Ryzen 7 1700 Eight-Core Processor
stepping    : 1
microcode    : 0x8001105
cpu MHz        : 1550.000
cache size    : 512 KB
physical id    : 0
siblings    : 16
core id        : 3
cpu cores    : 8
apicid        : 7
initial apicid    : 7
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw skinit wdt tce topoext perfctr_core perfctr_nb bpext perfctr_l2 mwaitx hw_pstate vmmcall fsgsbase bmi1 avx2 smep bmi2 rdseed adx smap clflushopt sha_ni xsaveopt xsavec xgetbv1 xsaves clzero irperf arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic overflow_recov succor smca
bugs        : fxsave_leak sysret_ss_attrs null_seg
bogomips    : 7186.10
TLB size    : 2560 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm hwpstate eff_freq_ro [13] [14]

processor    : 8
vendor_id    : AuthenticAMD
cpu family    : 23
model        : 1
model name    : AMD Ryzen 7 1700 Eight-Core Processor
stepping    : 1
microcode    : 0x8001105
cpu MHz        : 1550.000
cache size    : 512 KB
physical id    : 0
siblings    : 16
core id        : 4
cpu cores    : 8
apicid        : 8
initial apicid    : 8
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw skinit wdt tce topoext perfctr_core perfctr_nb bpext perfctr_l2 mwaitx hw_pstate vmmcall fsgsbase bmi1 avx2 smep bmi2 rdseed adx smap clflushopt sha_ni xsaveopt xsavec xgetbv1 xsaves clzero irperf arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic overflow_recov succor smca
bugs        : fxsave_leak sysret_ss_attrs null_seg
bogomips    : 7186.10
TLB size    : 2560 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm hwpstate eff_freq_ro [13] [14]

processor    : 9
vendor_id    : AuthenticAMD
cpu family    : 23
model        : 1
model name    : AMD Ryzen 7 1700 Eight-Core Processor
stepping    : 1
microcode    : 0x8001105
cpu MHz        : 1550.000
cache size    : 512 KB
physical id    : 0
siblings    : 16
core id        : 4
cpu cores    : 8
apicid        : 9
initial apicid    : 9
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw skinit wdt tce topoext perfctr_core perfctr_nb bpext perfctr_l2 mwaitx hw_pstate vmmcall fsgsbase bmi1 avx2 smep bmi2 rdseed adx smap clflushopt sha_ni xsaveopt xsavec xgetbv1 xsaves clzero irperf arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic overflow_recov succor smca
bugs        : fxsave_leak sysret_ss_attrs null_seg
bogomips    : 7186.10
TLB size    : 2560 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm hwpstate eff_freq_ro [13] [14]

processor    : 10
vendor_id    : AuthenticAMD
cpu family    : 23
model        : 1
model name    : AMD Ryzen 7 1700 Eight-Core Processor
stepping    : 1
microcode    : 0x8001105
cpu MHz        : 1550.000
cache size    : 512 KB
physical id    : 0
siblings    : 16
core id        : 5
cpu cores    : 8
apicid        : 10
initial apicid    : 10
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw skinit wdt tce topoext perfctr_core perfctr_nb bpext perfctr_l2 mwaitx hw_pstate vmmcall fsgsbase bmi1 avx2 smep bmi2 rdseed adx smap clflushopt sha_ni xsaveopt xsavec xgetbv1 xsaves clzero irperf arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic overflow_recov succor smca
bugs        : fxsave_leak sysret_ss_attrs null_seg
bogomips    : 7186.10
TLB size    : 2560 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm hwpstate eff_freq_ro [13] [14]

processor    : 11
vendor_id    : AuthenticAMD
cpu family    : 23
model        : 1
model name    : AMD Ryzen 7 1700 Eight-Core Processor
stepping    : 1
microcode    : 0x8001105
cpu MHz        : 1550.000
cache size    : 512 KB
physical id    : 0
siblings    : 16
core id        : 5
cpu cores    : 8
apicid        : 11
initial apicid    : 11
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw skinit wdt tce topoext perfctr_core perfctr_nb bpext perfctr_l2 mwaitx hw_pstate vmmcall fsgsbase bmi1 avx2 smep bmi2 rdseed adx smap clflushopt sha_ni xsaveopt xsavec xgetbv1 xsaves clzero irperf arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic overflow_recov succor smca
bugs        : fxsave_leak sysret_ss_attrs null_seg
bogomips    : 7186.10
TLB size    : 2560 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm hwpstate eff_freq_ro [13] [14]

processor    : 12
vendor_id    : AuthenticAMD
cpu family    : 23
model        : 1
model name    : AMD Ryzen 7 1700 Eight-Core Processor
stepping    : 1
microcode    : 0x8001105
cpu MHz        : 1550.000
cache size    : 512 KB
physical id    : 0
siblings    : 16
core id        : 6
cpu cores    : 8
apicid        : 12
initial apicid    : 12
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw skinit wdt tce topoext perfctr_core perfctr_nb bpext perfctr_l2 mwaitx hw_pstate vmmcall fsgsbase bmi1 avx2 smep bmi2 rdseed adx smap clflushopt sha_ni xsaveopt xsavec xgetbv1 xsaves clzero irperf arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic overflow_recov succor smca
bugs        : fxsave_leak sysret_ss_attrs null_seg
bogomips    : 7186.10
TLB size    : 2560 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm hwpstate eff_freq_ro [13] [14]

processor    : 13
vendor_id    : AuthenticAMD
cpu family    : 23
model        : 1
model name    : AMD Ryzen 7 1700 Eight-Core Processor
stepping    : 1
microcode    : 0x8001105
cpu MHz        : 1550.000
cache size    : 512 KB
physical id    : 0
siblings    : 16
core id        : 6
cpu cores    : 8
apicid        : 13
initial apicid    : 13
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw skinit wdt tce topoext perfctr_core perfctr_nb bpext perfctr_l2 mwaitx hw_pstate vmmcall fsgsbase bmi1 avx2 smep bmi2 rdseed adx smap clflushopt sha_ni xsaveopt xsavec xgetbv1 xsaves clzero irperf arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic overflow_recov succor smca
bugs        : fxsave_leak sysret_ss_attrs null_seg
bogomips    : 7186.10
TLB size    : 2560 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm hwpstate eff_freq_ro [13] [14]

processor    : 14
vendor_id    : AuthenticAMD
cpu family    : 23
model        : 1
model name    : AMD Ryzen 7 1700 Eight-Core Processor
stepping    : 1
microcode    : 0x8001105
cpu MHz        : 1550.000
cache size    : 512 KB
physical id    : 0
siblings    : 16
core id        : 7
cpu cores    : 8
apicid        : 14
initial apicid    : 14
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw skinit wdt tce topoext perfctr_core perfctr_nb bpext perfctr_l2 mwaitx hw_pstate vmmcall fsgsbase bmi1 avx2 smep bmi2 rdseed adx smap clflushopt sha_ni xsaveopt xsavec xgetbv1 xsaves clzero irperf arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic overflow_recov succor smca
bugs        : fxsave_leak sysret_ss_attrs null_seg
bogomips    : 7186.10
TLB size    : 2560 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm hwpstate eff_freq_ro [13] [14]

processor    : 15
vendor_id    : AuthenticAMD
cpu family    : 23
model        : 1
model name    : AMD Ryzen 7 1700 Eight-Core Processor
stepping    : 1
microcode    : 0x8001105
cpu MHz        : 1550.000
cache size    : 512 KB
physical id    : 0
siblings    : 16
core id        : 7
cpu cores    : 8
apicid        : 15
initial apicid    : 15
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw skinit wdt tce topoext perfctr_core perfctr_nb bpext perfctr_l2 mwaitx hw_pstate vmmcall fsgsbase bmi1 avx2 smep bmi2 rdseed adx smap clflushopt sha_ni xsaveopt xsavec xgetbv1 xsaves clzero irperf arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic overflow_recov succor smca
bugs        : fxsave_leak sysret_ss_attrs null_seg
bogomips    : 7186.10
TLB size    : 2560 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm hwpstate eff_freq_ro [13] [14]

p-i@pi-MSI-B350-Tomahawk-Kingstone:~$
```

---

### Post by Yellow Pasque on 2017-03-12
> **mgilbertnz said:**
> My Ryzen chip only shows as one core / thread.  Is this normal?  It doesn't seem to be performing like an 8 core but more like a single core running at 3.6GHz.  Any insights into what's going on would be appreciated.

Check the "Downcore Control" in your BIOS. If it's set to "Auto", try manually setting it.

> Sensors are missing.

What sensor chip does the board have? If it's Nuvoton NCT679x, try manually loading the module:
```
sudo modprobe nct6775
sensors
```

Note that this is the Super I/O chip found in the board, so it may not be accurate with CPU temp. The CPU temp sensor built in to the CPU is not supported yet for Ryzen.

---

### Post by P-I H on 2017-03-12
Tried [COLOR=#000000][FONT=&amp]sudo modprobe nct6775
[/FONT][/COLOR]```
p-i@pi-MSI-B350-Tomahawk-Kingstone:~$ sudo modprobe nct6775
[sudo] password for p-i: 
modprobe: ERROR: could not insert 'nct6775': No such device
p-i@pi-MSI-B350-Tomahawk-Kingstone:~$ 

```

---

### Post by Yellow Pasque on 2017-03-12
Disregard this. I answered my own question.

---

### Post by Yellow Pasque on 2017-03-12
Okay, I see the motherboard has a Nuvoton NCT6795D. As far as I can tell, it is unsupported at the moment. Maybe you could report it to kernel bugzilla:
[https://bugzilla.kernel.org/buglist.cgi?component=Hardware%20Monitoring&product=Drivers&resolution=---](https://bugzilla.kernel.org/buglist.cgi?component=Hardware%20Monitoring&product=Drivers&resolution=---)

If we're lucky, it is very similar to other Nuvoton NCT679x chips, and minimal work will be needed to add support for it.

---

