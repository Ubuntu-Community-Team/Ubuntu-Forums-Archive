---
title: "No power scaling AMD Turion"
date: 2008-06-11
forum: Hardware
---

### Post by rado3105 on 2008-06-11
Hi power scaling doesnt work on my notebook asus with AMD Turion processor(one core) also doesnt work battery/adapter indicator.Problem with acpi? Can you help?

---

### Post by rado3105 on 2008-06-12
PLEASE DELETE DOUBLE POST OR HOW TO DELETE

This is output using *lsmod | grep cpu*
> cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8712  0 
[I]
lsmod | grep power[/I]
> cpufreq_powersave       2688  0 

*dmesg | grep powernow*
> [   59.831474] powernow_k8: Unknown symbol acpi_processor_notify_smm
[   59.831586] powernow_k8: Unknown symbol acpi_processor_unregister_performance
[   59.831789] powernow_k8: Unknown symbol acpi_processor_register_performance

*cat /proc/cpuinfo*
> processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 36
model name	: AMD Turion(tm) 64 Mobile Technology MT-32
stepping	: 2
cpu MHz		: 800.054
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm ts fid vid ttp tm stc
bogomips	: 1601.47
clflush size	: 64

*cat /proc/acpi/processor/CPU0/info*
it shows that this file doesnt exist,then I tried to get using cd to acpi folder cd /proc/acpi
and also showed that doesnt exist, can you help how to install acpi,or solve this problem

---

### Post by rado3105 on 2008-06-12
This is output using *lsmod | grep cpu*
> cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8712  0 
[I]
lsmod | grep power[/I]
> cpufreq_powersave       2688  0 

*dmesg | grep powernow*
> [   59.831474] powernow_k8: Unknown symbol acpi_processor_notify_smm
[   59.831586] powernow_k8: Unknown symbol acpi_processor_unregister_performance
[   59.831789] powernow_k8: Unknown symbol acpi_processor_register_performance

*cat /proc/cpuinfo*
> processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 36
model name	: AMD Turion(tm) 64 Mobile Technology MT-32
stepping	: 2
cpu MHz		: 800.054
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm ts fid vid ttp tm stc
bogomips	: 1601.47
clflush size	: 64

*lsmod | grep acpi*
> pata_acpi               8320  0 
libata                159344  3 pata_sis,pata_acpi,ata_generic

*cat /proc/acpi/processor/CPU0/info*
it shows that this file doesnt exist,then I tried to get using cd to acpi folder cd /proc/acpi
and also showed that doesnt exist, can you help how to install acpi,or solve this problem

---

