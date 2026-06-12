---
title: "Powercap (intel-rapl) - Changing long-term power limit"
date: 2020-09-04
forum: Hardware
---

### Post by ahaslam on 2020-09-04
Hi, I'm looking for some clarification on how to use either rapl-set or powercap-set to change the long term power limit on my Intel N4200 laptop running Ubuntu 20.04.

Firstly, I know that my bios allows modification of the long-term constraint (up to a preset max) as I've had good results with ThrottleStop on Windows.

My default constraints:

```
powercap-info -p intel-rapl         
Zone 0
  name: package-0
  enabled: 0
  max_energy_range_uj: 262143328850
  energy_uj: 1431662228
  Constraint 0
    name: long_term
    power_limit_uw: 3999744
    time_window_us: 27983872
    max_power_uw: 5999616
  Constraint 1
    name: short_term
    power_limit_uw: 5999616
    time_window_us: 976
    max_power_uw: 0
  Zone 0:0
    name: core
    enabled: 0
    max_energy_range_uj: 262143328850
    energy_uj: 975192877
  Zone 0:1
    name: uncore
    enabled: 0
    max_energy_range_uj: 262143328850
    energy_uj: 308897463
  Zone 0:2
    name: dram
    enabled: 0
    max_energy_range_uj: 262143328850
    energy_uj: 410797898
    Constraint 0
      name: long_term
      power_limit_uw: 0
      time_window_us: 976
```

So I'm looking at Zone 0, Constraint 0. You can see that it's set to 4w long-term with a short-term limit of 6w. What I would like to achieve is to make the long-term constraint equal to the short term constraint, which would replicate what Ive achieved with ThrottleStop on Windows.

To that end, I have tried the following, which all seem to do the same thing:

```
cd /sys/class/powercap/intel-rapl/intel-rapl:0 && cat constraint_0_max_power_uw | tee constraint_0_power_limit_uw
rapl-set -p 0 -c 0 -l 5999616 -e 1
powercap-set -p intel-rapl -z 0 -c 0 -l 5999616 -e 1
```

Either one of these appear to set the constraint as required:

```
Zone 0
  name: package-0
  enabled: 1
  max_energy_range_uj: 262143328850
  energy_uj: 4600742311
  Constraint 0
    name: long_term
    power_limit_uw: 5999616
    time_window_us: 27983872
    max_power_uw: 5999616
```

With either method, there is no error and the relevant files are successfully updated. However, the new power limit is not adhered to. Please see the attached s-tui screenshot which illustrates the clocks & power limit dropping regardless of settings.

The CPU governor is set to 'performance' and disabled TLP is disabled.

Am I missing something here? I assume that the relevant driver is loaded due to the files being present and no errors are being produced, but it feels as tough I'm overlooking something of that nature.

Any help/suggestions would be greatly appreciated. **Has anyone even seen this work on Linux?**

---

### Post by Rocket2DMn on 2021-07-16
Author of the powercap-utils software here.  Since you never got any replies, I'll chime in now - better late than never? I actually ran across this while searching for something else.

First, it looks like you're using the powercap tools correctly and they are working as designed.  In the future, I recommend sticking to the powercap-{info,set} tools as the RAPL-specific rapl-{info,set} tools are deprecated and may eventually be removed.

The long term power constraint is typically set to be around the processor's thermal design power (TDP)  A higher short term power cap allows the CPU to use TurboBoost for short periods, which improves performance for bursty applications, but the higher frequencies that TurboBoost uses cannot be sustained because it generates too much heat in the processor.  I'd guess that other mechanisms (like thermal protections) in the system are kicking in to reduce the processor frequency, which in turn uses lower power (which settles around the TDP, as designed).

As an aside, in your attachment, you've highlighted the core domain in the s-tui output, which is actually "Zone 0:0" in the powercap-info output.  Since the core components use the majority of the power on your system, it looks similar to the entire package domain (to its left in the s-tui output).

In summary, I'd say everything appears to be working correctly, but your expectations about the system behavior are incorrect.

---

