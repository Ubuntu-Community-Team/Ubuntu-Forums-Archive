---
title: "CPU has no covid but is permanently in lockdown!"
date: 2022-02-04
forum: Hardware
---

### Post by linucyphre on 2022-02-04
I have a problem with the CPUs of my PANASONIC TOUGHPAD FZ-M1 MK1. Normally the Toughpad works between 600MHz and 2300MHz. Under WINDOWS 10 it works without any problems - up to 2300 MHz Turbo and even 4K films are played smoothly.

Under UBUNTU, the frequency remains at the minimum value of 600 MHz. At 100% load, this value does not change.
I've researched and tried several suggested solutions from the web - with no success.

Here's my system:


Scaling-Driver:
```

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_driver
intel_cpufreq

```

Turbostat:
```

sudo turbostat
turbostat version 21.05.04 - Len Brown <lenb@kernel.org>
CPUID(0): GenuineIntel 0xd CPUID levels
CPUID(1): family:model:stepping 0x6:45:1 (6:69:1) microcode 0x26
CPUID(0x80000000): max_extended_levels: 0x80000008
CPUID(1): SSE3 MONITOR SMX EIST TM2 TSC MSR ACPI-TM HT TM
CPUID(6): APERF, TURBO, DTS, PTM, No-HWP, No-HWPnotify, No-HWPwindow, No-HWPepp, No-HWPpkg, EPB
cpu3: MSR_IA32_MISC_ENABLE: 0x00850089 (TCC EIST MWAIT PREFETCH TURBO)
CPUID(7): No-SGX
cpu3: MSR_MISC_PWR_MGMT: 0x00400000 (ENable-EIST_Coordination DISable-EPB DISable-OOB)
RAPL: 22795 sec. Joule Counter Range, at 12 Watts
cpu3: MSR_PLATFORM_INFO: 0x6063bf3011000
6 * 100.0 = 600.0 MHz max efficiency frequency
16 * 100.0 = 1600.0 MHz base frequency
cpu3: MSR_IA32_POWER_CTL: 0x0004005d (C1E auto-promotion: DISabled)
cpu3: MSR_TURBO_RATIO_LIMIT: 0x14141417
20 * 100.0 = 2000.0 MHz max turbo 4 active cores
20 * 100.0 = 2000.0 MHz max turbo 3 active cores
20 * 100.0 = 2000.0 MHz max turbo 2 active cores
23 * 100.0 = 2300.0 MHz max turbo 1 active cores
cpu3: MSR_CONFIG_TDP_NOMINAL: 0x00000010 (base_ratio=16)
cpu3: MSR_CONFIG_TDP_LEVEL_1: 0x0008004c (PKG_MIN_PWR_LVL1=0 PKG_MAX_PWR_LVL1=0 LVL1_RATIO=8 PKG_TDP_LVL1=76)
cpu3: MSR_CONFIG_TDP_LEVEL_2: 0x00000000 ()
cpu3: MSR_CONFIG_TDP_CONTROL: 0x00000001 (TDP_LEVEL=1  lock=0)
cpu3: MSR_TURBO_ACTIVATION_RATIO: 0x00000007 (MAX_NON_TURBO_RATIO=7 lock=0)
cpu3: MSR_PKG_CST_CONFIG_CONTROL: 0x1e008405 (UNdemote-C3, UNdemote-C1, demote-C3, demote-C1, locked, pkg-cstate-limit=5 (pc7s))
/dev/cpu_dma_latency: 2000000000 usec (default)
current_driver: intel_idle
current_governor: menu
current_governor_ro: menu
cpu3: POLL: CPUIDLE CORE POLL IDLE
cpu3: C1: MWAIT 0x00
cpu3: C1E: MWAIT 0x01
cpu3: C3: MWAIT 0x10
cpu3: C6: MWAIT 0x20
cpu3: C7s: MWAIT 0x32
cpu3: C8: MWAIT 0x40
cpu3: C9: MWAIT 0x50
cpu3: C10: MWAIT 0x60
cpu3: cpufreq driver: intel_cpufreq
cpu3: cpufreq governor: ondemand
cpufreq intel_pstate no_turbo: 0
cpu3: MSR_MISC_FEATURE_CONTROL: 0x00000000 (L2-Prefetch L2-Prefetch-pair L1-Prefetch L1-IP-Prefetch)
cpu0: EPB: 4 (custom)
cpu0: MSR_CORE_PERF_LIMIT_REASONS, 0x14000400 (Active: PkgPwrL1, ) (Logged: MultiCoreTurbo, PkgPwrL1, )
cpu0: MSR_GFX_PERF_LIMIT_REASONS, 0x14001400 (Active: PkgPwrL1, ) (Logged: PkgPwrL1, )
cpu0: MSR_RING_PERF_LIMIT_REASONS, 0x00000000 (Active: ) (Logged: )
cpu0: MSR_RAPL_POWER_UNIT: 0x000a0e03 (0.125000 Watts, 0.000061 Joules, 0.000977 sec.)
cpu0: MSR_PKG_POWER_INFO: 0x0000005c (12 W TDP, RAPL 0 - 0 W, 0.000000 sec.)
cpu0: MSR_PKG_POWER_LIMIT: 0x804280c800dd805c (locked)
cpu0: PKG Limit #1: ENabled (11.500000 Watts, 28.000000 sec, clamp ENabled)
cpu0: PKG Limit #2: ENabled (25.000000 Watts, 0.002441* sec, clamp DISabled)
cpu0: MSR_PP0_POLICY: 0
cpu0: MSR_PP0_POWER_LIMIT: 0x00000000 (UNlocked)
cpu0: Cores Limit: DISabled (0.000000 Watts, 0.000977 sec, clamp DISabled)
cpu0: MSR_PP1_POLICY: 0
cpu0: MSR_PP1_POWER_LIMIT: 0x00000000 (UNlocked)
cpu0: GFX Limit: DISabled (0.000000 Watts, 0.000977 sec, clamp DISabled)
cpu0: MSR_IA32_TEMPERATURE_TARGET: 0x00640000 (100 C)
cpu0: MSR_IA32_PACKAGE_THERM_STATUS: 0x882a0c00 (58 C)
cpu0: MSR_IA32_PACKAGE_THERM_INTERRUPT: 0x00000003 (100 C, 100 C)
cpu3: MSR_PKGC3_IRTL: 0x00008842 (valid, 67584 ns)
cpu3: MSR_PKGC6_IRTL: 0x00008873 (valid, 117760 ns)
cpu3: MSR_PKGC7_IRTL: 0x00008891 (valid, 148480 ns)
cpu3: MSR_PKGC8_IRTL: 0x000088e4 (valid, 233472 ns)
cpu3: MSR_PKGC9_IRTL: 0x00008945 (valid, 332800 ns)
cpu3: MSR_PKGC10_IRTL: 0x000089ef (valid, 506880 ns)
Core    CPU     Avg_MHz Busy%   Bzy_MHz TSC_MHz IPC     IRQ     SMI     POLL    C1      C1E     C3      C6      C7s     C8      C9      C10   POLL%    C1%     C1E%    C3%     C6%     C7s%    C8%     C9%     C10%    CPU%c1  CPU%c3  CPU%c6  CPU%c7  CoreTmp PkgTmp  GFX%rc6 GFXMHz  GFXAMHzPkg%pc2 Pkg%pc3 Pkg%pc6 Pkg%pc7 PkgWatt CorWatt GFXWatt
-       -       599     100.00  600     1596    0.99    10656   0       0       0       0       0       0       0       0       0       0     0.00     0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00    58      58      52.43   350     150   0.00     0.00    0.00    0.00    6.22    1.91    0.37
0       0       599     100.00  600     1596    1.02    2334    0       0       0       0       0       0       0       0       0       0     0.00     0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00    57      58      52.42   350     150   0.00     0.00    0.00    0.00    6.22    1.91    0.37
0       2       599     100.00  600     1596    1.01    3112    0       0       0       0       0       0       0       0       0       0     0.00     0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00
1       1       599     100.00  600     1596    1.01    2829    0       0       0       0       0       0       0       0       0       0     0.00     0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00    58
1       3       599     100.00  600     1596    0.92    2381    0       0       0       0       0       0       0       0       0       0     0.00     0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00

```

Cpufreq.info:
```

cpufreq.info
cpufrequtils 008: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: intel_cpufreq
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 20.0 us.
  hardware limits: 600 MHz - 2.30 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance, schedutil
  current policy: frequency should be within 600 MHz and 2.30 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 599 MHz.
analyzing CPU 1:
  driver: intel_cpufreq
  CPUs which run at the same hardware frequency: 1
  CPUs which need to have their frequency coordinated by software: 1
  maximum transition latency: 20.0 us.
  hardware limits: 600 MHz - 2.30 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance, schedutil
  current policy: frequency should be within 600 MHz and 2.30 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 599 MHz.
analyzing CPU 2:
  driver: intel_cpufreq
  CPUs which run at the same hardware frequency: 2
  CPUs which need to have their frequency coordinated by software: 2
  maximum transition latency: 20.0 us.
  hardware limits: 600 MHz - 2.30 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance, schedutil
  current policy: frequency should be within 600 MHz and 2.30 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 599 MHz.
analyzing CPU 3:
  driver: intel_cpufreq
  CPUs which run at the same hardware frequency: 3
  CPUs which need to have their frequency coordinated by software: 3
  maximum transition latency: 20.0 us.
  hardware limits: 600 MHz - 2.30 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance, schedutil
  current policy: frequency should be within 600 MHz and 2.30 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 599 MHz.

```

Kernel:
```

uname -a
Linux hrf1 5.13.0-28-generic #31~20.04.1-Ubuntu SMP Wed Jan 19 14:08:10 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

```


The lscpu output:
```

lscpu
Architektur:                     x86_64
CPU Operationsmodus:             32-bit, 64-bit
Byte-Reihenfolge:                Little Endian
Adressgrößen:                    39 bits physical, 48 bits virtual
CPU(s):                          4
Liste der Online-CPU(s):         0-3
Thread(s) pro Kern:              2
Kern(e) pro Socket:              2
Sockel:                          1
NUMA-Knoten:                     1
Anbieterkennung:                 GenuineIntel
Prozessorfamilie:                6
Modell:                          69
Modellname:                      Intel(R) Core(TM) i5-4302Y CPU @ 1.60GHz
Stepping:                        1
CPU MHz:                         1000.000
Maximale Taktfrequenz der CPU:   2300,0000
Minimale Taktfrequenz der CPU:   600,0000
BogoMIPS:                        3192.66
Virtualisierung:                 VT-x
L1d Cache:                       64 KiB
L1i Cache:                       64 KiB
L2 Cache:                        512 KiB
L3 Cache:                        3 MiB
NUMA-Knoten0 CPU(s):             0-3
Vulnerability Itlb multihit:     KVM: Mitigation: VMX disabled
Vulnerability L1tf:              Mitigation; PTE Inversion; VMX conditional cache flushes, SMT vulnerable
Vulnerability Mds:               Mitigation; Clear CPU buffers; SMT vulnerable
Vulnerability Meltdown:          Mitigation; PTI
Vulnerability Spec store bypass: Mitigation; Speculative Store Bypass disabled via prctl and seccomp
Vulnerability Spectre v1:        Mitigation; usercopy/swapgs barriers and __user pointer sanitization
Vulnerability Spectre v2:        Mitigation; Full generic retpoline, IBPB conditional, IBRS_FW, STIBP conditional, RSB filling
Vulnerability Srbds:             Mitigation; Microcode
Vulnerability Tsx async abort:   Not affected
Markierungen:                    fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss 
                                 ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc 
                                 cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1
                                  sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm cpuid_fault epb invpcid_s
                                 ingle pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep
                                  bmi2 erms invpcid xsaveopt dtherm ida arat pln pts md_clear flush_l1d

```


