---
title: "Scaling CPU unsupported"
date: 2010-07-15
forum: Hardware
---

### Post by MartinoM on 2010-07-15
Hi! I have a lot of problems with my CPU (Intel core 2 Duo T8100): i can't scaling the frequency. I just try some ways (update BIOS, [http://ubuntuforums.org/showthread.php?t=248867]("http://ubuntuforums.org/showthread.php?t=248867") , ecc...) to fix the problem, but nothing result.

If i try to use the applet on Ubuntu, appear this message: "CPU Scaling unsupported".


```

martino@martino-laptop:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     T8100  @ 2.10GHz
stepping	: 6
cpu MHz		: 2094.900
cache size	: 3072 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm ida tpr_shadow vnmi flexpriority
bogomips	: 4189.80
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     T8100  @ 2.10GHz
stepping	: 6
cpu MHz		: 2094.900
cache size	: 3072 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm ida tpr_shadow vnmi flexpriority
bogomips	: 4189.48
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:



```

---

### Post by MartinoM on 2010-07-20
Bump!

---

### Post by MartinoM on 2010-07-24
bump

---

### Post by PresenceofMind on 2010-07-25
Hello,

Try these threads:

[http://ubuntuforums.org/showthread.php?t=1477743](http://ubuntuforums.org/showthread.php?t=1477743)

[http://ubuntuforums.org/showthread.php?t=1468833](http://ubuntuforums.org/showthread.php?t=1468833)

---

### Post by MartinoM on 2010-07-27
Noothing. I follow this HOWTO: [http://ubuntuforums.org/showthread.php?t=248867]("http://ubuntuforums.org/showthread.php?t=248867")
but i have no results whit this command:
```
martino@martino-laptop:~$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
cat: /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors: Nessun file o directory

```

---

