---
title: "Intel Atom D2500 CPU stepping not available on Ubuntu Server 12.04.2 LTS"
date: 2013-07-15
forum: Hardware
---

### Post by dns809 on 2013-07-15
Hello,

I am glad to be posting here for the first time.

Ubuntu has been doing a great job for me in terms of basic server applications. However my server is inactive most of the time and being a small box with minimum ventilation it gets hot quickly even if it is not in use.

I have installed Ubuntu Server on this Atom D2500 Machine and when i issue the command **cat /proc/cpuinfo** :
```

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 54
model name      : Intel(R) Atom(TM) CPU D2500   @ 1.86GHz
stepping        : 1
microcode       : 0x10d
cpu MHz         : 1866.668
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
apicid          : 1
initial apicid  : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm arat dtherm
bogomips        : 3733.33
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:
```

I always get the full clock speed listed even if the server is on idle (1.86GHz).

Is there any way to enable the CPU stepping function to lower the voltage and frequency to a certain state while the server is on idle? I cannot manage to find a right way to do this with my Atom Cedarview system.

Thank you very much for your time.

---

### Post by Yellow Pasque on 2013-07-16
> Is there any way to enable the CPU stepping function to lower the voltage and frequency to a certain state while the server is on idle?
No, you're SOL on that one. The Atom 'D' chips don't support Speedstep.

---

### Post by dns809 on 2013-07-16
I should have researched that before getting one >_< So no under-clock either?


Is the stepping usually enabled by default on Ubuntu Server distributions?


Thanks for the info hehe

---

### Post by Yellow Pasque on 2013-07-18
> **dns809 said:**
> So no under-clock either?
[http://sol.urbanup.com/1675643](http://sol.urbanup.com/1675643)
:)

> Is the stepping usually enabled by default on Ubuntu Server distributions?
Yes, the ondemand cpufreq governor is still used as default as far as I'm aware.

---

