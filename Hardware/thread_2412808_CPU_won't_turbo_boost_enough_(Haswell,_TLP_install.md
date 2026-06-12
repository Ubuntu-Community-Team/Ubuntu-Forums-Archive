---
title: "CPU won't turbo boost enough (Haswell, TLP installed)"
date: 2019-02-17
forum: Hardware
---

### Post by sf6 on 2019-02-17
Hello,

I'm having trouble getting full perfomance out of my little Haswell based Panasonic CF-SX3 notebook.
If I used lscpu | grep MHz it shows that the max frequency should be 2.9 Ghz (i5 4300U).
But I never reach this CPU frequency. When all four threads are in use, I get 2 Ghz out of it (as shown by lscpu | grep MHz).

This should be quite a bit higher, and it shows as 2 Ghz really is not much.
How should I go about this? First an foremost, is there a way to reliably trace the CPU frequency in Ubuntu? Is there a way to extract the current TDP envelope?

Thanks for your help :)

---

### Post by Doug S on 2019-02-18
The tool for this is "turbostat", which is included in the linux-tools-common package.
To start with, you want an bunch of information that turbostat will spew on startup. Perhaps post it here for us to also review. I'll do an example from my test server (normally I run the same command, but with "--quite" for no big spew):

```
doug@s15:~$ [COLOR="#FF0000"]sudo turbostat --Summary --show Busy%,Bzy_MHz,PkgTmp,PkgWatt,IRQ --interval 15[/COLOR]
[sudo] password for doug:
turbostat version 18.07.27 - Len Brown <lenb@kernel.org>
CPUID(0): GenuineIntel 13 CPUID levels; family:model:stepping 0x6:2a:7 (6:42:7)
CPUID(1): SSE3 MONITOR - EIST TM2 TSC MSR ACPI-TM HT TM
CPUID(6): APERF, TURBO, DTS, PTM, No-HWP, No-HWPnotify, No-HWPwindow, No-HWPepp, No-HWPpkg, EPB
cpu0: MSR_IA32_MISC_ENABLE: 0x00850089 (TCC EIST MWAIT PREFETCH TURBO)
CPUID(7): No-SGX
cpu0: MSR_MISC_PWR_MGMT: 0x00400000 (ENable-EIST_Coordination DISable-EPB DISable-OOB)
RAPL: 690 sec. Joule Counter Range, at 95 Watts
cpu0: MSR_PLATFORM_INFO: 0x100070012200
16 * 100.0 = 1600.0 MHz max efficiency frequency
34 * 100.0 = 3400.0 MHz base frequency
cpu0: MSR_IA32_POWER_CTL: 0x0004005d (C1E auto-promotion: DISabled)
cpu0: MSR_TURBO_RATIO_LIMIT: 0x23242526
[COLOR="#FF0000"]35 * 100.0 = 3500.0 MHz max turbo 4 active cores
36 * 100.0 = 3600.0 MHz max turbo 3 active cores
37 * 100.0 = 3700.0 MHz max turbo 2 active cores
38 * 100.0 = 3800.0 MHz max turbo 1 active cores[/COLOR]
cpu0: MSR_PKG_CST_CONFIG_CONTROL: 0x1e008403 (UNdemote-C3, UNdemote-C1, demote-C3, demote-C1, locked, pkg-cstate-limit=3 (pc6r))
cpu0: cpufreq driver: intel_pstate
cpu0: cpufreq governor: powersave
cpufreq intel_pstate no_turbo: 0
cpu0: MSR_MISC_FEATURE_CONTROL: 0x00000000 (L2-Prefetch L2-Prefetch-pair L1-Prefetch L1-IP-Prefetch)
cpu0: MSR_IA32_ENERGY_PERF_BIAS: 0x00000006 (balanced)
cpu0: MSR_RAPL_POWER_UNIT: 0x000a1003 (0.125000 Watts, 0.000015 Joules, 0.000977 sec.)
[COLOR="#FF0000"]cpu0: MSR_PKG_POWER_INFO: 0x01e002f8 (95 W TDP, RAPL 60 - 0 W, 0.000000 sec.)[/COLOR]
cpu0: MSR_PKG_POWER_LIMIT: 0x800087f8001487f8 (locked)
cpu0: PKG Limit #1: ENabled (255.000000 Watts, 1.000000 sec, clamp DISabled)
cpu0: PKG Limit #2: ENabled (255.000000 Watts, 0.000977* sec, clamp DISabled)
cpu0: MSR_PP0_POLICY: 0
cpu0: MSR_PP0_POWER_LIMIT: 0x00000000 (UNlocked)
cpu0: Cores Limit: DISabled (0.000000 Watts, 0.000977 sec, clamp DISabled)
cpu0: MSR_PP1_POLICY: 0
cpu0: MSR_PP1_POWER_LIMIT: 0x00000000 (UNlocked)
cpu0: GFX Limit: DISabled (0.000000 Watts, 0.000977 sec, clamp DISabled)
cpu0: MSR_IA32_TEMPERATURE_TARGET: 0x00621200 (98 C)
cpu0: MSR_IA32_PACKAGE_THERM_STATUS: 0x88440000 (30 C)
cpu0: MSR_IA32_PACKAGE_THERM_INTERRUPT: 0x00000003 (98 C, 98 C)
cpu0: MSR_PKGC3_IRTL: 0x00008850 (valid, 81920 ns)
cpu0: MSR_PKGC6_IRTL: 0x00008868 (valid, 106496 ns)
cpu0: MSR_PKGC7_IRTL: 0x0000886d (valid, 111616 ns)
Busy%   Bzy_MHz IRQ     PkgTmp  PkgWatt
0.03    1606    808     25      3.69
0.03    1600    729     25      3.69
6.60    3785    8962    38      13.59
12.53   3799    16157   41      22.84   [COLOR="#FF0000"]<<< CPU 7 100% load, 1 core active[/COLOR]
12.53   3799    16137   42      22.96
18.79   3731    26571   47      28.90
25.03   3697    36413   50      35.02    [COLOR="#FF0000"]<<< add CPU 6 100% load, 2 cores active[/COLOR]
35.66   3607    49414   54      44.48    [COLOR="#FF0000"]<<< add CPU 5 100% load, 3 cores active[/COLOR]
47.98   3514    63265   59      54.75
50.27   3500    66412   62      57.26    [COLOR="#FF0000"]<<< add CPU 4 100% load, 4 cores active[/COLOR]
50.25   3500    65561   66      58.16
50.24   3500    65419   67      58.55
45.32   3531    60999   66      54.73    [COLOR="#FF0000"]<<< now start removing the loads[/COLOR]
37.50   3597    52024   66      48.20
36.19   3604    51570   64      47.07
25.02   3697    36465   63      36.65
16.61   3749    22562   59      28.28
12.53   3799    16265   57      24.10
3.02    3779    4454    42      8.75
0.03    1600    749     39      3.89
0.03    1600    734     37      3.86
0.03    1600    750     36      3.83
^C0.03  1600    296     36      3.82

```Now lets look at some throttling intervention. I don't use tlp, but will use thermald with a temperature trip point of 57 degrees for this example:
```
doug@s15:~$ [COLOR="#FF0000"]sudo turbostat --Summary --quiet --show Busy%,Bzy_MHz,PkgTmp,PkgWatt,IRQ --interval 15[/COLOR]
Busy%   Bzy_MHz IRQ     PkgTmp  PkgWatt
0.04    1600    900     28      3.73
0.04    1600    773     28      3.73
53.79   3510    66572   51      38.35
100.00  3500    120462  56      58.98    [COLOR="#FF0000"]<<< heavy load applied. Note package temperature[/COLOR]
100.00  2677    120469  51      41.69    [COLOR="#FF0000"]<<<< Note the CPU clock has been throttled back.[/COLOR]
100.00  2418    120528  55      36.63
100.00  2434    120517  52      37.02
100.00  2140    120459  57      31.72
66.62   2471    80826   42      26.43     [COLOR="#FF0000"]<<<< The load has been removed[/COLOR]
0.05    1600    1037    39      3.90
0.03    1600    772     37      3.85
^C0.03  1600    74      36      3.83
```At the same time observe the maximum performance percent:
```
doug@s15:~$ cat /sys/devices/system/cpu/intel_pstate/max_perf_pct
100
doug@s15:~$ cat /sys/devices/system/cpu/intel_pstate/max_perf_pct
60          [COLOR="#FF0000"]<<<< thermald has scaled back the maximum so as to reduce the processor temperature.[/COLOR]
doug@s15:~$ cat /sys/devices/system/cpu/intel_pstate/max_perf_pct
70
doug@s15:~$ cat /sys/devices/system/cpu/intel_pstate/max_perf_pct
60           [COLOR="#FF0000"]<<<< it tends to oscillate some, but does the job.[/COLOR]
doug@s15:~$ cat /sys/devices/system/cpu/intel_pstate/max_perf_pct
70
doug@s15:~$ cat /sys/devices/system/cpu/intel_pstate/max_perf_pct
70
doug@s15:~$ cat /sys/devices/system/cpu/intel_pstate/max_perf_pct
80          [COLOR="#FF0000"]<<<< the load has been removed and thermald restores performance as the processor temperature drops.[/COLOR]
doug@s15:~$ cat /sys/devices/system/cpu/intel_pstate/max_perf_pct
80
doug@s15:~$ cat /sys/devices/system/cpu/intel_pstate/max_perf_pct
90
doug@s15:~$ cat /sys/devices/system/cpu/intel_pstate/max_perf_pct
100          [COLOR="#FF0000"]<<<< until finally full performance has been restored.[/COLOR]

```

---