The lsmod output:
```

lsmod | grep intel
btintel                32768  1 btusb
bluetooth             651264  45 btrtl,btintel,btbcm,bnep,btusb,rfcomm
snd_hda_intel          53248  4
snd_intel_dspcfg       28672  1 snd_hda_intel
intel_rapl_msr         20480  0
snd_intel_sdw_acpi     20480  1 snd_intel_dspcfg
snd_hda_codec         147456  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           94208  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_pcm               114688  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
intel_powerclamp       20480  0
kvm_intel             303104  0
kvm                   864256  1 kvm_intel
intel_cstate           20480  0
intel_pch_thermal      20480  0
snd                    94208  20 snd_ctl_led,snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
intel_rapl_common      24576  2 intel_rapl_msr,processor_thermal_rapl
intel_soc_dts_iosf     20480  1 processor_thermal_device
intel_vbtn             20480  0
sparse_keymap          16384  2 intel_vbtn,panasonic_laptop
intel_smartconnect     16384  0
ghash_clmulni_intel    16384  0
aesni_intel           376832  20
crypto_simd            16384  1 aesni_intel
cryptd                 24576  7 crypto_simd,ghash_clmulni_intel

```

the i7z output:
```

sudo i7z 
i7z DEBUG: i7z version: svn-r93-(27-MAY-2013)
i7z DEBUG: Found Intel Processor
i7z DEBUG:    Stepping 1
i7z DEBUG:    Model 5
i7z DEBUG:    Family 6
i7z DEBUG:    Processor Type 0
i7z DEBUG:    Extended Model 4
i7z DEBUG: msr = Model Specific Register
i7z DEBUG: Unknown processor, not exactly based on Nehalem, Sandy bridge or Ivy Bridge
i7z DEBUG: msr device files exist /dev/cpu/*/msr
i7z DEBUG: You have write permissions to msr device files

------------------------------
--[core id]--- Other information
-------------------------------------
--[0] Processor number 0
--[0] Socket number/Hyperthreaded Sibling number  0,2
--[0] Core id number 0
--[0] Display core in i7z Tool: Yes

--[1] Processor number 1
--[1] Socket number/Hyperthreaded Sibling number  0,3
--[1] Core id number 1
--[1] Display core in i7z Tool: Yes

--[2] Processor number 2
--[2] Socket number/Hyperthreaded Sibling number  0,0
--[2] Core id number 0
--[2] Display core in i7z Tool: No

--[3] Processor number 3
--[3] Socket number/Hyperthreaded Sibling number  0,1
--[3] Core id number 1
--[3] Display core in i7z Tool: No

Socket-0 [num of cpus 2 physical 2 logical 4] 0,1,
Socket-1 [num of cpus 0 physical 0 logical 0] 
GUI has been Turned ON
i7z DEBUG: Single Socket Detected
i7z DEBUG: In i7z Single_Socket()
i7z DEBUG: guessing Nehalem
hrf1@hrf1:~$ 


Cpu speed from cpuinfo 1596.00Mhz
cpuinfo might be wrong if cpufreq is enabled. To guess correctly try estimating via tsc
Linux's inbuilt cpu_khz code emulated now
True Frequency (without accounting Turbo) 1596 MHz
  CPU Multiplier 16x || Bus clock frequency (BCLK) 99.75 MHz

Socket [0] - [physical cores=2, logical cores=4, max online cores ever=2]
  TURBO ENABLED on 2 Cores, Hyper Threading ON
  Max Frequency without considering Turbo 1695.75 MHz (99.75 x [17])
  Max TURBO Multiplier (if Enabled) with 1/2/3/4 Cores is  23x/20x/20x/20x
  Real Current Frequency 598.50 MHz [99.75 x 6.00] (Max of below)
        Core [core-id]  :Actual Freq (Mult.)      C0%   Halt(C1)%  C3 %   C6 %  Temp      VCore
        Core 1 [0]:       598.50 (6.00x)         100    62.5       0       0    60      0.5906
        Core 2 [1]:       598.46 (6.00x)         100    62.5       0       0    61      0.5912





C0 = Processor running without halting
C1 = Processor running with halts (States >C0 are power saver modes with cores idling)
C3 = Cores running with PLL turned off and core cache turned off
C6, C7 = Everything in C3 + core state saved to last level cache, C7 is deeper than C6
  Above values in table are in percentage over the last 1 sec
[core-id] refers to core-id number in /proc/cpuinfo
'Garbage Values' message printed when garbage values are read
  Ctrl+C to exit

```

Steps to find a solution:

1. I've enabled the intel_pstate driver from passive to active in bios:
```
 intel_pstate=active
```
with no effect.

2. I've disabled the intel_pstate driver completeley to get the old acpi driver:
```
 intel_pstate=disable
```
with no effect.

3. I've disabled the intel_pstate hwp:
```
 intel_pstate=no_hwp
```
with no effect.

4. I removed the battery and disconnected the power supply. Then pressed the power button for 20 seconds
with no effect.

5. I've changed the msr registry
```
 sudo modprobe msr
sudo wrmsr 0x1FC value 
```
with no effect.

6. In WINDOWS 10 i disabled the PROCHAT tag in throttlestop
with no effect.

7. I've changed the settings in cpupower-gui to performance
with no effect.

8. I successfully installed trhrottlestop from github
but didn't realise any changes.

