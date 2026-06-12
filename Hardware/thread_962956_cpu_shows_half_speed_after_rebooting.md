---
title: "cpu shows half speed after rebooting"
date: 2008-10-29
forum: Hardware
---

### Post by csc2ya on 2008-10-29
I'm running Ubuntu Ultimate Edition on my laptop which has a 1.6Ghz Intel Core 2 Duo (T5200) processor.

When I first startup or reboot my laptop, it reports the cpu speed as being half of what it should be:

irssi sysinfo script:

> Host 'Laptop', running Linux 2.6.24-21-generic - Cpu0: Intel 
                   800 MHz Cpu1: Intel 800 MHz; Up: 33 min; Users: 3; Load: 
                   0.44; Free: [Mem: 909/2018 MB] [Swap: 0/0 MB] [/: 
                   104549/118293 MB] [/media/Backups: 84562/119237 MB]; Vpenis: 
                   159.3 cm;


Results of cat /proc/cpuinfo:

> administrator@Laptop:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU         T5200  @ 1.60GHz
stepping	: 6
cpu MHz		: 800.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 3203.94
clflush size	: 64

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU         T5200  @ 1.60GHz
stepping	: 6
cpu MHz		: 800.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 3200.17
clflush size	: 64


If I do 'sudo /usr/bin/cpufreq-selector -f 1600000' in the terminal window, it then reports the full speed of 1600.000MHz.

It's then fine until I reboot.

Is there any way to get it to report the full speed after booting up/rebooting without having to run the frequency selector script every time?

---

