---
title: "cpu not recognized as XP-M: Cpufreq not working"
date: 2008-10-04
forum: Hardware
---

### Post by jstateson on 2008-10-04
I have a pair of XP-M (mobile) Bartons running at 1867 in a desktop A7M266D, but they should be running at 2133.  Cpuinfo show the type is XP, not XP-M and I cannot get powernow-k7 to load.  I have both frequency monitors on the task bar, but they wont set any speed and when booting I get the error about the system being misconfigured and "frequency scaling unsupported". BTW, cpufreq is missing at cpu/cpu0/cpufreq and cpu/cpu1/cpufreq.

This mombo worked at 2133 when running windows XP and using crystalcpuid to set the multipliers.  Is there any way to force the powernow-k7 driver to load?  I have built kernels for RH9, but that was some time ago and I am no expert on ubuntu.

---

### Post by Calmatory on 2008-10-04
What does 

```
cat /proc/cpuinfo
```

show?

Does the kernel recognize it as Mobile?

---

### Post by jstateson on 2008-10-04
Thanks crematory - I tried the following
- aptget linux-k7
- added "powernow-k7" to that /etc/modules
- added sysfs           /sys    sysfs   defaults        0       0
  to fstab (googled that somewhere)

from modprobe -
root@jyslinux4:/etc# modprobe powernow-k7
FATAL: Error inserting powernow_k7 (/lib/modules/2.6.24-19-generic/kernel/arch/x86/kernel/cpu/cpufreq/powernow-k7.ko): No such device


jstateson@jyslinux4:/proc$ cat cpuinfo 
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 6
model		: 10
model name	: AMD Athlon(TM) XP
stepping	: 0
cpu MHz		: 1866.788
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow ts fid vid
bogomips	: 3737.60
clflush size	: 32

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 6
model		: 10
model name	: AMD Athlon(TM) XP
stepping	: 0
cpu MHz		: 1866.788
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow ts fid vid
bogomips	: 3733.83
clflush size	: 32

---

