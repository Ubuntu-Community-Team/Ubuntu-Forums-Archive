---
title: "Core 2 Duo won't slow down"
date: 2007-01-12
forum: Hardware &amp; Laptops
---

### Post by BHBrain on 2007-01-12
Hi,

I got an Asus notebook and my core 2 duo is always running at full speed. 
What do I have to install to get speedstep working? 

I am using kernel 2.6.17-10-generic

And this is what cpuinfo says:

```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
stepping        : 6
cpu MHz         : 1995.004
cache size      : 4096 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips        : 3995.77
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
stepping        : 6
cpu MHz         : 1995.004
cache size      : 4096 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips        : 3990.09
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

```

---

### Post by tweedledee on 2007-01-13
> **BHBrain said:**
> Hi,

I got an Asus notebook and my core 2 duo is always running at full speed. 
What do I have to install to get speedstep working? 


Try laptop-mode.  Set "laptop mode" to true in /etc/default/acpi-support, then you can edit /etc/laptop-mode/laptop-mode.conf (and possibly what you've already tried) to regulate the processors.

---

### Post by BHBrain on 2007-01-14
This did not change anything.

My Ubuntu is even missing "/sys/devices/system/cpu/cpu*/cpufreq/scaling_available_frequencies"

Does nobody use a laptop? Nobody got the same problem?

Please help me.

---

### Post by lutra on 2007-01-19
> **BHBrain said:**
> This did not change anything.

My Ubuntu is even missing "/sys/devices/system/cpu/cpu*/cpufreq/scaling_available_frequencies"

Does nobody use a laptop? Nobody got the same problem?

Please help me.


Use the "cpu frequency scaling monitor" but also do

```

sudo dpkg-reconfigure gnome-applets
```


Now you can use the monitor to change frequencies. 
Note that when you select the other core it only seems that is not selecting it, but in truth it works ok, just confirm by

```
cat /proc/cpuinfo
```

---

