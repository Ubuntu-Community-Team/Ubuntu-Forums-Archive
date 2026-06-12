---
title: "Incorrect number of cores detected"
date: 2008-09-15
forum: Hardware
---

### Post by tareqsiraj on 2008-09-15
Hello everyone,
I have this Quad Quad-core machine running Hardy x86_64. Unfortunately, its only detecting 8 cores out of 16 cores. I tried a Fedora 8 x86_64 installation disk and did a cat /proc/cpuinfo in a ternimal and it detected all 16 cores. Do I need to enable any kernel flags when booting Hardy? Thanks in advance.

```

$ uname -a
Linux moriyama 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux

$ cat /proc/cpuinfo  | grep processor
processor	: 0
processor	: 1
processor	: 2
processor	: 3
processor	: 4
processor	: 5
processor	: 6
processor	: 7

 $ sudo lshw -C cpu
[sudo] password for tsiraj: 
  *-cpu:0                 
       description: CPU
       product: Quad-Core AMD Opteron(tm) Processor 8354
       vendor: Advanced Micro Devices [AMD]
       physical id: 3
       bus info: cpu@0
       version: 15.2.3
       serial: To Be Filled By O.E.M.
       slot: CPU 1
       size: 2200MHz
       capacity: 2200MHz
       width: 64 bits
       clock: 200MHz
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good pni cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
  *-cpu:1
       description: CPU
       product: Quad-Core AMD Opteron(tm) Processor 8354
       vendor: Advanced Micro Devices [AMD]
       physical id: 8
       bus info: cpu@1
       version: 15.2.3
       serial: To Be Filled By O.E.M.
       slot: CPU 2
       size: 2200MHz
       capacity: 2200MHz
       width: 64 bits
       clock: 200MHz
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good pni cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
  *-cpu:2
       description: CPU
       product: (To Be Filled By O.E.M.)
       vendor: AMD
       physical id: 4
       bus info: cpu@2
       version: 15.2.3
       serial: To Be Filled By O.E.M.
       slot: CPU 3
       size: 2200MHz
       capacity: 2200MHz
       clock: 200MHz
  *-cpu:3
       description: CPU
       product: (To Be Filled By O.E.M.)
       vendor: AMD
       physical id: 10
       bus info: cpu@3
       version: 15.2.3
       serial: To Be Filled By O.E.M.
       slot: CPU 4
       size: 2200MHz
       capacity: 2200MHz
       clock: 200MHz
  *-cpu:4 UNCLAIMED
       physical id: 7
       bus info: cpu@4
       version: 15.2.3
  <snip />
  *-cpu:14 UNCLAIMED
       physical id: 14
       bus info: cpu@14
       version: 15.2.3



```

---

### Post by sdennie on 2008-09-15
This is probably due to the kernel configuration only supporting up to 8 CPUs.  You could verify this with:

```

grep NR_CPU /boot/config-`uname -r`

```

If I'm not mistaken, even the server kernel has this value set to 8 so, I think get all 16 CPUs online, you'll have to build your own kernel.  I think the relevant option is in the "Processor Type and Features" section of the kernel config.

---

### Post by DoctorMO on 2008-09-15
Yea, I think you might need to compile your own kernel to get the best out of those.

---

### Post by tareqsiraj on 2008-09-15
yup... just finished compiling the kernel with 16 cpu support and it looks like working fine. Thanks for replying guys :)

---

