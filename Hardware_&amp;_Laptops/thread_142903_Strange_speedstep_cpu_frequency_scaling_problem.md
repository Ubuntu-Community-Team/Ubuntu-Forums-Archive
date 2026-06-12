---
title: "Strange speedstep cpu frequency scaling problem"
date: 2006-03-11
forum: Hardware &amp; Laptops
---

### Post by Pausanias on 2006-03-11
Hi

I am experiencing some strange behavior with the cpu frequency handling. Normally, everything is fine---the chip steps up and down perfectly well using the default Ubuntu breezy setup. The minimum speed is 800MHz and the maximum speed is 2GHz

**However**, when I run a cpu-intensive task for a long time, something very strange happens. At the beginning of the run all is well---my laptop runs at its maximum 2GHz frequency. However, after about an hour or so, it scales itself down to 1.6GHz and stays there. Nothing I seem to do fixes it aside from rebooting:

[list]
[*] Killing powernowd and selecting the performance governor does nothing.
[*] When I do cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq, it says 1600000
[*] Killing powernowd and doing a sudo tcsh -c "echo -n 2000000 > /sys/device/system/cpu/cpu0/cpufreq/scaling_max_freq" does nothing---the maximum frequency stays at 1600000.
[*] scaling_available_frequencies still says 2000000 is an available option.
[/list]

This is what /proc/cpuinfo state says during the affected state
> 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 2.00GHz
stepping        : 8
cpu MHz         : 1596.668
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx est tm2
bogomips        : 3152.28


---

### Post by Pausanias on 2006-03-11
I have some updated information. Basically, the governor is userspace, and I've killed powernowd, but something periodically keeps setting the frequency down from 2GHz to 1.6 GHz. Echoing 2000000 to scaling_setspeed sets it back to 2 GHz, but only for a few minutes. After that, the scaling goes back to 1.6 GHz.

By the way, I am using the speedstep_centrino module.

My question is, what is setting the cpu speed if the governor is userspace and powernowd is killed?

---

### Post by WildTangent on 2006-03-12
Does your CPU start throttling if it gets too hot?

-Wild

---

### Post by Pausanias on 2006-03-12
Can't be that. The Maximum Pentium M temperature is [100C acoording to intel]("http://www.intel.com/support/processors/mobile/pm/sb/CS-007971.htm"), but I've never run hotter than 70., even with my workaround which is the following tcsh shell script:

```

#!/bin/tcsh

while (1 == 1)
  echo 2000000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_setspeed
  sleep 30
end

```

This keeps the CPU at 2GHz when I need it, but it's an awful kludge. Is there a better place to ask this question?

---

