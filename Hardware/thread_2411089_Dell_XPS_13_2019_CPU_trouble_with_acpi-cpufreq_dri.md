---
title: "Dell XPS 13 2019 CPU trouble with acpi-cpufreq driver"
date: 2019-01-24
forum: Hardware
---

### Post by dabsig on 2019-01-24
Hey guys,
so I got myself a Dell XPS 13 preloaded with Ubuntu 18.04. Dist-Upgraded it to 18.10 but the system didn't feel as fast as you would expect it from a Intel® Core™ i7-8565U CPU @ 1.80GHz × 8, Turboboost up to 4,6GHz.


Output of "cpufreq-info" same for all 8 cores:
  ```
driver: intel_pstate
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 4294.55 ms.
  hardware limits: 400 MHz - 4.60 GHz
  available cpufreq governors: performance, powersave
  current policy: frequency should be within 400 MHz and 4.60 GHz.
                  The governor "powersave" may decide which speed to use
                  within this range.
  current CPU frequency is 2.29 GHz.
```


I tried the performance governor, but it feels like its still scaling down when not needed even with the performance mode to save energy or smth.


I found the cpufrq GNOEM extension online and wanted to go for mixed mode
[http://konkor.github.io/cpufreq/faq/](http://konkor.github.io/cpufreq/faq/)
So I'd have a core on high alert and GHz all the time and starting up applications goes quickly, while the other cores can adjust their GHz according to the needs I got at a certain point.
To do so I found out I have to turn off intel_pstate.


So I edited /etc/default/grub and disabled intel_pstate and rebooted.


Afterwards output of "cpufreq-info" same for all 8 cores:

```

  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 400 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 2.00 GHz, 1.90 GHz, 1.80 GHz, 1.70 GHz, 1.50 GHz, 1.40 GHz, 1.30 GHz, 1.20 GHz, 1.10 GHz, 1000 MHz, 800 MHz, 700 MHz, 600 MHz, 500 MHz, 400 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance, schedutil
  current policy: frequency should be within 400 MHz and 2.00 GHz.
                  The governor "powersave" may decide which speed to use
                  within this range.
  current CPU frequency is 900 MHz.
```


So now for some reason hardware limits dropped to 400 MHz - 2.00 GHz.
So I started searching the net again, and found out bios_limit is screwing me, with it's 
```
cat /sys/devices/system/cpu/cpu*/cpufreq/bios_limit = 2001000
```
set /sys/module/processor/parameters/ignore_ppc from 0 to 1 to ignore the BIOS, I did so in the GRUB config and updated grub and rebooted.


Result: cat /sys/devices/system/cpu/cpu*/cpufreq/bios_limit still is 2001000


For my understanding I can not edit /sys/devices/system/cpu/cpu*/cpufreq/bios_limit
but with /sys/module/processor/parameters/ignore_ppc = 1 it should be ignored.


Still I can not set userspace governor above 2.001 GHz.

I was thinking about turning off intel speed step but that would mean that ubuntu doesnt have an influence on cpu Ghz at all, right?

Any ideas how I can get my system to run with the acpi-cpufreq so I can go for mixed mode but still get the 4,6GHz ?

Feel free to ask if anything is still unclear, english isnt my native language and I may not have expressed myself in an well understandable way.

Thanks for your advice in advance.

---

### Post by CatKiller on 2019-01-24
acpi-cpufreq is pretty bad for anything remotely modern from Intel. pstate is the one that you want to be using. It will react the quickest and give you the best performance.

Edit to add: It would have been better to have stayed on 18.04, since that is a Long Term Support release - supported until 2023. Support for 18.10 will end in July.

---

### Post by Doug S on 2019-01-25
> **dabsig said:**
> I tried the performance governor, but it feels like its still scaling down when not needed even with the performance mode to save energy or smth.That is true, the processor itself can decide to scale down the CPU clock frequency, if the load is extremely light, even in performance mode.

> **dabsig said:**
> I found the cpufrq GNOEM extension online and wanted to go for mixed mode
[http://konkor.github.io/cpufreq/faq/](http://konkor.github.io/cpufreq/faq/)
So I'd have a core on high alert and GHz all the time and starting up applications goes quickly, while the other cores can adjust their GHz according to the needs I got at a certain point.
To do so I found out I have to turn off intel_pstate.That is not a very good reference, and not really how things work with current Intel processors. There is only one PLL (Phase Locked Loop) and so all CPUs are always at the same clock frequency, as decided by each ones vote. Since one never really knows which CPU will be assigned to which task, to me mixed mode doesn't make any sense.


> **dabsig said:**
> So now for some reason hardware limits dropped to 400 MHz - 2.00 GHz.No, that is not what it means. Use a direct primitive command, instead if cpufreq-info, to know for sure (and because another digit is required, read further down):
```
doug@s15:~/temp$ cat /sys/devices/system/cpu/cpufreq/policy0/scaling_available_frequencies
[COLOR="#FF0000"]3401000[/COLOR] 3400000 3300000 3100000 3000000 2900000 2800000 2600000 2500000 2400000 2200000 2100000 2000000 1900000 1700000 1600000
```

> **dabsig said:**
> So I started searching the net again, and found out bios_limit is screwing me, with it's 
```
cat /sys/devices/system/cpu/cpu*/cpufreq/bios_limit = 2001000
```with the acpi-cpufreq CPU scaling driver, the "1" means that the CPU is allowed to go into the turbo range of frequencies. There is no limit being set via this.
 
> **dabsig said:**
> set /sys/module/processor/parameters/ignore_ppc from 0 to 1 to ignore the BIOS, I did so in the GRUB config and updated grub and rebooted.


Result: cat /sys/devices/system/cpu/cpu*/cpufreq/bios_limit still is 2001000


For my understanding I can not edit /sys/devices/system/cpu/cpu*/cpufreq/bios_limit
but with /sys/module/processor/parameters/ignore_ppc = 1 it should be ignored.No, that is not what that means. It means to disable the last line of thermal defense, something that you should not do.


> **dabsig said:**
> Still I can not set userspace governor above 2.001 GHz.That is correct. 200100 means that turbo is allowed, any turbo.


> **dabsig said:**
> I was thinking about turning off intel speed step but that would mean that ubuntu doesnt have an influence on cpu Ghz at all, right?Don't do that. It'll cost you wasted power for no benefit.

> **dabsig said:**
> Any ideas how I can get my system to run with the acpi-cpufreq so I can go for mixed mode but still get the 4,6GHz ?It already is working properly.

Example, using my older i7-2600K processor, 3.4 GHz base, and 3.8 GHz turbo (1.6GHz minimum). I'll load up one CPU at 100% after a bit:

```
doug@s15:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/bios_limit
3401000
3401000
3401000
3401000
3401000
3401000
3401000
3401000
doug@s15:~$ sudo turbostat --Summary --quiet --show Busy%,Bzy_MHz,PkgTmp,PkgWatt,IRQ --interval 15
Busy%   Bzy_MHz IRQ     PkgTmp  PkgWatt
0.02    1908    564     28      3.72
0.01    1600    393     27      3.71
0.01    1601    461     27      3.71
0.01    1600    427     28      3.71
4.85    3792    7305    40      11.08
12.52   [COLOR="#FF0000"]3800[/COLOR]    17749   42      23.00   <<<< Notice how it is at max turbo
12.52   [COLOR="#FF0000"]3800[/COLOR]    17751   44      23.13

```EDIT 1: I agree with catkiller, just use the intel_pstate CPU frequency scaling driver.
EDIT 2: With the Intel_pstate driver in passive mode (no HWP) the same governors are available as would be available via the acpi-cpufreq driver:
```
$ cat /sys/devices/system/cpu/cpufreq/policy0/scaling_available_governors
conservative ondemand userspace powersave performance schedutil
$ cat /sys/devices/system/cpu/cpufreq/policy0/scaling_driver
intel_cpufreq        [COLOR="#FF0000"]<<<< The intel_pstate driver in passive mode changes its name.[/COLOR]


``` So, your mixed mode stuff could be done there also.

---

### Post by dabsig on 2019-01-27
Thank you for your answers, I kinda thought ubunuforums.org would notify me via mail when I get a reply, but thats not the default, so my bad.... Sorry for the late response.

@CatKiller I favour new features over LTS so I will go for 19.04 and will have support again.

@Doug S Thanks for explaining in such detail, I switched everything back to how it was. The question I'm asking myself now is the following. 
How do I get rid of this:

> [COLOR=#000000]That is true, the processor itself can decide to scale down the CPU clock frequency, if the load is extremely light, even in performance mode.[/COLOR]

You said I can set the intel_pstate to passive mode, but you also said mixed mode isn't the way to go anymore, can I edit the govenor, so it's not going too slow? Especially after boot or reoping the lid, even using the terminal takes forever. It takes like 5-10 sec for the password prompt after I pressed enter for smth like "sudo apt update"

I feel like that shouldn't be the case with this kind of CPU and RAM...

If that is normal, it really is disappointing. :/

---

### Post by coffeecat on 2019-01-27
> **dabsig said:**
> Thank you for your answers, I kinda thought ubunuforums.org would notify me via mail when I get a reply, but thats not the default

Welcome to the forum. 

When you have 10 posts in support forums, you'll be able to access your profile settings and change your default thread subscription mode to one of four options, including three by email at different frequencies. Until then, if you want to subscribe to a thread - any thread, not just ones you started - click on Thread Tools at the top of the thread, and then "Subscribe to this thread".

---

### Post by dabsig on 2019-01-27
Thanks for the heads-up!
May I also ask who I quote someone in the way you did it? I only managed to use > this kind of quote.

---

### Post by coffeecat on 2019-01-27
> **dabsig said:**
> Thanks for the heads-up!
May I also ask who I quote someone in the way you did it? I only managed to use .

:wink:

If you look just under any post, you'll see a number of clickable icon/labels, namely: Edit Post, Quick Reply, Advanced Reply, Reply with Quote, and an icon without label that is for quoting multiple posts. Click on Reply with Quote and the forum software will do the necessary. You can then remove some of the quoted text, as I did, if you want to respond to just a single point.

So as not to drag your technical support thread even more off-topic, if you have any other questions about using the admittedly labyrinthine forum software, you are very welcome to ask in [Forum Feedback & Help](https://ubuntuforums.org/forumdisplay.php?f=48).

---

### Post by CatKiller on 2019-01-27
> **dabsig said:**
> You said I can set the intel_pstate to passive mode, but you also said mixed mode isn't the way to go anymore, can I edit the govenor, so it's not going too slow? Especially after boot or reoping the lid, even using the terminal takes forever. It takes like 5-10 sec for the password prompt after I pressed enter for smth like "sudo apt update"

I feel like that shouldn't be the case with this kind of CPU and RAM...

If that is normal, it really is disappointing. :/

*powersave* and *performance* are the governors available with the pstate driver. Each P-state has a frequency range to use. *powersave* chooses the lowest frequency and *performance* picks the highest frequency from those ranges. Real-world performance is similar for all the governors, though: every modern computer is doing absolutely nothing almost all of the time. I'd imagine there are specific benchmark results at Phoronix if you're interested in the details.

It sounds like you might have some kind of responsiveness issue, but the CPU frequency is unlikely to be the cause. Everything responds pretty much instantly on my Skylake XPS 13 using intel_pstate and the powersave governor, even straight after boot or resume.

---

### Post by Doug S on 2019-01-27
> **dabsig said:**
> How do I get rid of this: "That is true, the processor itself can decide to scale down the CPU clock frequency, if the load is extremely light, even in performance mode."

You said I can set the intel_pstate to passive mode, but you also said mixed mode isn't the way to go anymore, can I edit the govenor, so it's not going too slow?
The only way i know of to lock the CPU frequency at their highest is to disable all idle states deeper than 0 (which is full power POLL on modern Intel CPUs). It wouldn't gain you anything, but cost a lot of energy and heat. Example (for my older i7-2600K):
```
doug@s15:~$ sudo turbostat --quiet --Summary --hide Avg_MHz,SMI,GFXMHz,TSC_MHz,GFXWatt,CorWatt,CPU%c1,CPU%c3,CPU%c6,CPU%c7,CoreTmp,GFX%rc6,Pkg%pc2,Pkg%pc3,Pkg%pc6,POLL,C1,C1E,C3,C6,C1%,C1E%,C3%,C6% --interval 15
Busy%   Bzy_MHz IRQ     POLL%   PkgTmp  PkgWatt
0.01    1600    411     0.00    28      3.71
0.01    1600    347     0.00    27      3.71
77.92   3498    94028   76.68   49      38.85
100.00  3500    120227  98.45   53      49.50  <<< Ilde states deeper than 0, disabled.
100.00  3500    120233  98.45   57      50.08
100.00  3500    120438  98.47   59      50.54
100.00  3500    120233  98.45   62      50.95
100.00  3500    120220  98.46   64      51.67  <<< Turbostat considers "POLL" time as busy.
100.00  3500    120230  98.45   66      52.06
100.00  3500    120215  98.46   67      52.34
100.00  3500    120244  98.46   68      52.54   <<< Cost = 40 degrees and 49 watts.

```

> **dabsig said:**
> Especially after boot or reoping the lid, even using the terminal takes forever. It takes like 5-10 sec for the password prompt after I pressed enter for smth like "sudo apt update"

I feel like that shouldn't be the case with this kind of CPU and RAM...

If that is normal, it really is disappointing. :/I am a server person and don't know about LapTop response times. However, I do not think the cause of your issues is with the CPU frequency scaling driver. I do not know if thermal or power limit throttling is coming into play or not. Dell also does some throttling if it detects a non Dell AC adapter and some other scenarios (at least they used to).

---

### Post by dabsig on 2019-01-27
> **Doug S said:**
>  I do not know if thermal or power limit throttling is coming into play or not. Dell also does some throttling if it detects a non Dell AC adapter and some other scenarios (at least they used to).

I checked throtteling via the cpu-freq gui (I don't knot how relieable this is as a source) and it's throtteling a lot, at least it says in orange cpu throttle: 2 sometimes in red cpu throttle: 40 and almost every time I check the gui overview there is always something about throtteling as a warning shown.

How can I check for throttle problems in a more "professional" way? and how can I troubleshoot throtteling, for my understanding throtteling means the cpu slows down because of overheating, but the fans are not even starting to make sounds and they simly can't be "too" hot.

---

### Post by Doug S on 2019-01-28
Please post the output for ```
sudo turbostat --Summary --show Busy%,Bzy_MHz,PkgTmp,PkgWatt,IRQ
``` let it run for about 20 seconds. turbostat is included in the linux-tools-common package.
Please also post the output for ```
grep . /sys/devices/system/cpu/intel_pstate/*
``` during one these events.

EDIT: The i7-8565U has a low TDP (Thermal Design Power) of 15 watts. It seems likely that power throttling might need to be activated. The turbostat spew at startup should tell us.

---

### Post by dabsig on 2019-01-30
Sorry for the late answer, I didn't see there is a new page.... ](*,)

Here you go. This is on "normal" output. If you can not see anything suspicious here I would like to see if i can run the commands in a moment when the computer seems to have issues, and doesn't even responde with a immediate password prompt after a sudo command.

sudo turbostat --Summary --show Busy%,Bzy_MHz,PkgTmp,PkgWatt,IRQ

turbostat version 17.06.23 - Len Brown <lenb@kernel.org>
CPUID(0): GenuineIntel 22 CPUID levels; family:model:stepping 0x6:8e:b (6:142:11)
CPUID(1): SSE3 MONITOR - EIST TM2 TSC MSR ACPI-TM TM
CPUID(6): APERF, TURBO, DTS, PTM, HWP, HWPnotify, HWPwindow, HWPepp, No-HWPpkg, EPB
cpu6: MSR_IA32_MISC_ENABLE: 0x00850089 (TCC EIST No-MWAIT PREFETCH TURBO)
CPUID(7): SGX
cpu6: MSR_IA32_FEATURE_CONTROL: 0x00040005 (Locked SGX)
CPUID(0x15): eax_crystal: 2 ebx_tsc: 166 ecx_crystal_hz: 0
TSC: 1992 MHz (24000000 Hz * 166 / 2 / 1000000)
CPUID(0x16): base_mhz: 2000 max_mhz: 4600 bus_mhz: 100
cpu6: MSR_MISC_PWR_MGMT: 0x00401cc0 (ENable-EIST_Coordination DISable-EPB DISable-OOB)
RAPL: 17476 sec. Joule Counter Range, at 15 Watts
cpu6: MSR_PLATFORM_INFO: 0x4043df1011400
4 * 100.0 = 400.0 MHz max efficiency frequency
20 * 100.0 = 2000.0 MHz base frequency
cpu6: MSR_IA32_POWER_CTL: 0x0024005d (C1E auto-promotion: DISabled)
cpu6: MSR_TURBO_RATIO_LIMIT: 0x29292d2e
41 * 100.0 = 4100.0 MHz max turbo 4 active cores
41 * 100.0 = 4100.0 MHz max turbo 3 active cores
45 * 100.0 = 4500.0 MHz max turbo 2 active cores
46 * 100.0 = 4600.0 MHz max turbo 1 active cores
cpu6: MSR_CONFIG_TDP_NOMINAL: 0x00000012 (base_ratio=18)
cpu6: MSR_CONFIG_TDP_LEVEL_1: 0x00080050 (PKG_MIN_PWR_LVL1=0 PKG_MAX_PWR_LVL1=0 LVL1_RATIO=8 PKG_TDP_LVL1=80)
cpu6: MSR_CONFIG_TDP_LEVEL_2: 0x001400c8 (PKG_MIN_PWR_LVL2=0 PKG_MAX_PWR_LVL2=0 LVL2_RATIO=20 PKG_TDP_LVL2=200)
cpu6: MSR_CONFIG_TDP_CONTROL: 0x00000000 ( lock=0)
cpu6: MSR_TURBO_ACTIVATION_RATIO: 0x00000011 (MAX_NON_TURBO_RATIO=17 lock=0)
cpu6: MSR_PKG_CST_CONFIG_CONTROL: 0x1e008008 (UNdemote-C3, UNdemote-C1, demote-C3, demote-C1, locked: pkg-cstate-limit=8: unlimited)
cpu6: cpufreq driver: intel_pstate
cpu6: cpufreq governor: powersave
cpufreq intel_pstate no_turbo: 0
cpu6: MSR_MISC_FEATURE_CONTROL: 0x00000000 (L2-Prefetch L2-Prefetch-pair L1-Prefetch L1-IP-Prefetch)
cpu0: MSR_PM_ENABLE: 0x00000001 (HWP)
cpu0: MSR_HWP_CAPABILITIES: 0x0108122e (high 46 guar 18 eff 8 low 1)
cpu0: MSR_HWP_REQUEST: 0x80002e17 (min 23 max 46 des 0 epp 0x80 window 0x0 pkg 0x0)
cpu0: MSR_HWP_INTERRUPT: 0x00000000 (Dis_Guaranteed_Perf_Change, Dis_Excursion_Min)
cpu0: MSR_HWP_STATUS: 0x00000004 (No-Guaranteed_Perf_Change, No-Excursion_Min)
cpu0: MSR_IA32_ENERGY_PERF_BIAS: 0x00000006 (balanced)
cpu0: MSR_RAPL_POWER_UNIT: 0x000a0e03 (0.125000 Watts, 0.000061 Joules, 0.000977 sec.)
cpu0: MSR_PKG_POWER_INFO: 0x00000078 (15 W TDP, RAPL 0 - 0 W, 0.000000 sec.)
cpu0: MSR_PKG_POWER_LIMIT: 0x420198009c8198 (UNlocked)
cpu0: PKG Limit #1: ENabled (51.000000 Watts, 24.000000 sec, clamp DISabled)
cpu0: PKG Limit #2: DISabled (51.000000 Watts, 0.002441* sec, clamp DISabled)
cpu0: MSR_DRAM_POWER_LIMIT: 0x5400de00000000 (UNlocked)
cpu0: DRAM Limit: DISabled (0.000000 Watts, 0.000977 sec, clamp DISabled)
cpu0: MSR_PP0_POLICY: 0
cpu0: MSR_PP0_POWER_LIMIT: 0x00000000 (UNlocked)
cpu0: Cores Limit: DISabled (0.000000 Watts, 0.000977 sec, clamp DISabled)
cpu0: MSR_PP1_POLICY: 0
cpu0: MSR_PP1_POWER_LIMIT: 0x00000000 (UNlocked)
cpu0: GFX Limit: DISabled (0.000000 Watts, 0.000977 sec, clamp DISabled)
cpu0: MSR_IA32_TEMPERATURE_TARGET: 0x00640000 (100 C)
cpu0: MSR_IA32_PACKAGE_THERM_STATUS: 0x882f080a (53 C)
cpu0: MSR_IA32_PACKAGE_THERM_INTERRUPT: 0x00000003 (100 C, 100 C)
cpu6: MSR_PKGC3_IRTL: 0x0000884e (valid, 79872 ns)
cpu6: MSR_PKGC6_IRTL: 0x00008876 (valid, 120832 ns)
cpu6: MSR_PKGC7_IRTL: 0x00008894 (valid, 151552 ns)
cpu6: MSR_PKGC8_IRTL: 0x000088fa (valid, 256000 ns)
cpu6: MSR_PKGC9_IRTL: 0x0000894c (valid, 339968 ns)
cpu6: MSR_PKGC10_IRTL: 0x00008bf2 (valid, 1034240 ns)
Busy%	Bzy_MHz	IRQ	PkgTmp	PkgWatt
4.41	2282	50985	49	6.83
5.90	2327	36805	49	7.06
5.18	2332	47227	50	7.27
7.51	2361	40980	49	8.39
4.79	2293	52735	49	6.89
5.06	2359	43810	49	7.53
4.37	2275	60322	49	6.71




grep . /sys/devices/system/cpu/intel_pstate/*


/sys/devices/system/cpu/intel_pstate/max_perf_pct:100
/sys/devices/system/cpu/intel_pstate/min_perf_pct:50
/sys/devices/system/cpu/intel_pstate/no_turbo:0
/sys/devices/system/cpu/intel_pstate/num_pstates:43
/sys/devices/system/cpu/intel_pstate/status:active
/sys/devices/system/cpu/intel_pstate/turbo_pct:66

---

### Post by Doug S on 2019-02-01
> **dabsig said:**
> Here you go. This is on "normal" output. If you can not see anything suspicious here I would like to see if i can run the commands in a moment when the computer seems to have issues, and doesn't even responde with a immediate password prompt after a sudo command.This looks O.K. Yes, please run the commands when having issues.

Run this command all the time:
```
sudo turbostat --Summary --quiet --show Busy%,Bzy_MHz,PkgTmp,PkgWatt,IRQ --interval 15
```
> **dabsig said:**
> 
...
cpu0: MSR_PKG_POWER_INFO: 0x00000078 (15 W TDP, RAPL 0 - 0 W, 0.000000 sec.)
...
cpu0: PKG Limit #1: ENabled (51.000000 Watts, 24.000000 sec, clamp DISabled)
cpu0: PKG Limit #2: DISabled (51.000000 Watts, 0.002441* sec, clamp DISabled)
...


> **dabsig said:**
> 
grep . /sys/devices/system/cpu/intel_pstate/*


/sys/devices/system/cpu/intel_pstate/max_perf_pct:100  [COLOR="#FF0000"]<<< One method of throttling should reduce this[/COLOR]
/sys/devices/system/cpu/intel_pstate/min_perf_pct:50
/sys/devices/system/cpu/intel_pstate/no_turbo:0
/sys/devices/system/cpu/intel_pstate/num_pstates:43
/sys/devices/system/cpu/intel_pstate/status:active
/sys/devices/system/cpu/intel_pstate/turbo_pct:66

---

### Post by Doug S on 2019-02-01
> **dabsig said:**
> 
```
grep . /sys/devices/system/cpu/intel_pstate/*


/sys/devices/system/cpu/intel_pstate/max_perf_pct:100
/sys/devices/system/cpu/intel_pstate/min_perf_pct:[COLOR="#FF0000"]50[/COLOR][COLOR="#FF0000"]   <<<< This number is way too high.[/COLOR]
/sys/devices/system/cpu/intel_pstate/no_turbo:0
/sys/devices/system/cpu/intel_pstate/num_pstates:43
/sys/devices/system/cpu/intel_pstate/status:active
/sys/devices/system/cpu/intel_pstate/turbo_pct:[COLOR="#FF0000"]66   <<< ?? I calculate 60%? EDIT: O.K. I calc 66%, but don't understand why max non turbo ratio is 17.[/COLOR]
```
The min_perf_pct should be more like 9%, not 50%. I wonder what set that value and why? can you set it back?
```
$ echo 9 | sudo tee /sys/devices/system/cpu/intel_pstate/min_perf_pct
```Example (but for my processor 42% is the minimum):
```
doug@s15:~$ grep . /sys/devices/system/cpu/intel_pstate/*
/sys/devices/system/cpu/intel_pstate/max_perf_pct:100
/sys/devices/system/cpu/intel_pstate/min_perf_pct:[COLOR="#FF0000"]50[/COLOR]
/sys/devices/system/cpu/intel_pstate/no_turbo:0
/sys/devices/system/cpu/intel_pstate/num_pstates:23
/sys/devices/system/cpu/intel_pstate/status:active
/sys/devices/system/cpu/intel_pstate/turbo_pct:18
doug@s15:~$ [COLOR="#FF0000"]echo 9 | sudo tee /sys/devices/system/cpu/intel_pstate/min_perf_pct[/COLOR]
9
doug@s15:~$ grep . /sys/devices/system/cpu/intel_pstate/*
/sys/devices/system/cpu/intel_pstate/max_perf_pct:100
/sys/devices/system/cpu/intel_pstate/min_perf_pct:[COLOR="#FF0000"]42[/COLOR]   [COLOR="#FF0000"]<<< 42 is the minimum for my processor.[/COLOR]
/sys/devices/system/cpu/intel_pstate/no_turbo:0
/sys/devices/system/cpu/intel_pstate/num_pstates:23
/sys/devices/system/cpu/intel_pstate/status:active
/sys/devices/system/cpu/intel_pstate/turbo_pct:18

```

---

### Post by WinEunuchs2Unix on 2019-02-17
> **Doug S said:**
> You have focused on a graphics intensive test.
Additionally, I do not consider such things as a result of 1.00+-4600.00% to be a very good test.


I agree with Doug. Using nVidia GeForce GTX970M in my laptop the results were five times faster than with just native Intel HD 530 integrated graphics. That said my Motion Mark scores with nVidia GTX970M with 17 Firefox tabs open are:

- [FONT=courier new]intel_pstate[/FONT] **enabled**= 34.82
- [FONT=courier new]intel_pstate[/FONT] **disabled** = 66.90

The first test uses the `powersave` governor which means "less performance" in my mind. As such it seems to work properly.

[FONT=courier new]/sys/devices/system/cpu/intel_pstate$ dircat *
max_perf_pct  100
min_perf_pct  22
no_turbo      0
num_pstates   28
status        active
turbo_pct     33
[/FONT]

---

### Post by Doug S on 2019-02-17
@WinEunuchs2Unix: Thanks for doing this test on your Intel 6700 HQ based LapTop, which has HWP (HardWare Pstate control). Your results are not what I expected. Typically there is not such a difference between the intel_pstate CPU frequency scaling driver using the powersave governor and the acpi-cpufreq CPU frequency scaling driver using the ondemand governor.

@dabsig: Apologies for this digression on your thread.

@Readers: Some posts were deleted from this thread by the moderators. The claim was that the intel_pstate CPU scaling driver using the powersave governor performed poorly relative to the acpi-cpufreq CPU scaling driver using the ondemand governor. WinEunuchs2Unix was just confirming the results for this particular test. I am a server person, and do not have the proper hardware to do the test for myself. The test is [here]("https://browserbench.org/MotionMark1.1/").

---

