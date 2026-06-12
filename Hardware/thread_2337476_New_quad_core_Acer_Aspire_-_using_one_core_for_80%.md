---
title: "New quad core Acer Aspire - using one core for 80% of all tasks?"
date: 2016-09-18
forum: Hardware
---

### Post by TechGhost on 2016-09-18
I bought a new Acer Aspire E5-574. Added 8GB more RAM and a new 1TB HDD, and obviously installed Ubuntu as the first thing. 

I run HTOP, and in there I see one core in specific (number 3) being the one used most of the time. Its always the one being used, and the consumption is when both FF and Thunderbird and other applications run, more than 60%, while the other 3 core jump between 20-30% on average, and sometimes are not even being used. 

Everything runs super smooth on my new laptop, but I wondered if there was a way to make better use of all cores, rather than just using one excessively. 

A few outputs to help the experts if anyone has suggestions. 

```

laptop@laptop-Aspire-E5-574:~$ lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                4
On-line CPU(s) list:   0-3
Thread(s) per core:    2
Core(s) per socket:    2
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 78
Model name:            Intel(R) Core(TM) i5-6200U CPU @ 2.30GHz
Stepping:              3
CPU MHz:               2600.250
CPU max MHz:           2700.0000
CPU min MHz:           400.0000
BogoMIPS:              4800.09
Virtualisation:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              3072K
NUMA node0 CPU(s):     0-3
Flags:                 fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch epb intel_pt tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt xsaveopt xsavec xgetbv1 dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp

```

```

laptop@laptop-Aspire-E5-574:~$ sudo lshw -class cpu
  *-cpu                   
       description: CPU
       product: Intel(R) Core(TM) i5-6200U CPU @ 2.30GHz
       vendor: Intel Corp.
       physical id: 4
       bus info: cpu@0
       version: Intel(R) Core(TM) i5-6200U CPU @ 2.30GHz
       serial: To Be Filled By O.E.M.
       slot: U3E1
       size: 2695MHz
       capacity: 2700MHz
       width: 64 bits
       clock: 100MHz
       capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch epb intel_pt tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt xsaveopt xsavec xgetbv1 dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp cpufreq
       configuration: cores=2 enabledcores=2 threads=4

```

Any suggestion is welcome to what I can do to spread the usage to all cores, if that is even possible?

---

