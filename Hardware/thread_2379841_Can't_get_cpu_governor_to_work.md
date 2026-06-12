---
title: "Can't get cpu governor to work"
date: 2017-12-10
forum: Hardware
---

### Post by Peter_Brandon on 2017-12-10
I have a desktop w/ an i7 processor.  I noticed that the cpu frequency on all cpus is always set at the maximum possible value or maybe a tiny bit below that value.  I hate wasting power, so thought I'd turn on powersave or ondemand.  

sudo cpufreq-info tells me that I only have the performance or powersave options available on my system. 
It also says my driver is intel-pstate. 

So I tried cpufreqd, altered the config file to use powersave, activated p-state regulation, restarted cpufreqd, and saw exactly no effect on my cpu frequency.  My system is at least 93% idle according to top, so you'd think that cpu frequencies could be scaled back. So, I uninstalled cpufreqd, installed tlp, and got exactly the same result.

When I looked up specifications for my chip, all I see is that power is regulated through c-state--there's no mention of p-state.  My kernel modules include a module called intel_cstate (I see no module that mentions pstate, though cpufreq-info says that's my driver).

I can force my cpu frequency to go lower using:

for ((i=0;i<$(nproc);i++)); do sudo sh -c "echo 1000000 > /sys/devices/system/cpu/cpu$i/cpufreq/scaling_max_freq"; done

However, all my CPUs get stuck at whatever the highest level is I gave in the above command, there's no scaling.

I did a little digging on c-states and apparently they are states in which parts of the processor are powered down.  According to powertop, my CPU's are at C0 (fully active) about 5% of the time and at C7 (very inactive) about 80% of the time.

So, maybe I'm thinking about this wrong. Is it that the system automatically powers down using C states, which don't show up in cpu frequency?  Maybe because the power management is C states, the processors are always put in maximum frequency when they are needed?

I wonder, then, whether I'm actually saving power by forcing the maximum cpu frequency down using scaling_max_freq?  I don't notice much if any lag with the cpu frequency forced down to 1GHz (even, say, with video running), but this may just be because more CPUs are active and are in C0 for longer.

Anyone have any enlightenment to share?

---

### Post by Doug S on 2017-12-11
> **Peter_Brandon said:**
> I have a desktop w/ an i7 processor.What generation of i7? It is relevant, because we want to know if you have HWP (HardWare Pstate control or not).
> **Peter_Brandon said:**
> sudo cpufreq-info tells me that I only have the performance or powersave options available on my system. 
It also says my driver is intel-pstate. Yes, the intel_pstate CPU frequency scaling driver only has "performance" and "powersave" frequency scaling governors. Think of intel_pstate powersave as roughly equivalent to acpi-cpufreq ondemand.

> **Peter_Brandon said:**
> So, maybe I'm thinking about this wrong. Is it that the system automatically powers down using C states, which don't show up in cpu frequency? That is correct.
> **Peter_Brandon said:**
> Maybe because the power management is C states, the processors are always put in maximum frequency when they are needed?That is incorrect. The active CPU frequency should scale, but it depends on load and potential IO boost and such. A trace would be required to know for sure.

> **Peter_Brandon said:**
> I wonder, then, whether I'm actually saving power by forcing the maximum cpu frequency down using scaling_max_freq?It depends on many factors, including generation of i7, workflow, how deep your max C state is... There are situations where lower CPU frequency and longer execution time saves energy. There are also situations where higher CPU frequencies and getting the job done faster, and spending more time in deep sleep states saves energy (called race to idle).

> **Peter_Brandon said:**
> Anyone have any enlightenment to share?A good tool to use is "turbostat" (I can never remember which package it is included in, because I build it from source).

EDIT: turbostat is in the "linux-tools-common" package. It also matters which kernel you are using, because there have been recent changes to the control algorithm.

---

### Post by Peter_Brandon on 2017-12-12
Thanks Doug for a very lucid explanation.

I tried turbostat, and the results are interesting.

