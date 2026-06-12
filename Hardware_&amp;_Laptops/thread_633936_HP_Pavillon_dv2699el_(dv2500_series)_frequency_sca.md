---
title: "HP Pavillon dv2699el (dv2500 series): frequency scaling unsupported - high CPU temps"
date: 2007-12-07
forum: Hardware &amp; Laptops
---

### Post by icest0rm on 2007-12-07
Hi,
I'm running Ubuntu Gutsy 64 and can't scale frequency on my C2D T7500...
this is a bad behaviour since CPU runs hot (always between 70-80°C) and the fan it's always spinning...

I'm wondering what can be the problem...bios? (i've already updated to latest available so in this case I think I can't do anything) or something else...

some info:

brex@ubuntu-box:~$ uname -a
Linux ubuntu-box 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux

brex@ubuntu-box:~$ cat /proc/cpuinfo 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
stepping        : 11
cpu MHz         : 2194.742
cache size      : 4096 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 4393.78
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
stepping        : 11
cpu MHz         : 2194.742
cache size      : 4096 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 4389.63
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

brex@ubuntu-box:~$ lsmod | grep -i cpufreq_stats
cpufreq_stats           8160  0 
freq_table              6464  2 cpufreq_stats,cpufreq_ondemand

brex@ubuntu-box:~$ sudo modprobe acpi_cpufreq
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.22-14-generic/kernel/arch/x86_64/kernel/cpufreq/acpi-cpufreq.ko): No such device

(same behaviour for similar modules)

---

### Post by icest0rm on 2007-12-07
if useful:

brex@ubuntu-box:~$ ls /sys/devices/system/cpu/
cpu0  cpu1  sched_mc_power_savings

so nothing about frequency scaling

---

### Post by icest0rm on 2007-12-08
bump

---

### Post by icest0rm on 2007-12-10
no-one experiencing the same problem?

do you know where I can get more support on this?

do I need to open a bug ticket?

thanks

---

### Post by icest0rm on 2007-12-12
bump

---

### Post by antoniorc on 2008-05-17
Hi,

I've same problem. Have found you some solution?

---

### Post by icest0rm on 2008-05-18
yes, use latest bios, the issue has been fixed on it

---

### Post by jethai on 2008-06-13
> **icest0rm said:**
> yes, use latest bios, the issue has been fixed on it

I'm using F.25 on mine. Can you let me know which version exactly you've got?

---

### Post by icest0rm on 2008-06-13
> **jethai said:**
> I'm using F.25 on mine. Can you let me know which version exactly you've got?

F2A and F2B have fixed the problem,
btw I still have very high temps even if cpu scaling works now...
CPU throttles from 60°C to 85°C when installing packages etc.
Video Card throttles from 75°C to 85°C :-\

---

### Post by jethai on 2008-06-18
> **icest0rm said:**
> F2A and F2B have fixed the problem,
btw I still have very high temps even if cpu scaling works now...
CPU throttles from 60°C to 85°C when installing packages etc.
Video Card throttles from 75°C to 85°C :-\

You're right, the install of F.2B fixed that... Now the CPUs sit at 800 Mhz of the total 2.2 GHz and idle at 52 degrees. Nvidia GPU idles at 64 degrees.

It's been easier having Ubuntu while learning to set up some servers at slicehost, but the temps are ridiculous. I really can't keep it on my lap at all now. 

Are you going to stick with Hardy? I've read other people having no temperature problems with Feisty. Maybe I'll look into other distro's to see if they're friendly. I'm resisting going back to Vista...

---

### Post by icest0rm on 2008-06-19
> **jethai said:**
> 
Are you going to stick with Hardy? I've read other people having no temperature problems with Feisty. Maybe I'll look into other distro's to see if they're friendly. I'm resisting going back to Vista...

well I don't think it's an OS issue, since under vista I get those temps after 30min/1h of normal use:

[IMG]http://img81.imageshack.us/img81/4053/temphy9.jpg[/IMG]

---

### Post by jethai on 2008-06-19
I take it your fan is constantly running too?

---

### Post by icest0rm on 2008-06-19
yes, it starts spinning and then never stop!

---

