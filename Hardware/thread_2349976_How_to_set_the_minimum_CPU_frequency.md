---
title: "How to set the minimum CPU frequency"
date: 2017-01-20
forum: Hardware
---

### Post by phulshof2 on 2017-01-20
I've  been *blessed* with the power of speed step, which allows my Intel CPU  to switch from 800 MHz (idle) to 2.6 GHz (turbo). My problem is that one  of my applications requires so little CPU power that it switches to 800  MHz, causing issues with the video decoding. I've been trying to  convince my CPU to stay at at least 1.6 GHz, but no luck so far.

I've  tried disabling steed-step and CPU C states in the BIOS, but that had  no influence. In addition, I've set the processor.max_cstate=1 and  intel_idle.max_cstate=0 kernel parameters. I then proceeded to set the  scaling_governor to performance, and the scaling_min_frequency to  2000000, but when I run Pacman in MAME I get the following cpufreq-info:
-----
```
cpufrequtils 008: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to [EMAIL="cpufreq@vger.kernel.org"]cpufreq@vger.kernel.org[/EMAIL], please.
analyzing CPU 0:
  driver: intel_pstate
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 0.97 ms.
  hardware limits: 800 MHz - 2.60 GHz
  available cpufreq governors: performance, powersave
  current policy: frequency should be within 2.00 GHz and 2.60 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz (asserted by call to hardware).
analyzing CPU 1:
  driver: intel_pstate
  CPUs which run at the same hardware frequency: 1
  CPUs which need to have their frequency coordinated by software: 1
  maximum transition latency: 0.97 ms.
  hardware limits: 800 MHz - 2.60 GHz
  available cpufreq governors: performance, powersave
  current policy: frequency should be within 2.00 GHz and 2.60 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz (asserted by call to hardware).
analyzing CPU 2:
  driver: intel_pstate
  CPUs which run at the same hardware frequency: 2
  CPUs which need to have their frequency coordinated by software: 2
  maximum transition latency: 0.97 ms.
  hardware limits: 800 MHz - 2.60 GHz
  available cpufreq governors: performance, powersave
  current policy: frequency should be within 2.00 GHz and 2.60 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz (asserted by call to hardware).
analyzing CPU 3:
  driver: intel_pstate
  CPUs which run at the same hardware frequency: 3
  CPUs which need to have their frequency coordinated by software: 3
  maximum transition latency: 0.97 ms.
  hardware limits: 800 MHz - 2.60 GHz
  available cpufreq governors: performance, powersave
  current policy: frequency should be within 2.00 GHz and 2.60 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz (asserted by call to hardware).
-----
```

As  you can see, the frequency should be within 2-2.6 GHz, yet it runs at  800 MHz. If I run a more demanding game like Radiant Silvergun, the CPU  will be around 2400 MHz, so it's not like lack of power or heating is  causing an issue here. It may be related to the CPU waiting for the GPU  (I'm using internal graphics), since it only happens when I try to run  Pacman at the highest possible speed, which should be more demanding on  the CPU than running it at normal speed.

I'm running out of ideas on how to solve this. Any thoughts?

---

### Post by phulshof2 on 2017-01-21
I did a few more tests. If I reduce the FPS by adding sleep commands, the CPU frequency increases, and stays away from the 800 MHz. The results so far:
Operating System: CPU acts normal (around 1600-1800 MHz)
MAME at 100%: CPU acts normal (around 1200-1800 MHz)
MAME at maximum speed with complex game: CPU acts normal (around 2400-2500 MHz)
MAME at maximum speed with simple game: CPU goes down to 800 MHz
RetroFE at 60 FPS: CPU goes down to 800 MHz
RetroFE at 30 FPS: CPU acts normal (around 1400-1800 MHz)
Both programs are SDL programs, but whether that has any impact I don't know. Any thoughts?

---

