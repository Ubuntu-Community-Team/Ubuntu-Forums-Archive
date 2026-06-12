---
title: "CPU Throttling to avoid high temperatures"
date: 2021-06-03
forum: Hardware
---

### Post by sebastian23 on 2021-06-03
I would like to know how to minimize power consumption of my Laptop with i7-9750 CPU and GeForce RTX 2060 Mobile. I already switched off the GeForce and only use the internal CPU graphics, but power consumption still seems very high as the fan never switch off and always spin with a high speed. The area of the case next to touchpad also gets hot alll the time. I use this Laptop just for Office and Youtube most of the time, so I really don't need all of it's high end features. Is it possible to throttle down the CPU and would that makes any sense? I use Ubuntu 20.04.2 LTS.

---

### Post by TheFu on 2021-06-03
Intel CPUs have automatically throttled due to thermal limits for a very long time.  

Had a Core i7 from 2009 that did. It would show up in the logs as one or more CPUs was throttled.  Just needed to have fresh thermal grease applied and some dust removed from the case, fans, etc.  It didn't throttle at all when I first inherited the system.  None of my other systems, some older, had dust issues. It was just that one case.

---

### Post by mewingatthemoon on 2021-06-04
So first off, different tack: when was the last time you dusted out your laptop? It doesn't take much dust to cause overheating and loss of performance. Even dust stuck in the keyboard can contribute - laptop thermal dissipation isn't great to start with.

Failing that - install htop and powertop, and see what's causing the increased load. powertop in particular is very useful for this, as it shows what's actually consuming the most wattage and waking the machine's CPU the most.

