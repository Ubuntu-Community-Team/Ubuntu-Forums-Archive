---
title: "Problem using CPUFreq"
date: 2008-08-24
forum: Hardware
---

### Post by joho500 on 2008-08-24
Hi,

I want to set up CPUFreq to automatically lower the frequency of the CPU when it's on low use. But I get an error with cpufreq-info saying there's no driver active:

```
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU

```

The following modules are loaded:

```
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7104  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
```

And the folder /sys/devices/system/cpu/cpu0/cpufreq doesn't exist so it appears the drivers aren't on my system.

I can't find any solution on the net. Does anyone have a solution for this annoying problem? :confused:

Thanks.

Joost

---

### Post by Sam Lars on 2008-08-24
It sounds like your CPU doesn't support throttling, could you post the output of
```
cat /proc/cpuinfo
```

---

### Post by joho500 on 2008-08-25
Hi Sam,

Output of cat /proc/cpuinfo :

```
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 6
model		: 8
model name	: AMD Athlon(TM) XP 2200+
stepping	: 1
cpu MHz		: 1800.114
cache size	: 256 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep
mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up ts
bogomips	: 3603.69
clflush size	: 32
```

---

### Post by Sam Lars on 2008-08-26
What do you get from
```
sudo /etc/init.d/cpufreqd restart
```
Also, have you tried reinstalling it?
```
sudo aptitude reinstall cpufreqd cpufrequtils
```

---

### Post by joho500 on 2008-08-28
Hi Sam,

First I want to thank you for your help.:-) 
The problem isn't solved yet. cpufreqd isn't installed. I'm running mythbuntu on this box. When I select cpufreqd in Synaptic I get a message that mythbuntu-desktop will be removed. Of course, that's not what I want. Is cpufreqd incompatible with mythbuntu?

Joost

---

### Post by Sam Lars on 2008-08-29
Hmm, according to this, it appears that AMD Athlon processors don't support scaling.
[http://ubuntuforums.org/showthread.php?t=856812&highlight=AMD+Athlon+XP+scaling](http://ubuntuforums.org/showthread.php?t=856812&highlight=AMD+Athlon+XP+scaling)
Or maybe some do?
Try
```
sudo modprobe powernow-k8
```
I guess you want to use powernowd instead of cpufreqd.
If that doesn't work, try powernow-k7 instead.
This from:
```
http://ubuntuforums.org/showthread.php?t=248867&highlight=AMD+Athlon+XP+scaling
```

---

### Post by nicedude on 2008-08-29
Frequency stepping is not supported by your proccesor but if this is a desktop PC this shouldn't matter as the speed steping is to save power more than anything and for a desktop it shouldn't matter at all. I will post the output for my AMD CPU which does support stepping so you can see the differences although I am not sure what all of them are, I see stepping in the output and don't in yours. Also I googled it and found others saying your family of CPU is not equipped to do it so I am 99% that this is right.

MY CPU INFO OUTPUT

nicedude@dellbox:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 104
model name    : AMD Turion(tm) 64 X2 Mobile Technology TL-58
stepping    : 1
cpu MHz        : 800.000
cache size    : 512 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch ts fid vid ttp tm stc 100mhzsteps
bogomips    : 1601.85
clflush size    : 64

processor    : 1
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 104
model name    : AMD Turion(tm) 64 X2 Mobile Technology TL-58
stepping    : 1
cpu MHz        : 800.000
cache size    : 512 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch ts fid vid ttp tm stc 100mhzsteps
bogomips    : 1601.85
clflush size    : 64


Hope that helps clear it up for you and if you have a desktop PC then I would just forget about this as it is not needed anyway.

nicedude

---

### Post by joho500 on 2008-08-30
Thanks nicedude and Sam. I've been looking on Tom's Hardware (the link Sam provided) and came to the same conclusion: socket A Athlons don't support Cool 'n' Quiet and no stepping.

Thanks again.

Joost

---

