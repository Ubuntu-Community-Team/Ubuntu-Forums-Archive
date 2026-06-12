---
title: "ACPI temperature too high"
date: 2008-07-26
forum: Hardware
---

### Post by uraldinho on 2008-07-26
Hi, 

when on batteries my laptop CPU throttles and becomes unusable. I've been searching the forums and found the cause of the problem, but I need your help to solve it. 

The problems is, independent of what CPU frequency mode I am on, at one point ACPI reaches the trip points and the CPU throttles. The problem is that sensors gives me a temperature less than 50C but the ACPI reads more than 90C. 

Here is my data: 
CPU: AMD Turion 

output of "cat /proc/acpi/thermal_zone/THRM/trip_points"
```

critical (S5):           94 C
passive:                 90 C: tc1=2 tc2=5 tsp=50 devices=CPU0

```

Output of "sensors"
```

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +50.0°C

```

Output of cpufreq-info 
```

  driver: powernow-k8
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 800 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 1.80 GHz, 1.60 GHz, 800 MHz
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: frequency should be within 800 MHz and 2.00 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.

```

output of "cat /proc/acpi/processor/CPU0/throttling"
```

state count:             8
active state:            T0
state available: T0 to T7
states:
   *T0:                  100%
    T1:                  87%
    T2:                  75%
    T3:                  62%
    T4:                  50%
    T5:                  37%
    T6:                  25%
    T7:                  12%

```

"cat /proc/acpi/thermal_zone/THRM/temperature" always gives me 0, the only time I can get a reading is when the laptop is in battery mode and the ACPI temperature is higher than 90C. When the 90C point is reached the throttling starts from T0 and goes all the way down to T7 very quickly. 

I'm not sure what else I should include in this post. 

Any help with the problem would be appreciated, as I can't use my laptop in battery mode. 

Regards.

---

