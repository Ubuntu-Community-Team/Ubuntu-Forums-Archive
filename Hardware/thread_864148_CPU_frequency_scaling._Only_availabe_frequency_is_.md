---
title: "CPU frequency scaling. Only availabe frequency is top speed."
date: 2008-07-19
forum: Hardware
---

### Post by pergpau on 2008-07-19
Hello!

I have a problem concerning the CPU frequency scaling on my Compal laptop.

cat /proc/cpuinfo says:


```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz
stepping	: 6
cpu MHz		: 2400.000
cache size	: 3072 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm
bogomips	: 4793.12
clflush size	: 64

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz
stepping	: 6
cpu MHz		: 2400.000
cache size	: 3072 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm
bogomips	: 4787.99
clflush size	: 64

```


cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies says: ```
2400000 

```

My question is why is 2.4ghz the only option, and how can I get it to recognize other options? I have a Duo T8300, so "speedstepping" to a much lower freq shouldn't be a problem.

And I'm a complete beginner with linux, so if possible put things clearly and with commands for me to use. Thanks a heap!

---

### Post by ljonesj on 2008-07-19
there may be an option in bios called edst i think that controls freq scaling in bios or u need to install cpyfreq for intel or its powernod but i think that one is amd's version of a freq scalling programs

---

