---
title: "cpufreq doesn't list max speed as an option"
date: 2010-01-17
forum: Hardware
---

### Post by Pro_D on 2010-01-17
Not sure if this is the right place but here goes...

I noticed that 9.10 on my desktop machine, CPU Frequency Scaling Monitor is not offering 3ghz as an option (see output from /proc/cpuinfo below for cpu details).  I seem to remember that there was a way to modify the available options for scaling as I had to do this on my server, which was being overclocked when it came under load (8.10).  I don't remember how to do this though and this was before I started trying to keep logs on linux tweaks.



What follows is my output from /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
stepping	: 10
cpu MHz		: 2000.000
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
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority
bogomips	: 5999.90
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
stepping	: 10
cpu MHz		: 2000.000
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
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority
bogomips	: 5999.31
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:




[edit]
cpufreq-set doesn't seem to let me change the max -no effect in settings available nor contents of scaling_max_freq.

[/edit]

[edit2]
*facepalm* after several days of booting and rebooting (odd problem I may ask about in a different thread where ubuntu just stops responding to all input, including ctrl-alt-F1) I noticed on the bios boot screen that my processor was underclocked.

I don't know how the heck that happened or when.  Double checked that I do have a 3 ghz proc and clocked it proper in the bios.  cpufreq is now showing 3ghz as an option (though I don't have many choices, just 2, 2ghz and 3ghz)...
[/edit2]

---

