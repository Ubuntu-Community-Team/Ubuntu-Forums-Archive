---
title: "CPU Freq Sacling not working on cpu 0 - core 2 duo 2.67ghz"
date: 2011-02-10
forum: Hardware
---

### Post by ghosthand on 2011-02-10
I recently upgraded to ubuntu 10.10 and have notice that my cpu freq scaling applet is stuck on 800mhz.  I tried to click on 2.67ghz but it doesn't change.  Weird thing is that if I go to the prefs and change it to monitor cpu 1, then I can change the cpu freq.  However, the freq of cpu 0 alwasy stays at 800mhz.  This is confirmed by `cat /proc/cpuinfo`.  I tried using `sudo cpufreq-selector -c 0 -f 267000` but it didn't do anything, just took a while to run and then exited with no output.  

I didn't even know that you could set the two cpu's to different frequencies...

It looks like everything is getting detected correctly, so I'm not sure what happened.  This problem was present under 10.04

$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     T9550  @ 2.66GHz
stepping	: 10
cpu MHz		: 800.000
cache size	: 6144 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm ida dts tpr_shadow vnmi flexpriority
bogomips	: 5319.74
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     T9550  @ 2.66GHz
stepping	: 10
cpu MHz		: 2666.000
cache size	: 6144 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm ida dts tpr_shadow vnmi flexpriority
bogomips	: 4346.38
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

---

