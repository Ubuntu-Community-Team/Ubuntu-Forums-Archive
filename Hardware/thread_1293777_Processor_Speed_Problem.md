---
title: "Processor Speed Problem"
date: 2009-10-17
forum: Hardware
---

### Post by snow_56767 on 2009-10-17
Hi Guys,
      I have a AMD Semperon LE-1300 processor. Linux is saying I only have 1.006 GHz when my processor is capable of 2.3 GHz. HOW DO I FIX THIS!?!?!?

I used the command cat /proc/cpuinfo to see if it was an application that was manipulating the speed of my processor. and I got this:

```

processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 127
model name	: AMD Sempron(tm) Processor LE-1300
stepping	: 2
cpu MHz		: 1000.000
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow up pni cx16 lahf_lm extapic cr8_legacy 3dnowprefetch
bogomips	: 2009.15
clflush size	: 64
power management: ts fid vid ttp tm stc 100mhzsteps

```

---

