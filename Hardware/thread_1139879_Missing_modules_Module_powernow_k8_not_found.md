---
title: "Missing modules? Module powernow_k8 not found"
date: 2009-04-27
forum: Hardware
---

### Post by Naguz on 2009-04-27
I am trying to install cpufreqd now, but to no avail. I have installed the cpufreqd-package, which pulled in the the libcpufreq0 as a dep.

The problem, however, is that 
"sudo modprobe powernow-k8" gives the result 
"FATAL: Module powernow_k8 not found."

I find this strange, I tought it was supposed to fail  with something like "(/lib/modules/...../cpu/cpufreq/powernow-k8.ko):
No such device"" When you loaded the wrong module. Even stranger, powernow_k7 and acpi_cpufreq not found also gives the same error.

modprobe -l |grep power    gives:
kernel/arch/x86/kernel/cpu/cpufreq/e_powersaver.ko
kernel/drivers/char/ipmi/ipmi_poweroff.ko
kernel/drivers/input/misc/powermate.ko
kernel/drivers/power/pda_power.ko
kernel/drivers/power/ds2760_battery.ko
kernel/drivers/power/olpc_battery.ko
kernel/drivers/power/bq27x00_battery.ko
so indeed, there seems like there is no powernow module at all.
Yet:
gert@htpc:~$ dmesg |grep powernow
[    3.626207] powernow-k8: Found 1 AMD Athlon(tm) 7750 Dual-Core Processor processors (2 cpu cores) (version 2.20.00)
[    3.626241] powernow-k8:    0 : pstate 0 (2700 MHz)
[    3.626243] powernow-k8:    1 : pstate 1 (1400 MHz)
Whaaat? :confused:

As for the givem value, I don't understand them either-
cpufreq-info says both cpus is at 2.7Ghz, and setting them to something else with cpufreq-set or f.eks. "cpufreq-selector -g ondemand" does not make a difference.

Is seriously wrong, or am I just being stupid/missing something?

Running Jaunty with latest updates. Cpu-info:

gert@htpc:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 2
model name	: AMD Athlon(tm) 7750 Dual-Core Processor
stepping	: 3
cpu MHz		: 2700.000
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
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc pni monitor cx16 lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips	: 5400.51
clflush size	: 64
power management: ts ttp tm stc 100mhzsteps hwpstate

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 2
model name	: AMD Athlon(tm) 7750 Dual-Core Processor
stepping	: 3
cpu MHz		: 2700.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc pni monitor cx16 lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips	: 5400.03
clflush size	: 64
power management: ts ttp tm stc 100mhzsteps hwpstate

---