You could also install cpufrequtils for further configuration of throttling (you'll have to copy /usr/share/doc/cpufrequtils/examples/cpufrequtils.sample to /etc/default/cpufrequtils). However, I'd strongly recommend diagnosing the problem first. Modern x86-64 processors tend to have their own pretty effective frequency scaling in addition to whatever the OS imposes. (e.g. if I run cpufreq-info on my i5-4300U tablet, it will show the frequency often falling well below the max of 2.9 GHz even when the scaling governor is set to "performance".) Some Intel CPUs, like the ca. 2012 i7 on my old laptop, will even completely ignore the OS on frequency scaling.

---

### Post by Doug S on 2021-06-04
Processors performance verses energy use verses CPU frequency is highly non linear in the upper range. It can take lot more energy for that last tiny bit of performance. By far, the easiest thing for you to do would be to disable turbo frequencies in the BIOS. However, if you want more control over it, you could manage the maximum CPU frequency yourself. A previous response mentioned cpufrequtils, but I only ever use primitive commands directly. You should be using the intel_pstate CPU frequency driver by default. Then if you wanted to limit the maximum CPU frequency to say, 85%, do:

```
echo 85 | sudo tee /sys/devices/system/cpu/intel_pstate/max_perf_pct
```

I pretty much always have turbostat running in a terminal window to monitor power and temperature and a couple of other things:

```
doug@s19:~$ sudo turbostat --Summary --quiet --show Busy%,Bzy_MHz,IRQ,PkgWatt,PkgTmp,RAMWatt,GFXWatt --interval 15
Busy%   Bzy_MHz IRQ     PkgTmp  PkgWatt GFXWatt RAMWatt
39.48   2520    3323748 40      11.35   0.00    0.89
39.45   2524    3324142 39      11.37   0.00    0.89
38.82   2508    3299833 39      11.11   0.00    0.89
```

You could also setup thermald to impose an upper temperature limit.
There is a new feature coming where the TCC offset can be used to limit the upper processor package temperature. I like it very much, but it is only implemented for a few intel processors so far, and only as of the most recent mainline kernels.

@mewingatthemoon : your old 2012 i7 will only ignore the OS if that was somehow set in your BIOS or forced by the manufacturer. It is not typical.

---

### Post by sebastian23 on 2021-06-09
> **mewingatthemoon said:**
> Failing that - install htop and powertop, and see what's causing the increased load. powertop in particular is very useful for this, as it shows what's actually consuming the most wattage and waking the machine's CPU the most.

Firefox always use most of my CPU. Something between 10% for browsing and up to 80% for streaming.

> **Doug S said:**
> Processors performance verses energy use verses CPU frequency is highly non linear in the upper range. It can take lot more energy for that last tiny bit of performance. By far, the easiest thing for you to do would be to disable turbo frequencies in the BIOS. However, if you want more control over it, you could manage the maximum CPU frequency yourself. A previous response mentioned cpufrequtils, but I only ever use primitive commands directly. You should be using the intel_pstate CPU frequency driver by default. Then if you wanted to limit the maximum CPU frequency to say, 85%, do:

```
echo 85 | sudo tee /sys/devices/system/cpu/intel_pstate/max_perf_pct
```

I can't see any change in temperature if I limit my CPU to 70% or even lower.

[QUOTE=Doug S;14041838]I pretty much always have turbostat running in a terminal window to monitor power and temperature and a couple of other things:

```
doug@s19:~$ sudo turbostat --Summary --quiet --show Busy%,Bzy_MHz,IRQ,PkgWatt,PkgTmp,RAMWatt,GFXWatt --interval 15
Busy%   Bzy_MHz IRQ     PkgTmp  PkgWatt GFXWatt RAMWatt
39.48   2520    3323748 40      11.35   0.00    0.89
39.45   2524    3324142 39      11.37   0.00    0.89
38.82   2508    3299833 39      11.11   0.00    0.89
```

My PkgTmp is around 55 degress most of the time, sometimes it goes up to 80 and 90 degress, but that only for a few seconds, then immediately came back to below 60.

I guess it's a hardware problem, as the fan even spin loud if I use Windows. I haven't dust out the case, but I can't see any dust from outside. Maybe there really is to less thermal geese between Fan and CPU, but device is still within warranty so I don't want to open if by myself.
In the last days wifi interrupt couple of times and I wasn't able to reconnect as no wifi networks was available. After rebooting my laptop wifi works fine for many hours again.

---

### Post by TheFu on 2021-06-09
wifi is a different issue and needs people with different skills to help. Open a different thread in the "Networking" sub-forum here. Be certain to read the "Sticky" posts and run the wifi-info script before posting to get the quickest help.

---

### Post by Doug S on 2021-06-09
> **sebastian23 said:**
> I can't see any change in temperature if I limit my CPU to 70% or even lower.

My PkgTmp is around 55 degress most of the time, sometimes it goes up to 80 and 90 degress, but that only for a few seconds, then immediately came back to below 60.

Seems odd. I wonder if something else is overwriting your setting. You might need to do a test with CPU loaded to see cause and effect, example below. 90 degrees then coming down might be thermal throttling.

```
doug@s19:~$ sudo turbostat --Summary --quiet --show Busy%,Bzy_MHz,IRQ,PkgWatt,PkgTmp,RAMWatt,GFXWatt --interval 6
Busy%   Bzy_MHz IRQ     PkgTmp  PkgWatt GFXWatt RAMWatt
0.02    800     326     33      1.33    0.00    0.89   <<< system idle
0.01    800     131     33      1.33    0.00    0.89
0.01    800     133     32      1.40    0.00    0.89
82.68   800     60174   33      6.59    0.00    0.89  <<< prime 95 torture test load applied
99.76   800     72213   33      7.67    0.00    0.89  <<< CPU max freq limited to minimum
99.76   800     72160   33      7.69    0.00    0.89
99.76   853     72391   34      8.11    0.00    0.89  <<< Start increasing max CPU frequency
99.76   1200    72165   34      11.01   0.00    0.89
99.76   1200    72167   34      10.91   0.00    0.89
99.76   1200    72357   34      10.80   0.00    0.89
99.76   1200    72163   34      10.89   0.00    0.89
99.76   1651    72222   36      16.50   0.00    0.89
99.76   1700    72195   36      17.17   0.00    0.89
99.76   1700    72324   36      17.24   0.00    0.89
99.76   2031    72165   37      22.33   0.00    0.89
99.76   2200    72383   37      25.01   0.00    0.89
99.76   2200    72130   38      24.83   0.00    0.89
99.76   2643    72362   41      33.35   0.00    0.89
99.76   2700    72153   40      34.22   0.00    0.89
99.76   2700    72137   41      34.11   0.00    0.89
99.76   3124    72368   45      45.99   0.00    0.89
99.76   3200    72152   46      48.13   0.00    0.89
99.76   3200    72184   45      48.17   0.00    0.89
99.76   3200    72143   45      48.41   0.00    0.89
99.76   3535    72369   49      60.88   0.00    0.89
99.76   3600    72161   50      63.08   0.00    0.89
99.76   3600    72144   50      62.78   0.00    0.89
99.76   3902    72379   58      80.70   0.00    0.89
99.76   4100    72149   58      91.77   0.00    0.89
99.76   4100    72188   58      91.72   0.00    0.89
99.76   4100    72140   59      92.01   0.00    0.89
99.67   4487    72681   69      125.63  0.00    0.89
99.65   4596    72227   71      [COLOR="#FF0000"]135.16[/COLOR]  0.00    0.89
99.74   4520    72166   69      126.92  0.00    0.89  <<< Power limit throttling engages
99.74   4500    72136   69      124.90  0.00    0.89
99.72   4495    72170   70      124.91  0.00    0.89
99.73   4497    72192   71      124.91  0.00    0.89
99.72   4495    72140   72      124.91  0.00    0.89
99.72   4496    72192   72      124.91  0.00    0.89
99.73   2684    72161   44      67.60   0.00    0.89  <<< Drop max CPU frequency again
99.76   800     72154   43      7.74    0.00    0.89
99.76   800     72160   43      7.81    0.00    0.89  <<< Residual temperature, as coolant has warmed up.
99.76   800     72153   43      7.89    0.00    0.89
99.76   800     72156   43      7.95    0.00    0.89
99.76   800     72149   43      7.99    0.00    0.89
99.76   800     72149   43      7.98    0.00    0.89
26.11   800     19340   42      3.53    0.00    0.89
0.01    800     150     42      1.84    0.00    0.89  <<< Load removed
0.02    800     167     41      1.71    0.00    0.89
0.02    800     198     41      1.76    0.00    0.89
0.01    800     129     41      1.52    0.00    0.89
```

---

### Post by sebastian23 on 2021-06-10
Months ago I deactivated my Geforce and force Ubuntu to just use internal graphic card as battery drain to fast while using the Geforce. I activated the Geforce again and temperature of my CPU goes down to around 40 degrees. My Laptop use more energy now, but Fan isn't louder.

---

### Post by him610 on 2021-06-10
> activated the Geforce again and temperature of my CPU goes down to around 40 degrees. My Laptop use more energy now, but Fan isn't louder.
One possible explanation - the integrated GFX is part of the cpu package which results in a need for higher heat transfer because more electrons moving around in cpu package calling for more fan speed. When you set back to the external Geforce GFX. it reduced the heat generated in the cpu package.

---