9. Found thermal problems, 
[FONT=monospace][COLOR=#000000]```

dmesg | grep therm [/COLOR]
[    0.295370] [COLOR=#ff5454]**therm**[/COLOR][COLOR=#000000]al_sys: Registered [/COLOR][COLOR=#ff5454]**therm**[/COLOR][COLOR=#000000]al governor 'fair_share' [/COLOR]
[    0.295370] [COLOR=#ff5454]**therm**[/COLOR][COLOR=#000000]al_sys: Registered [/COLOR][COLOR=#ff5454]**therm**[/COLOR][COLOR=#000000]al governor 'bang_bang' [/COLOR]
[    0.295370] [COLOR=#ff5454]**therm**[/COLOR][COLOR=#000000]al_sys: Registered [/COLOR][COLOR=#ff5454]**therm**[/COLOR][COLOR=#000000]al governor 'step_wise' [/COLOR]
[    0.295370] [COLOR=#ff5454]**therm**[/COLOR][COLOR=#000000]al_sys: Registered [/COLOR][COLOR=#ff5454]**therm**[/COLOR][COLOR=#000000]al governor 'user_space' [/COLOR]
[    0.295370] [COLOR=#ff5454]**therm**[/COLOR][COLOR=#000000]al_sys: Registered [/COLOR][COLOR=#ff5454]**therm**[/COLOR][COLOR=#000000]al governor 'power_allocator' [/COLOR]
[    0.821805] [COLOR=#ff5454]**therm**[/COLOR][COLOR=#000000]al LNXTHERM:00: registered as [/COLOR][COLOR=#ff5454]**therm**[/COLOR][COLOR=#000000]al_zone0 [/COLOR]
[    0.821826] ACPI: [COLOR=#ff5454]**therm**[/COLOR][COLOR=#000000]al: Thermal Zone [TZ00] (51 C) [/COLOR]
[    0.831707] [COLOR=#ff5454]**therm**[/COLOR][COLOR=#000000]al LNXTHERM:01: registered as [/COLOR][COLOR=#ff5454]**therm**[/COLOR][COLOR=#000000]al_zone1 [/COLOR]
[    0.831724] ACPI: [COLOR=#ff5454]**therm**[/COLOR][COLOR=#000000]al: Thermal Zone [TZ01] (51 C) [/COLOR]
[   10.157461] [COLOR=#ff5454]**therm**[/COLOR][COLOR=#000000]al_sys: Error: Incorrect number of [/COLOR][COLOR=#ff5454]**therm**[/COLOR][COLOR=#000000]al trips [/COLOR]
[   10.157688] int3402 [COLOR=#ff5454]**therm**[/COLOR][COLOR=#000000]al: probe of INT3402:00 failed with error -22 [/COLOR]
[   10.516447] [COLOR=#ff5454]**therm**[/COLOR][COLOR=#000000]al_sys: Error: Incorrect number of [/COLOR][COLOR=#ff5454]**therm**[/COLOR][COLOR=#000000]al trips [/COLOR]
[   10.516690] int3403 [COLOR=#ff5454]**therm**[/COLOR][COLOR=#000000]al: probe of INT3403:01 failed with error -22 [/COLOR]
[   10.619520] proc_[COLOR=#ff5454]**therm**[/COLOR][COLOR=#000000]al 0000:00:04.0: enabling device (0000 -> 0002) [/COLOR]
[   10.703657] intel_pch_[COLOR=#ff5454]**therm**[/COLOR][COLOR=#000000]al 0000:00:1f.6: enabling device (0000 -> 0002) [/COLOR]
[   10.849416] [COLOR=#ff5454]**therm**[/COLOR][COLOR=#000000]al_sys: Error: Incorrect number of [/COLOR][COLOR=#ff5454]**therm**[/COLOR][COLOR=#000000]al trips [/COLOR]
[   10.850806] proc_[COLOR=#ff5454]**therm**[/COLOR][COLOR=#000000]al: probe of 0000:00:04.0 failed with error -22[/COLOR]

```
[/FONT]so disabled thermald - but this has no effect.


I would be very, very happy about any help.

---

### Post by linucyphre on 2022-02-05
Maybe there is a command to manually set the cpu scaling factor?

---

### Post by Frogs Hair on 2022-02-05
You could  install cpupower-gui and see if that works for you. I have not tried it myself. ```
sudo apt install cpupower-gui
```

---

### Post by linucyphre on 2022-02-06
Hello FrogsHair,

thank you for the response. Cpupower-gui is already installed and tested.
Unfortunately changing the parameters does not have an effect on the frequency behavior.:(

---

### Post by linucyphre on 2022-02-12
I'm one step further now. And more frustrated.

I put a new hard drive in and resetted everything in the BIOS. One system - Kubuntu - no Windows. Amazingly, the frequency scaling worked. But only as long as there was no heavy / normal load. Then the processor is throttling again. If the temperatures rise 57 degrees, the cpus are full throttling. Changing the limits with the plasmoid pstate tool is prohibited by the bios.

When re-attaching the old SSD again the old problem still exists. 

I think Windows writes something in the BIOS that prevents other OSes to work.
This myght be a Panasonic or fanless problem.

Any idea?

---

### Post by uninvolved on 2022-02-12
What are your temps like?

---

### Post by Doug S on 2022-02-12
I missed this thread until now.
I can help you with this, but I only use primitive commands for CPU frequency scaling type stuff, never any higher level tool. Turbostat is the preferred monitoring utility. If thermald is needed, which it never is on my systems, then I prefer to use a very simple configuration file.

It does seem as though your issues are thermal, and your processor seems rather warm for operating 100% at 600MHz. Your processor also has a low TDP (Thermal Design Power).

When your system is throttled, what do you get for:

```
grep -r . /sys/devices/system/cpu/cpu*/thermal_throttle/*
```

and what do you get for (is Clock Modulation involved?) (needs msr module to already be loaded):

```
sudo rdmsr -a 0x19a
```

The first challenge is to simply get your system to boot without it going into full throttled mode so that you can observe package temperature as a function of load and CPU frequency. Why? One needs to understand the relationship between load/CPU frequency/energy/temperature in order to decide the best way to prevent overheat and/or power limit and/or something else causing throttling.

Does it currently complete boot without being fully throttled? i.e. before you run any user heavy load?
If no, then I would try disabling tubo in BIOS, to see if the system at least can complete boot without such a severe throttle that it locks up.
If still no, then try to boot forcing the intel_pstate CPU frequency scaling driver into passive mode (A.K.A. intel_cpufreq) and the powersave governor. This will limit CPU frequency to minimum as soon as possible in the boot cycle. Example grub line:

```
GRUB_CMDLINE_LINUX_DEFAULT="intel_pstate=passive intel_pstate=no_hwp cpufreq.default_governor=powersave"
```

And the my system version of the same thing, with some other stuff I do:

```
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 consoleblank=450 intel_pstate=passive intel_pstate=no_hwp cpufreq.default_governor=powersave msr.allow_writes=on cpuidle.governor=teo"
```

There are many columns in turbostat that are not needed for this work. I suggest this:

sudo turbostat --Summary --quiet --show Busy%,Bzy_MHz,IRQ,PkgWatt,PkgTmp,GFXWatt,CorWatt --interval 6

Once properly booted, then gradually add loads and raise frequency restrictions, while monitoring with turbostat to understand your systems thermal abilities. (my test computer is busy right now, so I can not provide and example).

Another option might be to just implement a simple thermald configuration and try it. Use a relatively low thermal trip point to get started. For example:

```
doug@s19:~/freq-scalers/long_dur$ cat /home/doug/config/etc/thermald/thermal-conf.xml
<?xml version="1.0"?>

<!--
use "man thermal-conf.xml" for details
-->

<!-- BEGIN -->
<ThermalConfiguration>
        <Platform>
                <Name>Overide CPU default passive</Name>
                <ProductName>*</ProductName>
                <Preference>QUIET</Preference>
                <ThermalZones>
                        <ThermalZone>
                                <Type>cpu</Type>
                                <TripPoints>
                                        <TripPoint>
                                                <Temperature>55000</Temperature>
                                                <type>passive</type>
                                        </TripPoint>
                                </TripPoints>
                        </ThermalZone>
                </ThermalZones>
        </Platform>
</ThermalConfiguration>
<!-- END -->
```

and:

```
doug@s19:~/freq-scalers/long_dur$ cat /home/doug/config/etc/thermald/thermal-cpu-cdev-order.xml

<!--
For cpufreq - do max frequency first. Smythies 2019.07.16
Specifies the order of compensation to cool CPU only.
There is a default already implemented in the code, but
this file can be used to change order

The Following cooling device can present
-->

<CoolingDeviceOrder>
        <!-- Specify Cooling device order -->
        <CoolingDevice>intel_pstate</CoolingDevice>
        <CoolingDevice>cpufreq</CoolingDevice>
</CoolingDeviceOrder>
```

And yes, I would suggest 55 degrees to start with. Although, you might have to set it to 65 to even get started, as you are already at 58 @600MHz. This method needs plenty of head room, because the thermal servo reaction time is slow realtive to how fast the processor package temperature can increase due to a step function load increase. i.e. the temperature will overshoot before thermald kicks in to limit the CPU frequency. 

Anyway, Lets see how you make out, and we'll go from there.

EDIT: By the way, you processor does not have HWP.

---

### Post by linucyphre on 2022-02-13
Thank you very much for the extensive help.
So step by step:

@uninvolved
The temperature is currently between 48 and 54 degrees. The frequency moves between 598 MHz and 600 MHz.
Both values do not change even under load.

@Doug S
Here is the output when the system is throttled:
```

hrf1@hrf1:~$ grep -r . /sys/devices/system/cpu/cpu*/thermal_throttle/*
/sys/devices/system/cpu/cpu0/thermal_throttle/core_throttle_count:0
/sys/devices/system/cpu/cpu0/thermal_throttle/core_throttle_max_time_ms:0
/sys/devices/system/cpu/cpu0/thermal_throttle/core_throttle_total_time_ms:0
/sys/devices/system/cpu/cpu0/thermal_throttle/package_throttle_count:0
/sys/devices/system/cpu/cpu0/thermal_throttle/package_throttle_max_time_ms:0
/sys/devices/system/cpu/cpu0/thermal_throttle/package_throttle_total_time_ms:0
/sys/devices/system/cpu/cpu1/thermal_throttle/core_throttle_count:0
/sys/devices/system/cpu/cpu1/thermal_throttle/core_throttle_max_time_ms:0
/sys/devices/system/cpu/cpu1/thermal_throttle/core_throttle_total_time_ms:0
/sys/devices/system/cpu/cpu1/thermal_throttle/package_throttle_count:0
/sys/devices/system/cpu/cpu1/thermal_throttle/package_throttle_max_time_ms:0
/sys/devices/system/cpu/cpu1/thermal_throttle/package_throttle_total_time_ms:0
/sys/devices/system/cpu/cpu2/thermal_throttle/core_throttle_count:0
/sys/devices/system/cpu/cpu2/thermal_throttle/core_throttle_max_time_ms:0
/sys/devices/system/cpu/cpu2/thermal_throttle/core_throttle_total_time_ms:0
/sys/devices/system/cpu/cpu2/thermal_throttle/package_throttle_count:0
/sys/devices/system/cpu/cpu2/thermal_throttle/package_throttle_max_time_ms:0
/sys/devices/system/cpu/cpu2/thermal_throttle/package_throttle_total_time_ms:0
/sys/devices/system/cpu/cpu3/thermal_throttle/core_throttle_count:0
/sys/devices/system/cpu/cpu3/thermal_throttle/core_throttle_max_time_ms:0
/sys/devices/system/cpu/cpu3/thermal_throttle/core_throttle_total_time_ms:0
/sys/devices/system/cpu/cpu3/thermal_throttle/package_throttle_count:0
/sys/devices/system/cpu/cpu3/thermal_throttle/package_throttle_max_time_ms:0
/sys/devices/system/cpu/cpu3/thermal_throttle/package_throttle_total_time_ms:0

```

Here is the output of the msr module:
```

hrf1@hrf1:~$ sudo modprobe msr
hrf1@hrf1:~$ sudo rdmsr -a 0x19a
0
0
0
0

```

The CPU control options in the bios are (in case this is relevant):
```

CPU Configuration
Execute-Disable Bit Capability - Enabled
Intel (R) Hyper-Threading Technology - Enabled
Intel (R) Virtualization Technology - Enabled
Intel (R) VT-d - Enabled
Intel (R) Trusted Execution Technology - Disabled
Intel (R) Turbo Boost Technology 2.0 - Enabled

```

Deactivating the turbo function had no effect on the frequency / temperature.
```
Intel (R) Turbo Boost Technology 2.0 - Disabled
```

Unfortunately, the new Grub Commando line could not calm down the CPU.
```
GRUB_CMDLINE_LINUX_DEFAULT="intel_pstate=passive intel_pstate=no_hwp cpufreq.default_governor=powersave"
```
Nevertheless, I left this setting.

Turbostat delivers the following values:
Idle state:
```

hrf1@hrf1:~$ sudo turbostat --Summary --quiet --show Busy%,Bzy_MHz,IRQ,PkgWatt,PkgTmp,GFXWatt,CorWatt --interval 6
Busy%   Bzy_MHz IRQ     PkgTmp  PkgWatt CorWatt GFXWatt
7.71    600     2989    53      4.63    0.26    0.02
8.49    600     4224    53      4.68    0.28    0.04
7.91    600     3502    52      4.59    0.26    0.02
7.58    600     3127    53      4.66    0.25    0.03
7.74    600     2920    53      4.56    0.26    0.02
7.69    600     2758    53      4.67    0.25    0.03

```

and under heavy load:
```
stress-ng -c 4
```
```

hrf1@hrf1:~$ sudo turbostat --Summary --quiet --show Busy%,Bzy_MHz,IRQ,PkgWatt,PkgTmp,GFXWatt,CorWatt --interval 6
Busy%   Bzy_MHz IRQ     PkgTmp  PkgWatt CorWatt GFXWatt
100.00  600     8974    55      5.82    1.93    0.02
100.00  600     8890    55      5.71    1.94    0.02
100.00  600     9575    55      5.73    1.94    0.02
100.00  600     9592    56      5.72    1.95    0.04
100.00  600     9562    55      5.69    1.94    0.02

```

Next the settings for thermald. The thermal-conf.xml did not exist. So I created a new one:
```
hrf1@hrf1:~$ sudo nano /etc/thermald/thermal-conf.xml
```
and copied the code into it.

Then reboot again.
I also adapted the second code of the XML file. Reboot. Unfortunately without an effect :-(

Maybe we have a similar problem with this PANASONIC device analogue the DELL devices. For some DELL Laptops WINDOWS had set a "quiet" flag in the bios for the thermal control, which causes the throttling of their devices in LINUX.

---

### Post by Doug S on 2022-02-13
Please also provide:

```
grep . /sys/devices/system/cpu/intel_pstate/*
grep . /sys/devices/system/cpu/cpu*/cpufreq/*
```

Example, but for CPU 2 only:

```
doug@s19:~$ [COLOR="#FF0000"]grep . /sys/devices/system/cpu/intel_pstate/*[/COLOR]
//sys/devices/system/cpu/intel_pstate/max_perf_pct:100
/sys/devices/system/cpu/intel_pstate/min_perf_pct:16
/sys/devices/system/cpu/intel_pstate/no_turbo:0
/sys/devices/system/cpu/intel_pstate/num_pstates:41
/sys/devices/system/cpu/intel_pstate/status:[COLOR="#FF0000"]passive[/COLOR]
/sys/devices/system/cpu/intel_pstate/turbo_pct:18
doug@s19:~$
doug@s19:~$ [COLOR="#FF0000"]grep . /sys/devices/system/cpu/cpu2/cpufreq/*[/COLOR]
/sys/devices/system/cpu/cpu2/cpufreq/affected_cpus:2
/sys/devices/system/cpu/cpu2/cpufreq/cpuinfo_max_freq:4800000
/sys/devices/system/cpu/cpu2/cpufreq/cpuinfo_min_freq:800000
/sys/devices/system/cpu/cpu2/cpufreq/cpuinfo_transition_latency:20000
/sys/devices/system/cpu/cpu2/cpufreq/related_cpus:2
/sys/devices/system/cpu/cpu2/cpufreq/scaling_available_governors:conservative ondemand userspace powersave performance schedutil
/sys/devices/system/cpu/cpu2/cpufreq/scaling_cur_freq:[COLOR="#FF0000"]800222[/COLOR]
/sys/devices/system/cpu/cpu2/cpufreq/scaling_driver:[COLOR="#FF0000"]intel_cpufreq[/COLOR]
/sys/devices/system/cpu/cpu2/cpufreq/scaling_governor:[COLOR="#FF0000"]powersave[/COLOR]
/sys/devices/system/cpu/cpu2/cpufreq/scaling_max_freq:4800000
/sys/devices/system/cpu/cpu2/cpufreq/scaling_min_freq:800000
/sys/devices/system/cpu/cpu2/cpufreq/scaling_setspeed:<unsupported>

EDIT: I missed this:

[CODE]cpu3: MSR_PLATFORM_INFO: 0x6063bf3011000
6 * 100.0 = 600.0 MHz max efficiency frequency
```

I have never seen an Intel processor with a default minimum pstate of 6 before. More typically 4 or 8, so I incorrectly thought Clock Modulation was involved.

O.K. So, The boot forcing intel_cpufreq and powersave might be O.K., as it will always force 600 MHz no matter what. The idea was to get you booted without issue, and go from there. So once booted and state confirmed, then leave the system idle and enable actual frequency scaling. We can either use active mode and the powersave governor or stay in passive mode and use any other governor. Let's use intel_cpufreq/ondemand:

```
doug@s19:~$ echo ondemand | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
ondemand
doug@s19:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
``` Now does the CPU frequency scale? Note: Do not use any stress test at this point, as that will likely lockup your system again. Report back and we'll proceed from there by manually limiting the upper frequency and then watching temperature verses load and CPU frequency .

---

### Post by linucyphre on 2022-02-13
Thank you for the response.

The two commands:
```

hrf1@hrf1:~$ grep . /sys/devices/system/cpu/intel_pstate/*
/sys/devices/system/cpu/intel_pstate/max_perf_pct:100
/sys/devices/system/cpu/intel_pstate/min_perf_pct:26
/sys/devices/system/cpu/intel_pstate/no_turbo:0
/sys/devices/system/cpu/intel_pstate/num_pstates:18
/sys/devices/system/cpu/intel_pstate/status:passive
/sys/devices/system/cpu/intel_pstate/turbo_pct:90

```

and:
```

hrf1@hrf1:~$ grep . /sys/devices/system/cpu/cpu*/cpufreq/*
/sys/devices/system/cpu/cpu0/cpufreq/affected_cpus:0
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq:2300000
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_min_freq:600000
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_transition_latency:20000
/sys/devices/system/cpu/cpu0/cpufreq/related_cpus:0
/sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors:conservative ondemand userspace powersave performance schedutil 
/sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq:598723
/sys/devices/system/cpu/cpu0/cpufreq/scaling_driver:intel_cpufreq
/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor:ondemand
/sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq:2300000
/sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq:600000
/sys/devices/system/cpu/cpu0/cpufreq/scaling_setspeed:<unsupported>
/sys/devices/system/cpu/cpu1/cpufreq/affected_cpus:1
/sys/devices/system/cpu/cpu1/cpufreq/cpuinfo_max_freq:2300000
/sys/devices/system/cpu/cpu1/cpufreq/cpuinfo_min_freq:600000
/sys/devices/system/cpu/cpu1/cpufreq/cpuinfo_transition_latency:20000
/sys/devices/system/cpu/cpu1/cpufreq/related_cpus:1
/sys/devices/system/cpu/cpu1/cpufreq/scaling_available_governors:conservative ondemand userspace powersave performance schedutil 
/sys/devices/system/cpu/cpu1/cpufreq/scaling_cur_freq:598723
/sys/devices/system/cpu/cpu1/cpufreq/scaling_driver:intel_cpufreq
/sys/devices/system/cpu/cpu1/cpufreq/scaling_governor:ondemand
/sys/devices/system/cpu/cpu1/cpufreq/scaling_max_freq:2300000
/sys/devices/system/cpu/cpu1/cpufreq/scaling_min_freq:600000
/sys/devices/system/cpu/cpu1/cpufreq/scaling_setspeed:<unsupported>
/sys/devices/system/cpu/cpu2/cpufreq/affected_cpus:2
/sys/devices/system/cpu/cpu2/cpufreq/cpuinfo_max_freq:2300000
/sys/devices/system/cpu/cpu2/cpufreq/cpuinfo_min_freq:600000
/sys/devices/system/cpu/cpu2/cpufreq/cpuinfo_transition_latency:20000
/sys/devices/system/cpu/cpu2/cpufreq/related_cpus:2
/sys/devices/system/cpu/cpu2/cpufreq/scaling_available_governors:conservative ondemand userspace powersave performance schedutil 
/sys/devices/system/cpu/cpu2/cpufreq/scaling_cur_freq:598733
/sys/devices/system/cpu/cpu2/cpufreq/scaling_driver:intel_cpufreq
/sys/devices/system/cpu/cpu2/cpufreq/scaling_governor:ondemand
/sys/devices/system/cpu/cpu2/cpufreq/scaling_max_freq:2300000
/sys/devices/system/cpu/cpu2/cpufreq/scaling_min_freq:600000
/sys/devices/system/cpu/cpu2/cpufreq/scaling_setspeed:<unsupported>
/sys/devices/system/cpu/cpu3/cpufreq/affected_cpus:3
/sys/devices/system/cpu/cpu3/cpufreq/cpuinfo_max_freq:2300000
/sys/devices/system/cpu/cpu3/cpufreq/cpuinfo_min_freq:600000
/sys/devices/system/cpu/cpu3/cpufreq/cpuinfo_transition_latency:20000
/sys/devices/system/cpu/cpu3/cpufreq/related_cpus:3
/sys/devices/system/cpu/cpu3/cpufreq/scaling_available_governors:conservative ondemand userspace powersave performance schedutil 
/sys/devices/system/cpu/cpu3/cpufreq/scaling_cur_freq:598731
/sys/devices/system/cpu/cpu3/cpufreq/scaling_driver:intel_cpufreq
/sys/devices/system/cpu/cpu3/cpufreq/scaling_governor:ondemand
/sys/devices/system/cpu/cpu3/cpufreq/scaling_max_freq:2300000
/sys/devices/system/cpu/cpu3/cpufreq/scaling_min_freq:600000
/sys/devices/system/cpu/cpu3/cpufreq/scaling_setspeed:<unsupported>


```

hope this helps.

---

### Post by Doug S on 2022-02-13
O.K. great. See edits I kept making to my earlier post, as I did not see your quick reply. Did you try to force powersave on boot? Becuase I see ondemand in your output.

```
/sys/devices/system/cpu/cpu3/cpufreq/scaling_governor:[COLOR="#FF0000"]ondemand[/COLOR]
```

If yes, then it might be that stupid ondemand service (not to be confused with the ondemand governor) that Ubuntu uses. Disable it, for now:

```
doug@s19:~$ sudo systemctl status ondemand
&#9679; ondemand.service - Set the CPU Frequency Scaling governor
     Loaded: loaded (/lib/systemd/system/ondemand.service; disabled; vendor preset: enabled)
     Active: inactive (dead)
```

---

### Post by linucyphre on 2022-02-13
... thank you for your time.

```

[FONT=monospace][COLOR=#54ff54]**hrf1@hrf1**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ echo ondemand | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor [/COLOR]
ondemand[/FONT]

```

and
```

[FONT=monospace][COLOR=#54ff54]**hrf1@hrf1**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor [/COLOR]
ondemand 
ondemand 
ondemand 
ondemand
[/FONT]
```

Turbostat

```

[FONT=monospace][COLOR=#000000]Busy%   Bzy_MHz IRQ     PkgTmp  PkgWatt CorWatt GFXWatt [/COLOR]
28.11   600     11357   53      5.58    0.80    0.46 
21.46   600     10086   53      5.29    0.66    0.32 
18.09   600     9211    53      5.11    0.57    0.25 
18.61   600     9460    53      5.21    0.58    0.28 
18.58   600     9469    53      5.13    0.58    0.25
[/FONT]
```

```

[FONT=monospace][COLOR=#54ff54]**hrf1@hrf1**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_driver [/COLOR]
intel_cpufreq
[/FONT]
```

---

### Post by linucyphre on 2022-02-13
Yes, the actual boot-parameter is "quiet splash", so the intel_pstate mode is set to passive.

```

[FONT=monospace][COLOR=#54ff54]**hrf1@hrf1**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo systemctl status ondemand [/COLOR]
&#9679; ondemand.service - Set the CPU Frequency Scaling governor 
     Loaded: loaded (/lib/systemd/system/ondemand.service; enabled; vendor preset: enabled) 
     Active: inactive (dead) since Sun 2022-02-13 16:36:31 CET; 12min ago 
    Process: 1090 ExecStart=/lib/systemd/set-cpufreq (code=exited, status=0/SUCCESS) 
   Main PID: 1090 (code=exited, status=0/SUCCESS) 

Feb 13 16:36:26 hrf1 systemd[1]: Started Set the CPU Frequency Scaling governor. 
Feb 13 16:36:30 hrf1 set-cpufreq[1090]: Setting ondemand scheduler for all CPUs 
Feb 13 16:36:31 hrf1 systemd[1]: ondemand.service: Succeeded.
[/FONT]
```

---

### Post by Doug S on 2022-02-13
I suspect your processor does not have MSR 0X64F, but try it:

```
doug@s19:~$ sudo rdmsr 0x64f
0
```

And disable the service:

```
sudo systemctl disable ondemand
``` and re-boot.

We are attempting to get you booted without getting into a locked up state. Then we can proceed from there.

EDIT: By the way, such a difference between package power and core power is unusual, in my experience.

```
Busy%   Bzy_MHz IRQ     PkgTmp  PkgWatt CorWatt GFXWatt 
28.11   600     11357   53      [COLOR="#FF0000"]5.58    0.80[/COLOR]    0.46
```

More like about a 1/2 watt is more typical:

```
Busy%   Bzy_MHz IRQ     PkgTmp  PkgWatt CorWatt GFXWatt RAMWatt
2.49    3164    200428  35      4.03    3.37    0.00    0.89
```

---

### Post by linucyphre on 2022-02-13
```

[FONT=monospace][COLOR=#54ff54]**hrf1@hrf1**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo rdmsr 0x64f [/COLOR]
rdmsr: CPU 0 cannot read MSR 0x0000064f
[/FONT]
```

```
[FONT=monospace][COLOR=#54ff54][B]
hrf1@hrf1[/B][/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo systemctl disable ondemand [/COLOR]
Removed /etc/systemd/system/multi-user.target.wants/ondemand.service.
[/FONT]
```

---

### Post by linucyphre on 2022-02-13
I had already thought about a fault in the cooling or heat dissipation. But under WINDOWS-10 everything runs fine (up to 2.300MHz).

---

### Post by Doug S on 2022-02-13
I don't know about windows.

So, does your system now boot into intel_cpufreq / powersave?
And, after boot and after things have settled down a little (say a minute or 2) if you then switch to the ondemand governor, does the frequency scale properly? Note: Do NOT use stress test at this step, just watch the idle system with turbostat. Actually have turbostat running with a sample interval of 1 second during the governor change, watch for anomalies.

---

### Post by linucyphre on 2022-02-13
Yes, the actual driver is intel_cpufreq. Pstate is still in passive mode. If i want to use the active mode, i have to add intel_pstate=active to the boot parameter, i think.

After waiting several minutes and activating ondemand
```
[FONT=monospace][COLOR=#000000]echo ondemand | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor[/COLOR][/FONT][FONT=monospace]
ondemand[/FONT]
```
i have still the same result:
```

Busy%   Bzy_MHz IRQ     PkgTmp  PkgWatt CorWatt GFXWatt
7.60    600     2818    45      4.39    0.25    0.01

```

---

### Post by linucyphre on 2022-02-13
... i'll make another test with the new GRUB setting.

---> still the same :-( Changing the governor doesn't change anything in turbostat.

The temperature is going to 46 degrees, but the frequency is always stuck at 600 MHz.

It is possible to change some parameters, but the system has its own regime. I can see it on cpupower, when the frequency range is outside the actual frequency.
I can switch the frequencies with cpupower-gui, but the system still ignores them:

```
  current policy: frequency should be within 1.09 GHz and 2.30 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 599 MHz.
```

---

### Post by Doug S on 2022-02-13
> **linucyphre said:**
> If i want to use the active mode, i have to add intel_pstate=active to the boot parameter, i think. No, you can change it on the fly. Just write "active" to /sys/devices/system/cpu/intel_pstate/status.

Example, from memory, my test computer can not be disturbed at the moment:

```
echo active | sudo tee /sys/devices/system/cpu/intel_pstate/status

```

You mentioned "cpupower-gui". Don't use any of that stuff and make sure no related daemons are running. If the intel_powerclamp module is running get rid of it. We only want to use primitive commands for now.
If indeed you are still stuck after boot to intel_cpufreq and powersave, then changing to ondemand, then I think you have hardware issues.

---

### Post by linucyphre on 2022-02-13
so, there is no solution? 
I am no friend of windows, definitely. Won't switch to it.

---

### Post by Doug S on 2022-02-13
This:

```
cpu0: MSR_IA32_PACKAGE_THERM_STATUS: 0x882a0c00 (58 C)
```

decodes to:

```
Package Power Limitation Status (bit 10, RO) — Indicates package power limit is forcing one ore more
processors to operate below OS-requested P-state. Note that package power limit violation may be caused by
processor cores or by devices residing in the uncore. Software can examine IA32_THERM_STATUS to determine
if the cause originates from a processor core.
```

So, it thinks it has to throttle due to power consumption, which is not true.
We need to look at the IA32_THERM_STATUS registers for all CPUs. Example:

```
doug@s19:~$ sudo rdmsr -a 0X019C
88430000
88460000
88430000
88420000
88440000
88440000
88430000
88460000
88430000
88420000
88440000
88440000
```

---

### Post by linucyphre on 2022-02-13
```

[FONT=monospace][COLOR=#54ff54]**rf1@hrf1**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo rdmsr -a 0X019C [/COLOR]
88430800 
88430800 
88430800 
88430800 
[/FONT]
```

---

### Post by Doug S on 2022-02-13
O.K. so it is not any user core causing the power throttling, leaving only uncore or other devices (not user accessible, as far as I know). I do not know how to go further. I did look at a few web pages about how to install linux on your tablet model, and some references specify grub command line entries to turn off some things.
You could try resetting the log bits, but I doubt it'll help. I have a program to reset the bits, so I forget actual details, but it does this:

```
sudo wrmsr 0x19c 0
sudo wrmsr 0x1b1 0 [COLOR="#FF0000"]<<< You might not have this register, check first with a read.[/COLOR]
sudo wrmsr 0x64f 0  [COLOR="#FF0000"]<<< You do not have this register[/COLOR]

```You might find you do not have write ability, if your kernel is new enough. I enable write via grub but there is a terminal command line way to enable it, I'll have to find it though as I forget what is is.

EDIT: You could look around the below area for anything odd (example only, just look around):

```
doug@s19:~/c$ [COLOR="#FF0000"]grep . /sys/class/powercap/intel-rapl/intel-rapl:0/*[/COLOR]
/sys/class/powercap/intel-rapl/intel-rapl:0/constraint_0_max_power_uw:125000000
/sys/class/powercap/intel-rapl/intel-rapl:0/constraint_0_name:long_term
/sys/class/powercap/intel-rapl/intel-rapl:0/constraint_0_power_limit_uw:125000000
/sys/class/powercap/intel-rapl/intel-rapl:0/constraint_0_time_window_us:7995392
/sys/class/powercap/intel-rapl/intel-rapl:0/constraint_1_max_power_uw:0
/sys/class/powercap/intel-rapl/intel-rapl:0/constraint_1_name:short_term
/sys/class/powercap/intel-rapl/intel-rapl:0/constraint_1_power_limit_uw:136000000
/sys/class/powercap/intel-rapl/intel-rapl:0/constraint_1_time_window_us:2440
grep: /sys/class/powercap/intel-rapl/intel-rapl:0/device: Is a directory
/sys/class/powercap/intel-rapl/intel-rapl:0/enabled:1
grep: /sys/class/powercap/intel-rapl/intel-rapl:0/energy_uj: Permission denied
grep: /sys/class/powercap/intel-rapl/intel-rapl:0/intel-rapl:0:0: Is a directory
grep: /sys/class/powercap/intel-rapl/intel-rapl:0/intel-rapl:0:1: Is a directory
grep: /sys/class/powercap/intel-rapl/intel-rapl:0/intel-rapl:0:2: Is a directory
/sys/class/powercap/intel-rapl/intel-rapl:0/max_energy_range_uj:262143328850
/sys/class/powercap/intel-rapl/intel-rapl:0/name:package-0
grep: /sys/class/powercap/intel-rapl/intel-rapl:0/power: Is a directory
grep: /sys/class/powercap/intel-rapl/intel-rapl:0/subsystem: Is a directory
```

---

### Post by linucyphre on 2022-02-14
Great, a new round. Here's the output:

```

[FONT=monospace][COLOR=#54ff54]**hrf1@hrf1**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo rdmsr 0x19c   [/COLOR]
88350800 
[COLOR=#54ff54]**hrf1@hrf1**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo rdmsr 0x1b1 [/COLOR]
88340c00 
[COLOR=#54ff54]**hrf1@hrf1**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo rdmsr 0x64f [/COLOR]
rdmsr: CPU 0 cannot read MSR 0x0000064f 
[COLOR=#54ff54]**hrf1@hrf1**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo wrmsr 0x19c 0 [/COLOR]
[COLOR=#54ff54]**hrf1@hrf1**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo wrmsr 0x1b1 0
[/COLOR][/FONT]
```[FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#000000][FONT=monospace]
[/FONT][/COLOR][/FONT]and
[/COLOR][/FONT]```
[FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#54ff54]**hrf1@hrf1**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ grep . /sys/class/powercap/intel-rapl/intel-rapl:0/* [/COLOR]
[COLOR=#b218b2]/sys/class/powercap/intel-rapl/intel-rapl:0/constraint_0_max_power_uw[/COLOR][COLOR=#18b2b2]:[/COLOR][COLOR=#ff5454]**11500000**[/COLOR]
[COLOR=#b218b2]/sys/class/powercap/intel-rapl/intel-rapl:0/constraint_0_name[/COLOR][COLOR=#18b2b2]:[/COLOR][COLOR=#ff5454]**long_term**[/COLOR]
[COLOR=#b218b2]/sys/class/powercap/intel-rapl/intel-rapl:0/constraint_0_power_limit_uw[/COLOR][COLOR=#18b2b2]:[/COLOR][COLOR=#ff5454]**11500000**[/COLOR]
[COLOR=#b218b2]/sys/class/powercap/intel-rapl/intel-rapl:0/constraint_0_time_window_us[/COLOR][COLOR=#18b2b2]:[/COLOR][COLOR=#ff5454]**27983872**[/COLOR]
[COLOR=#b218b2]/sys/class/powercap/intel-rapl/intel-rapl:0/constraint_1_max_power_uw[/COLOR][COLOR=#18b2b2]:[/COLOR][COLOR=#ff5454]**0**[/COLOR]
[COLOR=#b218b2]/sys/class/powercap/intel-rapl/intel-rapl:0/constraint_1_name[/COLOR][COLOR=#18b2b2]:[/COLOR][COLOR=#ff5454]**short_term**[/COLOR]
[COLOR=#b218b2]/sys/class/powercap/intel-rapl/intel-rapl:0/constraint_1_power_limit_uw[/COLOR][COLOR=#18b2b2]:[/COLOR][COLOR=#ff5454]**25000000**[/COLOR]
[COLOR=#b218b2]/sys/class/powercap/intel-rapl/intel-rapl:0/constraint_1_time_window_us[/COLOR][COLOR=#18b2b2]:[/COLOR][COLOR=#ff5454]**2440**[/COLOR]
grep: /sys/class/powercap/intel-rapl/intel-rapl:0/device: Ist ein Verzeichnis 
[COLOR=#b218b2]/sys/class/powercap/intel-rapl/intel-rapl:0/enabled[/COLOR][COLOR=#18b2b2]:[/COLOR][COLOR=#ff5454]**0**[/COLOR]
grep: /sys/class/powercap/intel-rapl/intel-rapl:0/energy_uj: Keine Berechtigung 
grep: /sys/class/powercap/intel-rapl/intel-rapl:0/intel-rapl:0:0: Ist ein Verzeichnis 
grep: /sys/class/powercap/intel-rapl/intel-rapl:0/intel-rapl:0:1: Ist ein Verzeichnis 
grep: /sys/class/powercap/intel-rapl/intel-rapl:0/intel-rapl:0:2: Ist ein Verzeichnis 
[COLOR=#b218b2]/sys/class/powercap/intel-rapl/intel-rapl:0/max_energy_range_uj[/COLOR][COLOR=#18b2b2]:[/COLOR][COLOR=#ff5454]**262143328850**[/COLOR]
[COLOR=#b218b2]/sys/class/powercap/intel-rapl/intel-rapl:0/name[/COLOR][COLOR=#18b2b2]:[/COLOR][COLOR=#ff5454]**package-0**[/COLOR]
grep: /sys/class/powercap/intel-rapl/intel-rapl:0/power: Ist ein Verzeichnis 
grep: /sys/class/powercap/intel-rapl/intel-rapl:0/subsystem: Ist ein Verzeichnis
[/FONT][/COLOR][/FONT]
```[FONT=monospace][COLOR=#000000][FONT=monospace]
[/FONT][/COLOR]
Turbostat with no changes / anomalies. The higher busy rate is from the browser.

```
[FONT=monospace]
Busy%   Bzy_MHz IRQ     PkgTmp  PkgWatt CorWatt GFXWatt 
27.95   600     10245   54      5.56    0.85    0.48 
25.95   600     9778    54      5.51    0.81    0.45 
28.73   600     9839    54      5.55    0.88    0.42[/FONT][FONT=monospace][COLOR=#000000][FONT=monospace]
[/FONT][/COLOR][/FONT]
```[FONT=monospace][COLOR=#000000][FONT=monospace][FONT=monospace][COLOR=#000000][FONT=monospace]
[/FONT][/COLOR][/FONT][/FONT][/COLOR][/FONT]
and

[FONT=monospace]```
[/FONT]
[FONT=monospace][COLOR=#54ff54]**rf1@hrf1**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ dmesg | grep locked [/COLOR]
[    0.237462] ACPI: EC: interrupt b[COLOR=#ff5454]**locked**[/COLOR][COLOR=#000000] [/COLOR]
[    0.380104] ACPI: EC: interrupt unb[COLOR=#ff5454]**locked**[/COLOR][COLOR=#000000] [/COLOR]
[    0.380117] ACPI: EC: event unb[COLOR=#ff5454]**locked**[/COLOR][COLOR=#000000] [/COLOR]
[   11.835940] intel_rapl_common: RAPL package-0 domain package [COLOR=#ff5454]**locked**[/COLOR][COLOR=#000000] by BIOS [/COLOR]
[   11.835968] intel_rapl_common: RAPL package-0 domain dram [COLOR=#ff5454]**locked**[/COLOR][COLOR=#000000] by BIOS[/COLOR]
[FONT=monospace]
```[/FONT]

[/FONT]

[/FONT]

---

### Post by Doug S on 2022-02-14
After you try to clear the log bit in register 0x1B1, read it again and what do you get?

Do both commands as below:

```
doug@s19:~$ sudo rdmsr 0x1b1
88410000
doug@s19:~$ sudo rdmsr --bitfield 10:10 -u 0x1B1
[COLOR="#FF0000"]0   <<< This bit needs to be 0, or your processor will be throttled. [/COLOR]
```

---

### Post by linucyphre on 2022-02-14
so,
```

[FONT=monospace][COLOR=#54ff54]**hrf1@hrf1**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo rdmsr 0x1b1  [/COLOR]
882d0c00 
[COLOR=#54ff54]**hrf1@hrf1**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo rdmsr --bitfield 10:10 -u 0x1B1 [/COLOR]
1 
[COLOR=#54ff54]**hrf1@hrf1**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ [/COLOR]
[/FONT]
```

and i think it&#8217;s your script from an older post
```

[FONT=monospace][COLOR=#54ff54]**hrf1@hrf1**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~/Downloads**[/COLOR][COLOR=#000000]$ sudo ./msr-decoder  [/COLOR]
How many CPUs?: 4 
8.) 0x198: IA32_PERF_STATUS     : CPU 0-3 :   6 :   6 :   6 :   6 :  
rdmsr: CPU 0 cannot read MSR 0x00000770 
B.) 0x770: IA32_PM_ENABLE: Command B not found or exited with error status 
9.) 0x199: IA32_PERF_CTL        : CPU 0-3 :   6 :   6 :   6 :   6 :  
C.) 0x1B0: IA32_ENERGY_PERF_BIAS: CPU 0-3 :   4 :   4 :   4 :   4 :  
1.) 0x19C: IA32_THERM_STATUS: 882C0800 PWL  
2.) 0x1AA: MSR_MISC_PWR_MGMT: 400000 EIST enabled Coordination enabled OOB Bit 8 reset OOB Bit 18 reset  
3.) 0x1B1: IA32_PACKAGE_THERM_STATUS: 882D0C00 PW PWL  
rdmsr: CPU 0 cannot read MSR 0x0000064f 
4.) 0x64F: MSR_CORE_PERF_LIMIT_REASONS: Command 4 not found or exited with error status 
A.) 0x1FC: MSR_POWER_CTL: 4005D : C1E disable : EEO enable : RHO enable
[/FONT]
```

---

### Post by Doug S on 2022-02-14
> **linucyphre said:**
> 
and this from an older post
```

[FONT=monospace][COLOR=#54ff54]**hrf1@hrf1**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~/Downloads**[/COLOR][COLOR=#000000]$ sudo ./msr-decoder  [/COLOR]
How many CPUs?: 4 
...  
1.) 0x19C: IA32_THERM_STATUS: 882C0800 [COLOR="#0000CD"]PWL[/COLOR]
2.) 0x1AA: MSR_MISC_PWR_MGMT: 400000 EIST enabled Coordination enabled OOB Bit 8 reset OOB Bit 18 reset  
3.) 0x1B1: IA32_PACKAGE_THERM_STATUS: 882D0C00 [COLOR="#FF0000"]PW[/COLOR] [COLOR="#0000CD"]PWL[/COLOR]  [COLOR="#FF0000"]<<< "Power limit bit set = bad"[/COLOR]
...
[/FONT]
```O.K. so using my msr decoder method is great. At this point I do not know how to get that bit to be 0.

Note: I know extremely little about this next stuff: What to you get for:

```
doug@s19:~$ sudo rdmsr 0x620
82b
```

---

### Post by linucyphre on 2022-02-14
i get
```

hrf1@hrf1:~$ sudo rdmsr 0x620
717

```

found this script and executed it. Does it help?
```

[FONT=monospace][COLOR=#54ff54]**[FONT=monospace][COLOR=#54ff54][B]h**[/COLOR][/FONT]rf1@hrf1[/B][/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~/Downloads**[/COLOR][COLOR=#000000]$ sudo ./msr_output.sh  [/COLOR]
[sudo] Passwort für hrf1:  
MSR Dump, Script Version 1.0 

$ eval date 
Mo 14. Feb 17:56:50 CET 2022 
$ eval cat /proc/cpuinfo | grep "MHz" 
cpu MHz         : 598.613 
cpu MHz         : 598.614 
cpu MHz         : 598.614 
cpu MHz         : 598.617 
$ eval lsb_release -a 
No LSB modules are available. 
Distributor ID: Ubuntu 
Description:    Ubuntu 20.04.3 LTS 
Release:        20.04 
Codename:       focal 
$ eval dmesg | grep 'MHz processor' 
[    0.000000] tsc: Detected 1596.303 MHz processor 
$ eval cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor 
powersave 
powersave 
powersave 
powersave 


+----+------------------------------+---------+----------+----------+----------+----------+ 
|  # | MSR Register                 | Address |   Core 0 |   Core 1 |   Core 2 |   Core 3 | 
+----+------------------------------+---------+----------+----------+----------+----------+ 
|  0 | IA32_PERF_CTL                |   0x199 |      600 |      600 |      600 |      600 | 
|  1 | IA32_CLOCK_MODULATION        |   0x19A |        0 |        0 |        0 |        0 | 
|  2 | IA32_THERM_INTERRUPT         |   0x19B |       13 |       13 |       13 |       13 | 
|  3 | IA32_HWP_THERM_STATUS        |   0x19C | 882a0800 | 882b0800 | 882a0800 | 882a0800 | 
|  4 | IA32_MISC_ENABLE             |   0x1A0 |   850089 |   850089 |   850089 |   850089 | 
|  5 | IA32_PACKAGE_THERM_MARGIN    |   0x1A1 |     29ee |     29ee |     29ec |     29ea | 
|  6 | IA32_TEMPERATURE_TARGET      |   0x1A2 |   640000 |   640000 |   640000 |   640000 | 
|  7 | IA32_PKG_THERM_STATUS        |   0x1B1 | 882a0c00 | 882a0c00 | 882a0c00 | 882a0c00 | 
|  8 | MSR_PKG_ENERGY_STATUS        |   0x611 |  7edfad3 |  7ee1170 |  7ee22fc |  7ee3304 | 
|  9 | MSR_PKG_STATUS               |   0x613 |     44f5 |     44f5 |     44f5 |     44f5 | 
| 10 | MSR_PPERF                    |   0x64E |      N/A |      N/A |      N/A |      N/A | 
| 11 | MSR_CORE_PERF_LIMIT_REASONS  |   0x690 | 1e000000 | 1e000000 | 1e000000 | 1e000000 | 
| 12 | IA32_PM_ENABLE               |   0x770 |      N/A |      N/A |      N/A |      N/A | 
| 13 | IA32_HWP_CAPABILITIES        |   0x771 |      N/A |      N/A |      N/A |      N/A | 
| 14 | IA32_HWP_REQUEST_PKG         |   0x772 |      N/A |      N/A |      N/A |      N/A | 
| 15 | IA32_HWP_INTERRUPT           |   0x773 |      N/A |      N/A |      N/A |      N/A | 
| 16 | IA32_HWP_REQUEST             |   0x774 |      N/A |      N/A |      N/A |      N/A | 
| 17 | IA32_HWP_PECI_REQUEST_INFO   |   0x775 |      N/A |      N/A |      N/A |      N/A | 
| 18 | IA32_HWP_STATUS              |   0x777 |      N/A |      N/A |      N/A |      N/A | 
+----+------------------------------+---------+----------+----------+----------+----------+ 
Generated table by executing commands: 
  [ 0] sudo rdmsr -p 0 0x199 -f 63:0 2>&1 
  [ 0] sudo rdmsr -p 1 0x199 -f 63:0 2>&1 
  [ 0] sudo rdmsr -p 2 0x199 -f 63:0 2>&1 
  [ 0] sudo rdmsr -p 3 0x199 -f 63:0 2>&1 
  [ 1] sudo rdmsr -p 0 0x19A -f 63:0 2>&1 
  [ 1] sudo rdmsr -p 1 0x19A -f 63:0 2>&1 
  [ 1] sudo rdmsr -p 2 0x19A -f 63:0 2>&1 
  [ 1] sudo rdmsr -p 3 0x19A -f 63:0 2>&1 
  [ 2] sudo rdmsr -p 0 0x19B -f 63:0 2>&1 
  [ 2] sudo rdmsr -p 1 0x19B -f 63:0 2>&1 
  [ 2] sudo rdmsr -p 2 0x19B -f 63:0 2>&1 
  [ 2] sudo rdmsr -p 3 0x19B -f 63:0 2>&1 
  [ 3] sudo rdmsr -p 0 0x19C -f 63:0 2>&1 
  [ 3] sudo rdmsr -p 1 0x19C -f 63:0 2>&1 
  [ 3] sudo rdmsr -p 2 0x19C -f 63:0 2>&1 
  [ 3] sudo rdmsr -p 3 0x19C -f 63:0 2>&1 
  [ 4] sudo rdmsr -p 0 0x1A0 -f 63:0 2>&1 
  [ 4] sudo rdmsr -p 1 0x1A0 -f 63:0 2>&1 
  [ 4] sudo rdmsr -p 2 0x1A0 -f 63:0 2>&1 
  [ 4] sudo rdmsr -p 3 0x1A0 -f 63:0 2>&1 
  [ 5] sudo rdmsr -p 0 0x1A1 -f 63:0 2>&1 
  [ 5] sudo rdmsr -p 1 0x1A1 -f 63:0 2>&1 
  [ 5] sudo rdmsr -p 2 0x1A1 -f 63:0 2>&1 
  [ 5] sudo rdmsr -p 3 0x1A1 -f 63:0 2>&1 
  [ 6] sudo rdmsr -p 0 0x1A2 -f 63:0 2>&1 
  [ 6] sudo rdmsr -p 1 0x1A2 -f 63:0 2>&1 
  [ 6] sudo rdmsr -p 2 0x1A2 -f 63:0 2>&1 
  [ 6] sudo rdmsr -p 3 0x1A2 -f 63:0 2>&1 
  [ 7] sudo rdmsr -p 0 0x1B1 -f 63:0 2>&1 
  [ 7] sudo rdmsr -p 1 0x1B1 -f 63:0 2>&1 
  [ 7] sudo rdmsr -p 2 0x1B1 -f 63:0 2>&1 
  [ 7] sudo rdmsr -p 3 0x1B1 -f 63:0 2>&1 
  [ 8] sudo rdmsr -p 0 0x611 -f 63:0 2>&1 
  [ 8] sudo rdmsr -p 1 0x611 -f 63:0 2>&1 
  [ 8] sudo rdmsr -p 2 0x611 -f 63:0 2>&1 
  [ 8] sudo rdmsr -p 3 0x611 -f 63:0 2>&1 
  [ 9] sudo rdmsr -p 0 0x613 -f 63:0 2>&1 
  [ 9] sudo rdmsr -p 1 0x613 -f 63:0 2>&1 
  [ 9] sudo rdmsr -p 2 0x613 -f 63:0 2>&1 
  [ 9] sudo rdmsr -p 3 0x613 -f 63:0 2>&1 
  [10] sudo rdmsr -p 0 0x64E -f 63:0 2>&1 
  [10] sudo rdmsr -p 1 0x64E -f 63:0 2>&1 
  [10] sudo rdmsr -p 2 0x64E -f 63:0 2>&1 
  [10] sudo rdmsr -p 3 0x64E -f 63:0 2>&1 
  [11] sudo rdmsr -p 0 0x690 -f 63:0 2>&1 
  [11] sudo rdmsr -p 1 0x690 -f 63:0 2>&1 
  [11] sudo rdmsr -p 2 0x690 -f 63:0 2>&1 
  [11] sudo rdmsr -p 3 0x690 -f 63:0 2>&1 
  [12] sudo rdmsr -p 0 0x770 -f 63:0 2>&1 
  [12] sudo rdmsr -p 1 0x770 -f 63:0 2>&1 
  [12] sudo rdmsr -p 2 0x770 -f 63:0 2>&1 
  [12] sudo rdmsr -p 3 0x770 -f 63:0 2>&1 
  [13] sudo rdmsr -p 0 0x771 -f 63:0 2>&1 
  [13] sudo rdmsr -p 1 0x771 -f 63:0 2>&1 
  [13] sudo rdmsr -p 2 0x771 -f 63:0 2>&1 
  [13] sudo rdmsr -p 3 0x771 -f 63:0 2>&1 
  [14] sudo rdmsr -p 0 0x772 -f 63:0 2>&1 
  [14] sudo rdmsr -p 1 0x772 -f 63:0 2>&1 
  [14] sudo rdmsr -p 2 0x772 -f 63:0 2>&1 
  [14] sudo rdmsr -p 3 0x772 -f 63:0 2>&1 
  [15] sudo rdmsr -p 0 0x773 -f 63:0 2>&1 
  [15] sudo rdmsr -p 1 0x773 -f 63:0 2>&1 
  [15] sudo rdmsr -p 2 0x773 -f 63:0 2>&1 
  [15] sudo rdmsr -p 3 0x773 -f 63:0 2>&1 
  [16] sudo rdmsr -p 0 0x774 -f 63:0 2>&1 
  [16] sudo rdmsr -p 1 0x774 -f 63:0 2>&1 
  [16] sudo rdmsr -p 2 0x774 -f 63:0 2>&1 
  [16] sudo rdmsr -p 3 0x774 -f 63:0 2>&1 
  [17] sudo rdmsr -p 0 0x775 -f 63:0 2>&1 
  [17] sudo rdmsr -p 1 0x775 -f 63:0 2>&1 
  [17] sudo rdmsr -p 2 0x775 -f 63:0 2>&1 
  [17] sudo rdmsr -p 3 0x775 -f 63:0 2>&1 
  [18] sudo rdmsr -p 0 0x777 -f 63:0 2>&1 
  [18] sudo rdmsr -p 1 0x777 -f 63:0 2>&1 
  [18] sudo rdmsr -p 2 0x777 -f 63:0 2>&1 
  [18] sudo rdmsr -p 3 0x777 -f 63:0 2>&1


```



[/FONT]

---

### Post by Doug S on 2022-02-14
> **linucyphre said:**
> i get
```

hrf1@hrf1:~$ sudo rdmsr 0x620
717

```

Ok, thanks. I did not expect that, I expected 0X06ZZ. You could try writing 0X0707 to that register, which should limit the uncore to 700 MHz. Again, I doubt it'll help.

> **linucyphre said:**
> 
found this script and executed it. Does it help?
I decoded some of those registers and gained no new information.

You were using the powersave governor. Was that in active mode (intel_pstate driver) or passive (intel_cpufreq). If the latter, then the CPU frequency would be limited to 600 MHz anyhow. I observe only pstate 6  (600 MHz) is being requested.

---

### Post by linucyphre on 2022-02-15
I changed the driver to "active", set the governor to "performance" and wrote the register:
```

[FONT=monospace][COLOR=#54ff54]**hrf1@hrf1**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ echo active | sudo tee /sys/devices/system/cpu/intel_pstate/status [/COLOR]
active 
[COLOR=#54ff54]**hrf1@hrf1**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo cpupower frequency-set --governor performance [/COLOR]
Setting cpu: 0 
Setting cpu: 1 
Setting cpu: 2 
Setting cpu: 3 
[COLOR=#54ff54]**hrf1@hrf1**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo wrmsr 0x620 0X0707
[/COLOR][/FONT]
```[FONT=monospace][COLOR=#000000]
[/COLOR]... without any changes in the frequency behavior. :-(

UPDATE!

[/FONT]When I measure CPU frequency this way, I get full scaling:[FONT=monospace]```
[FONT=monospace][COLOR=#000000]
[/COLOR][/FONT][FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#54ff54]**hrf1@hrf1**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ watch -n 3 "grep 'cpu MHz' /proc/cpuinfo" [/COLOR][/FONT]
Alle 3,0s: grep 'cpu MHz' /proc/cpuinfo                              hrf1: Wed Feb 16 09:25:32 2022 [/COLOR]

cpu MHz         : 1596.581 
cpu MHz         : 1596.581 
cpu MHz         : 598.769 
cpu MHz         : 1596.581
[/FONT]
```[FONT=monospace][FONT=monospace][COLOR=#000000]
[/COLOR][/FONT]As soon as the CPU load increases slightly, for example when Turbostat or Firefox is started, the frequency is throttled again. If I close those programs, the scaling is fine again.

Another hint:
[/FONT][/FONT]Installing Fedora with the Gnu Stress app showed amazing values. The maximum  temperature, set for the processors, is actually given as 57 degrees.[FONT=monospace][FONT=monospace]

Bios is locked for any changes. Lower kernel didn&#8217;t solve it. Linux can&#8216;t access or change the BIOS settings. So i&#8216;ll try to overwrite BIOS settings by reinstall WINDOWS and preventing from making updates.
[/FONT]

[/FONT]

---

### Post by linucyphre on 2022-02-19
Next UPDATE:
After a complete reinstallation of WINDOWS and KUBUNTU, Linux runs at maximum frequency - but only if there is no load on the processor. 

As soon as some load is added, it is immediately throttled back to 600 MHz. 

Surprisingly, this effect also occurred with a new WINDOWS installation. Before I installed the thermal management package, the processor frequency was constant throttled at 600 MHz. 

Therefore - from my opinion - the fault is clearly with an incompatible thermal management of Linux and the lack of taking control to BIOS settings.
This is absolutely disappointing, as I need a little processing power for signal processing software in Linux.

---

### Post by Doug S on 2022-02-19
> **linucyphre said:**
> Therefore - from my opinion - the fault is clearly with an incompatible thermal management of Linux and the lack of taking control to BIOS settings.
This is absolutely disappointing, as I need a little processing power for signal processing software in Linux.Disagree. You have not set it up correctly for thermal management. I do not believe the light load of turbostat would cause throttling. Firefox, yes.

---

### Post by linucyphre on 2022-02-23
Yes you are right. With a repeated minimal installation, browser and turbostat do not affect the CPU frequency.


The following behavior is now evident:
A frequency of 600 MHz is displayed after a restart. After about 20 seconds, the frequency seems to oscillate randomly between 600 MHz and 2300 MHz.


If I start a 4K video, it is played smoothly for about 3 seconds. Then it jerks again and the frequency drops to 600 MHz. If I stop the video, the frequency randomly rises above 600 MHz up to 2300 MHz again.

The temperature never reaches more than 57 degrees Celsius.

---

### Post by Doug S on 2022-02-23
O.K., at least now your computer is functioning well enough to make progress investigating.

I would suggest, limiting the maximum CPU frequency manually. Start with a ridiculously low frequency and gradually raise it while under load. Observe with turbostat and try to determine what is causing the eventual throttling. Use primitive commands. (I'll have to come back later with examples, my test computer can not be disturbed right now)

You could also try running turbostat with a very fast sampling rate, say 0.1 seconds. With a step function load, processor package temperatures can change extremely fast, so fast the turbostat might not see it at lower sampling rates. [I have measured 800 degrees per second]("https://askubuntu.com/questions/1373633/how-to-troubleshoot-cpu-hw-crash-in-ubuntu-18-04/1373784#1373784").

---

### Post by uninvolved on 2022-02-23
Could a malfunctioning PSU/inadequate power cause this?

---

### Post by linucyphre on 2022-02-24
Many thanks for the support.

First I started turbostat and observed what happens under load.
For this I stressed the CPU in parallel:
```

[FONT=monospace][COLOR=#000000]stress-ng -c 4 --cpu-load 10[/COLOR]
[/FONT]
```
Here is the result
```

hrf@hrf1:~$ sudo turbostat --Summary --quiet --show Busy%,Bzy_MHz,IRQ,PkgWatt,PkgTmp,GFXWatt,CorWatt --interval 0.2

2.79    744     120     47      2.39    0.12    0.12
30.83   1805    253     50      7.07    3.88    0.12
61.19   1938    351     52      9.44    6.20    0.09
29.51   2248    250     54      8.89    5.28    0.10
19.70   1886    196     48      6.10    2.80    0.09
2.66    702     142     47      2.37    0.11    0.12
2.28    721     120     50      2.24    0.09    0.12
2.30    751     125     47      2.35    0.10    0.12
2.35    741     107     47      2.28    0.09    0.12
2.05    761     108     46      2.34    0.11    0.12
2.44    731     117     47      2.28    0.10    0.12
2.24    777     108     46      2.30    0.10    0.12
1.92    775     110     48      2.27    0.09    0.12
2.35    706     119     46      2.27    0.10    0.12
1.86    785     107     46      2.34    0.09    0.12
2.04    781     115     46      2.39    0.10    0.13
7.95    1936    139     47      3.91    1.22    0.12
33.75   2145    250     49      9.13    5.69    0.09
65.26   2005    340     54      9.69    6.45    0.09
50.64   2004    329     52      9.67    6.37    0.10
20.34   1901    212     49      5.67    2.74    0.09
1.94    762     93      48      2.24    0.08    0.12
2.35    730     121     48      2.36    0.10    0.12
2.38    718     118     47      2.31    0.10    0.12
2.75    682     104     47      2.35    0.11    0.12
25.74   2201    213     51      8.43    4.84    0.09
25.58   2085    230     50      8.10    4.40    0.10
1.95    889     112     47      2.28    0.12    0.12
2.26    708     124     47      2.39    0.09    0.13
2.31    758     139     48      2.36    0.10    0.13
2.42    771     152     47      2.42    0.11    0.13
1.93    781     104     46      2.39    0.09    0.13
2.03    750     104     46      2.34    0.09    0.12
2.35    804     137     47      2.44    0.12    0.12
2.23    766     130     50      2.51    0.11    0.13
2.18    752     113     47      2.33    0.10    0.12
6.03    1109    180     47      3.28    0.40    0.12
18.68   2132    206     47      6.84    3.33    0.12
25.56   2280    233     48      8.76    5.12    0.10
7.11    2065    130     47      3.40    1.16    0.09
2.95    712     130     48      2.51    0.12    0.12
7.49    1419    120     46      3.42    0.83    0.12
35.66   2094    266     51      9.02    5.63    0.10
48.70   1994    331     51      9.66    6.43    0.09
21.72   1693    184     48      6.22    2.69    0.10
21.87   607     193     50      4.76    0.83    0.12 # <------------- Here it is going to throttle
27.35   600     220     48      4.97    0.95    0.12
27.38   600     219     47      4.96    0.95    0.13
27.30   600     200     47      5.05    1.00    0.12
27.32   600     184     47      5.05    0.99    0.13
55.27   600     348     48      5.44    1.61    0.12
30.27   600     256     48      5.02    0.94    0.12
9.67    600     146     47      2.86    0.30    0.13
2.94    600     124     47      2.41    0.10    0.13
3.06    600     140     47      2.52    0.10    0.14
4.73    600     176     47      2.66    0.15    0.13
42.83   600     329     47      4.96    1.23    0.14
46.85   600     311     46      5.30    1.38    0.12
27.15   600     190     46      4.99    0.96    0.13
27.09   600     166     46      5.00    0.96    0.12
27.37   600     202     48      5.10    1.02    0.13
27.20   600     184     47      5.08    1.02    0.12
27.32   600     193     46      5.00    0.92    0.13
39.47   600     271     48      5.15    1.23    0.12
29.24   600     205     47      5.02    0.98    0.12
52.38   600     290     47      5.11    1.12    0.12
52.30   600     284     47      5.10    1.09    0.12
52.43   600     340     47      5.20    1.17    0.13
52.50   600     294     47      5.43    1.67    0.12
52.25   600     286     47      5.49    1.72    0.12
35.32   600     265     47      5.08    1.06    0.12
3.99    600     106     47      2.52    0.15    0.13
2.50    600     96      47      2.36    0.09    0.14
2.88    600     118     47      2.42    0.10    0.13
2.52    600     94      46      2.43    0.08    0.14
3.23    600     143     47      2.50    0.11    0.14
2.62    600     109     48      2.39    0.09    0.13
2.78    600     118     46      2.45    0.10    0.13
2.87    600     130     46      2.44    0.10    0.13
2.69    600     105     46      2.42    0.09    0.14
2.81    600     118     46      2.43    0.09    0.13
2.71    600     104     47      2.36    0.09    0.13
2.70    629     116     46      2.43    0.09    0.14
2.42    743     127     46      2.31    0.10    0.12
2.32    726     120     46      2.32    0.09    0.12
2.62    725     148     46      3.11    0.12    0.12
2.23    697     109     45      2.32    0.09    0.12
7.04    778     247     46      3.47    0.33    0.28

``` 

```

[FONT=monospace][COLOR=#000000]sudo rdmsr --bitfield 10:10 -u 0x1B1[/COLOR]
[/FONT]
```
returns 1, when throttled and returns 0, when not throttled. 

The thermal hysteresis switches the states when reaching 55 degrees into throttling, and at 48 degrees into not throttling. 
The thermald-conf.xml in /etc/thermald is missing. Thermald is writing its configuration file in /var/run/thermald/thermald-conf.xml.auto.

@DougS Can you see any inconsistencies?
@uninvolved AC adapter and power supply should be fine. I've tested different manufacturers. As already said, the system runs stable under Windows (dual-boot).

---

### Post by Doug S on 2022-02-24
> **linucyphre said:**
> 
@DougS Can you see any inconsistencies?
It looks like power limit throttling to me. The way to know for certain is to slowly approach the limits from the low side, using (for example):

```
echo 68 | sudo tee /sys/devices/system/cpu/intel_pstate/max_perf_pct
```

while watching with turbostat.

Also the various log bits can be reset, and then the tests run, the bits can then tell the answer (At least, I think. I don't have time to re-read this whole thread at the moment).

---

### Post by linucyphre on 2022-03-08
Here is another short status report.

It seems like the CPU scaling works only when the temperature drops below a certain level (around 42 degrees).
As soon as there is a small load on the system, which heats the system up to 10 degrees, the throttling kicks in immediately and the system only stops throttloing when the required low temperature is reached.

In a Linux Mint system with Plasma attached, the load on the operating system itself is so heavy, that the system does not get into scaling mode at all.
So I stayed in a less cpu intensive os.

BTW - On the Windows system, there is only a throttling when the battery level goes below 14%.

Enabling or disabling or customizing the thermald service does not affect the behavior. Tried some .xml files with different parameters. Even if thermald is completely removed, the behavior of the CPU is quite identical.

Since the C-states are controlled by the CPU and there is no corresponding entry in the BIOS, I see no way of getting the system up and running.
If I could manipulate the startup temperature that activates throttled mode, I probably would have a chance.:(

---

### Post by Doug S on 2022-03-08
Suggest that you disable turbo in the BIOS, thus limiting your maximum CPU frequency to 1.6 GHz, and try from there. I have no idea why your temperature limits would be so low.

---

### Post by linucyphre on 2022-03-17
UPDATE:
I made a new test with a KUBUNTU 20 operating system:
The device is throttled from the beginning. 

Even taking the device outside in the cold doesn't matter.
With an environment temperature of -1 Degrees the PKG-temperature lows from 57 to 35 Degrees, but the throttling indicator still shows "1" (throttled).

So i can exclude a thermal-based throttling.

Strange, strange. 


I've ordered another "fresh" device - to find out if the actual device has a hardware, sensor problem or there is a "too secured" BIOS problem.

---

### Post by linucyphre on 2022-04-01
I&#8216;ve tested a brandnew device with a clean system.
Yes, it is definitively a Linux problem.
Same behavior. Same lack of control.

Linux fails on this devices handling the CPU Management.

---

### Post by QIII on 2022-04-01
You have made an interesting point:  "... on this device ..."

This is not a general problem, as it works perfectly well on my machines (and always has) and on enough machines that yours is a pretty rare complaint.

I don't have time right now, but it might be interesting to search launchpad.net for that particular hardware and see if there is a bug reported.

---

### Post by Doug S on 2022-04-01
There remains recommended tests that you have not done. See my [post #35]("https://ubuntuforums.org/showthread.php?t=2471619&page=4&p=14082892#post14082892"), for example.

---

### Post by linucyphre on 2022-04-07
Thank you for the hints. Unfortunately, I can't find any further information on launchpad.net.

Yes, it's just this special type of tablet that doesn't work as it should. I have other fanless and robust PANASONIC tablets and computers that work beautifully with Windows and Linux. 
According to the hardware specs, the throttling should only be active at about 100 degrees Celsius. However, as soon as the PKG-temperature exceeds 55 degrees Celsius, throttling begins and the frequency drops to 600 MHz. What's really important, is to find out, what's causing the throttling when it hits 55 degrees Celsius.

See this behavior at a small cpu load:
[https://imgur.com/a/EwOBUNl](https://imgur.com/a/EwOBUNl)

---

### Post by linucyphre on 2022-05-03
After almost two months of research, I finally got the PANASONIC FZ-M1 up and running under Linux.:P

I've searched all the forums and tested all the suggestions. Without success. UBUNTU doesn't offer me a solution here.

Rather, an installation of FEDORA with a suitable dptf-service (pp3345/dptf) in combination with modified governor start script was finally successfull.

---

