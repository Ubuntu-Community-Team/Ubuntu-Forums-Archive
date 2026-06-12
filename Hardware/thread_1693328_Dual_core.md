---
title: "Dual core"
date: 2011-02-22
forum: Hardware
---

### Post by amalgamas on 2011-02-22
I searched for dual core and didn't really find anything relevant

I have a Dell inspiron 9300 with dual core processor.  cat /proc/cpuinfo gives the following:
```
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 13
model name    : Intel(R) Pentium(R) M processor 2.00GHz
stepping    : 8
cpu MHz        : 2000.000
cache size    : 2048 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts est tm2
bogomips    : 3989.78
clflush size    : 64
cache_alignment    : 64
address sizes    : 32 bits physical, 32 bits virtual
power management:

```
So it seems my ubuntu PC is using only one processor?  I need help to activate both processor cores.

---

### Post by grahammechanical on 2011-02-22
Try System>Administration>System Monitor. What do you see typed on the System tab? On my  machine I see Processor 0: Intel(R) core (TM) 2 CPU 6600 @2.40 GHz and underneath Processor 1: Intel(R) core (TM) 2 CPU 6600 @2.40 GHz.

I find that the OS switches between cores as it works. We may have two CPUs or more but do we have programs that can make use of them? The same applies to having a 64bit OS. Do we have programs that make use of the possibilities of having CPUs that use 64bit addressing or are they just programs that were designed for 32bit CPUs and have been modified sufficiently to run on a 64bit CPU?

By the way, who told you that you had a dual core CPU. From the listing it looks like a Pentium M.

Regards.

---

### Post by tgalati4 on 2011-02-22
Pentium M is a single core, 32-bit processor.  The good news is that it throttles processor speed and uses less power than the dual core chips.

---