When I set the maximum cpu frequency to 3.5 GHz by setting [COLOR=#000000] /sys/devices/system/cpu/cpu$i/cpufreq/scaling_max_freq, then turbostat over 2 minutes gives this:

[/COLOR][FONT=monospace][COLOR=#000000]root:/home# turbostat --interval 120[/COLOR]
        CPU     Avg_MHz Busy%   Bzy_MHz TSC_MHz
        -       150     4.32    3488    3492
        0       168     4.85    3480    3492
        4       145     4.17    3490    3492
        1       147     4.23    3490    3492
        5       148     4.24    3489    3492
        2       149     4.28    3490    3492
        6       143     4.12    3490    3492
        3       143     4.12    3489    3492
        7       159     4.56    3490    3492
[/FONT]
When I reset the maximum cpu freq to 1 GHz, I get this:

[FONT=monospace][COLOR=#000000]root:/home# turbostat --interval 120[/COLOR]
        CPU     Avg_MHz Busy%   Bzy_MHz TSC_MHz
        -       128     12.85   1000    3492
        0       133     13.37   1000    3492
        4       127     12.71   1000    3492
        1       129     12.94   1000    3492
        5       127     12.74   1000    3492
        2       136     13.66   1000    3492
        6       116     11.60   1000    3492
        3       132     13.20   1000    3492
        7       126     12.61   1000    3492

If I shorten the polling interval for turbostat to 1 second, Bzy_MHz is always 1000 when the maximum is set to 1 GHz.  When the max is set to 3.5 GHz, it sometimes comes in a bit slower than the apparent maximum of 3492, but lowest I saw was 3462 on a system that top says is running at about 95% idle.  

Maybe I'm misinterpreting here, but it looks to me like there's no evidence of any cpu frequency scaling--all the scaling is being done with C states.  Wish I had a clue as to why the governor is not working (it's set to powersave according to cpufreq-info).  I'm running a [/FONT]i7-4770K chip.  Powertop indicates my system spends most of its time in the C7 state.

[FONT=monospace]Perhaps the slightly lower avg_MHz rate when the system is set to 1 GHz as opposed to 3.5 GHz rate in the above printouts indicates that I'm using a bit less power--will examine wattage tomorrow.  I wonder if there's more wear and tear on the chips (if that's possible) if they are being used more of the time at a lower frequency....  Still, I think the watts used by the cpu even at 3.5 GHz is around 8 watts or so, so it probably doesn't make much difference in power consumption to have the lower frequency.

Thanks again.


[/FONT]

---

### Post by Doug S on 2017-12-14
> **Peter_Brandon said:**
> Maybe I'm misinterpreting here, but it looks to me like there's no evidence of any cpu frequency scaling--all the scaling is being done with C states.  Wish I had a clue as to why the governor is not working (it's set to powersave according to cpufreq-info).  I'm running a [/FONT]i7-4770K chip.  Powertop indicates my system spends most of its time in the C7 state.
Well, your CPU does seem rather busy, but also seems to ramp up to maximum clock frequency for relatively light load. You can use turobostat to monitor everything, including package power and various C state residency.

My main test computer is a server, so "idle" is way more "idle" than a desktop with a GUI. Here is an example from it (Note, my older i7-2600K does not have C7):

```
doug@s15:~/temp$ sudo turbostat --quiet --show CPU,Busy%,Bzy_MHz,IRQ,CPU%c1,CPU%c3,CPU%c6,PkgTmp,PkgWatt sleep 120
120.001481 sec
CPU     Busy%   Bzy_MHz IRQ     CPU%c1  CPU%c3  CPU%c6  PkgTmp  PkgWatt
-       0.22    1600    1686    0.24    0.00    99.54   26      3.86
0       0.01    1602    224     0.02    0.00    99.98   26      3.86
4       0.00    1600    68      0.02
1       0.00    1600    72      0.05    0.00    99.95
5       0.02    1600    556     0.03
2       0.01    1601    311     0.04    0.02    99.93
6       0.01    1600    243     0.04
3       0.00    1657    101     1.71    0.00    98.29
7       1.70    1600    111     0.01

```

And with a bit of load on CPU 7:
```
doug@s15:~/temp$ sudo turbostat --quiet --show CPU,Busy%,Bzy_MHz,IRQ,CPU%c1,CPU%c3,CPU%c6,PkgTmp,PkgWatt sleep 120
120.001588 sec
CPU     Busy%   Bzy_MHz IRQ     CPU%c1  CPU%c3  CPU%c6  PkgTmp  PkgWatt
-       6.17    1829    62177   6.65    0.00    87.18   33      6.52
0       2.08    1693    339     4.66    0.00    93.26   33      6.52
4       4.63    1753    106     2.11
1       0.00    1828    180     0.04    0.00    99.96
5       0.01    1696    581     0.03
2       1.83    1692    416     2.17    0.00    96.00
6       2.12    2742    378     1.88
3       0.00    1806    141     40.49   0.00    59.51
7       38.70   1802    60036   1.80

```

> **Peter_Brandon said:**
> I wonder if there's more wear and tear on the chips (if that's possible) if they are being used more of the time at a lower frequency....As long as all voltages are stable and in range, then the main chip stress would be as a function of temperature. Even then, I wouldn't worry unless you are getting towards critical temperatures.

EDIT: I should have mentioned my minimum pstate is 16 and my maximum, turbo, pstate is 38.

---

