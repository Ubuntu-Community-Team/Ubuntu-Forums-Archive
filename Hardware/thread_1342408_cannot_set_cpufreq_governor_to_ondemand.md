---
title: "cannot set cpufreq governor to ondemand"
date: 2009-11-30
forum: Hardware
---

### Post by mathfeel on 2009-11-30
I cannot set cpufreq to ondemand. dmesg return the following error:
```
[151769.367171] ondemand governor failed, too long transition latency of HW, fallback to performance governor
```

It was working before upgrade to Karmic.

It seems like clockmod doesn't work with ondemand, but p4-clockmod is the only one that works with my CPU:
```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 13
model name	: Intel(R) Celeron(R) M processor          900MHz
stepping	: 8
cpu MHz		: 900.000
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts
bogomips	: 1800.00
clflush size	: 64
power management:
```

---

### Post by Rayaz on 2010-04-25
Neither can I, it worked perfectly on Jaunty!

Anyone?

---

### Post by ian dobson on 2010-04-25
Hi,

Looks like a kernel change to get around a hardware limitation (Slow clock switched on some CPU's which breaks the scheduler). Have a look here [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=536183](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=536183)

Regards
Ian Dobson

---

