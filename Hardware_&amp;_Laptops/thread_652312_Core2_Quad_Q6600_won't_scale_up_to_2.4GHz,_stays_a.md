---
title: "Core2 Quad Q6600 won't scale up to 2.4GHz, stays at 1.6Ghz"
date: 2007-12-28
forum: Hardware &amp; Laptops
---

### Post by radu_radu on 2007-12-28
I have a Intel Core2 Quad Q6600 CPU, and Ubuntu will keep it at 50% of its speed, no matter what I do. As you can see below, it has a "policy" to stick at 1.6 Ghz. I tried the CPU Frequency Scaling applet, which shows me both 2.4GHz and 1.6GHz freqs, but it won't go to 2.4.
Any idea on how to push my CPU back to 2.4GHz? (It works on that freq on Win, so it's not a hardware problem, I think).

```
root@Xanadu:~# cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 1.60 GHz - 2.40 GHz
  available frequency steps: 2.40 GHz, 1.60 GHz
  available cpufreq governors: userspace, conservative, ondemand, powersave, performance
  current policy: frequency should be within 1.60 GHz and 1.60 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.60 GHz (asserted by call to hardware).
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 1
  hardware limits: 1.60 GHz - 2.40 GHz
  available frequency steps: 2.40 GHz, 1.60 GHz
  available cpufreq governors: userspace, conservative, ondemand, powersave, performance
  current policy: frequency should be within 1.60 GHz and 1.60 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.60 GHz (asserted by call to hardware).
analyzing CPU 2:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 2
  hardware limits: 1.60 GHz - 2.40 GHz
  available frequency steps: 2.40 GHz, 1.60 GHz
  available cpufreq governors: userspace, conservative, ondemand, powersave, performance
  current policy: frequency should be within 1.60 GHz and 1.60 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.60 GHz (asserted by call to hardware).
analyzing CPU 3:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 3
  hardware limits: 1.60 GHz - 2.40 GHz
  available frequency steps: 2.40 GHz, 1.60 GHz
  available cpufreq governors: userspace, conservative, ondemand, powersave, performance
  current policy: frequency should be within 1.60 GHz and 1.60 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.60 GHz (asserted by call to hardware).

root@Xanadu:~# cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping        : 11
cpu MHz         : 1600.000
cache size      : 4096 KB
physical id     : 0
siblings        : 4
core id         : 0
cpu cores       : 4
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 4803.94
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping        : 11
cpu MHz         : 1600.000
cache size      : 4096 KB
physical id     : 0
siblings        : 4
core id         : 1
cpu cores       : 4
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 4799.96
clflush size    : 64

processor       : 2
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping        : 11
cpu MHz         : 1600.000
cache size      : 4096 KB
physical id     : 0
siblings        : 4
core id         : 2
cpu cores       : 4
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 4800.04
clflush size    : 64

processor       : 3
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping        : 11
cpu MHz         : 1600.000
cache size      : 4096 KB
physical id     : 0
siblings        : 4
core id         : 3
cpu cores       : 4
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 4800.03
clflush size    : 64

root@Xanadu:~# lsmod | grep cpu
acpi_cpufreq           10568  0
cpufreq_userspace       5280  0
cpufreq_conservative     8072  0
cpufreq_ondemand        9612  4
cpufreq_powersave       2688  0
cpufreq_stats           7232  0
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
processor              32072  2 acpi_cpufreq,thermal

```

---

### Post by jespdj on 2007-12-29
I had a similar problem on my dual-core E6600. I fixed it by editing the file /etc/init.d/cpufrequtils.

Find the line that says MAX_SPEED="" and change it to MAX_SPEED="2400MHz", and reboot.

---

### Post by radu_radu on 2007-12-29
Thank you, that worked!

---

### Post by -random on 2008-01-22
awesome thnkx!

:guitar:

---

### Post by juyanith on 2008-03-16
Hmmm... this is odd. I just built a new system with a Q6600 and it's doing the same thing, so I edited /etc/init.d/cpufrequtils as follows:
```

ENABLE="true"
GOVERNOR="ondemand"
MAX_SPEED="2400000"
MIN_SPEED="1600000"

```
When I run cpufreq-info I get: 
```

analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 1.60 GHz - 2.40 GHz
  available frequency steps: 2.40 GHz, 1.60 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 1.60 GHz and 2.40 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.60 GHz.

```

So, I try running mprime (4 instances, each set to a different core) and I can see the cpu jump to 2.4GHz in conky briefly before settling back to 1.6GHz. What gives? Wouldn't the "ondemand" governor see that all 4 cores are maxed out and stay at 2.4 GHz? What criteria does the "ondemand" governor use to determine when to adjust the frequency?

I tried the other governors but didn't get the results I want. If I set it to "performance" the cpu stays at 2.4GHz, while for all the others it stays at 1.6GHz. This is a fresh install of 7.10 if that matters. I'm kind of at a loss here...

---

### Post by juyanith on 2008-03-17
Bump... I've tried everything I can think of, but the cpu is never set to 2.4 GHz unless I use the "performance" governor. Any help is appreciated... 
:guitar:

---

### Post by djjaan on 2008-03-19
In BIOS, try to disable EIST (Enhanced Intel Speedstep Technology) or similar, and see if it helps.
I had the same situation, and I decided to switch it off. System: Kubuntu 7.10 64bit, Intel G33 chipset, Q6600, 4G RAM.

---

