---
title: "Turion X2 and C states"
date: 2008-12-09
forum: Hardware
---

### Post by felipefoz on 2008-12-09
I have a AMD Turion X2 Mobile TL-58 and powertop doesn't recognize more than c1 state, but as I've read turion is capable of higher c states.
Does anyone know it is all right? Powertop PrintSc attached!

```
cat /proc/cpuinfo 
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 104
model name	: AMD Turion(tm) 64 X2 Mobile Technology TL-58
stepping	: 1
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips	: 1600.10
clflush size	: 64
power management: ts fid vid ttp tm stc 100mhzsteps

processor	: 1
vendor_id	: AuthenticAMD
..... same as above

```

```
 cat /proc/acpi/processor/CPU0/info
processor id:            0
acpi id:                 0
bus mastering control:   yes
power management:        yes
throttling control:      yes
limit interface:         yes

```
```
cat /proc/acpi/processor/CPU0/power
active state:            C0
max_cstate:              C1
bus master activity:     00000000
maximum allowed latency: 2000000000 usec
states:
    C1:                  type[C1] promotion[--] demotion[--] latency[000] usage[00183663] duration[00000000000000000000]
    C2:                  type[C2] promotion[--] demotion[--] latency[005] usage[00000000] duration[00000000000000000000]
    C3:                  type[C3] promotion[--] demotion[--] latency[020] usage[00000000] duration[00000000000000000000]

```
```
cat /proc/acpi/processor/CPU0/throttling 
state count:             8
active state:            T0
state available: T0 to T7
states:
   *T0:                  100%
    T1:                  87%
    T2:                  75%
    T3:                  62%
    T4:                  50%
    T5:                  37%
    T6:                  25%
    T7:                  12%

```

---

