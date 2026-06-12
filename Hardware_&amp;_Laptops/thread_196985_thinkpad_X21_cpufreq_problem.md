---
title: "thinkpad X21 cpufreq problem"
date: 2006-06-15
forum: Hardware &amp; Laptops
---

### Post by MrIch on 2006-06-15
Hello,
I have just installed xubuntu 6.06 on my laptop. Then I tried to activate cpufreq, I have used this howto:
[http://www.thinkwiki.org/wiki/How_to_get_SpeedStep_working_on_Coppermine-piix4-smi_based_ThinkPads](http://www.thinkwiki.org/wiki/How_to_get_SpeedStep_working_on_Coppermine-piix4-smi_based_ThinkPads)

But I get this error:
```

root@notebook:/boot# modprobe speedstep-smi
FATAL: Error inserting speedstep_smi (/lib/modules/2.6.15-23-386/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-smi.ko): No such device

root@notebook:/boot# cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 8
model name      : Pentium III (Coppermine)
stepping        : 6
cpu MHz         : 196.599
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse
bogomips        : 796.26

```

The folder  /sys/devices/system/cpu is empty...

Debian 3.1 with works without those problems.

Any ideas?

---

