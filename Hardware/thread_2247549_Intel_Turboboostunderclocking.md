---
title: "Intel Turboboost/underclocking"
date: 2014-10-08
forum: Hardware
---

### Post by user50 on 2014-10-08
I need to run a scientific computation package in ubuntu. During the process, the CPU (core i7 4790k) is heavily utilized (100% all cores) for a period of about 15sec, which causes the core temperatures to increase dramatically. Eventually they hit the limit (~100C) and computer shuts off to prevent damage. (The fan is already set to max rpm in the bios.) During this entire time, I noticed (via i7z) that all the cores are running at 4.2GHz (due to to turboboost).

If I boot into windows and try to run a stress-test (such as prime95), I find that the temperatures will also increase dramatically, but once they reach ~95C the core clock speeds will start to drop and the temperature will not increase any more. I've run stress tests overnight in windows, and while the processor runs hot (~95C) it does not power off. I looked through some of intel's documentation on this processor and that is the normal behavior.

Any ideas why the processor is not underclocking (thermal throttling) in ubuntu even though it does in windows?

---

### Post by tgalati4 on 2014-10-09
That clock-speed reduction is typically handled by the BIOS and the motherboard, using temperature information from the CPU thermal diodes.  It's possible that the Windows driver for the motherboard handles this correctly.  What version of the kernel?

```
uname -a
```

Perhaps a newer kernel addresses this.  Search for a bug against your current kernel version.  Look for "turboboost".

You can add a panel widget to set CPU speed to a fixed value.  Look for "CPU Scaling Frequency Monitor".  Put some temperature monitors on your panel as well and use the manual speed selector to pick something lower than 4.2 GHz.

Is this a laptop?

---

### Post by Michael_McKenney on 2014-10-09
I would consider a larger tower chassis and Panflo fans.  Keep it in an open space instead of under or in a desk.   Cooler Master tower has a lot of room and fan openings.  Panflo fans are 30 dB and provide higher volume.  You want same amount of inbound and outbound fans.

---

### Post by Doug S on 2014-10-09
Thermal throttling of Intel Processors of the type you have should be automatic. However, there have been many recent changes.
In addition to what tgalati4 asked for, what version of ubuntu are you using and what cpu frequency governor are you using? Example:```
doug@s15:~/docs-1404/tt_point_release$ [COLOR=#ff0000]lsb_release -a[/COLOR]
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:        14.04
Codename:       trusty
doug@s15:~/docs-1404/tt_point_release$ [COLOR=#ff0000]cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver[/COLOR]
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
doug@s15:~/docs-1404/tt_point_release$ [COLOR=#ff0000]cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor[/COLOR]
powersave
powersave
powersave
powersave
powersave
powersave
powersave
powersave
```Edit: Also if you have, or are willing to install, turbostat could you provide this:```
doug@s15:~/docs-1404/tt_point_release$ [COLOR=#ff0000]sudo modprobe msr[/COLOR]
doug@s15:~/docs-1404/tt_point_release$ [COLOR=#ff0000]sudo ~/temp/turbostat -v[/COLOR]
turbostat v3.7 Feb 6, 2014 - Len Brown <lenb@kernel.org>
CPUID(0): GenuineIntel 13 CPUID levels; family:model:stepping 0x6:2a:7 (6:42:7)
CPUID(6): APERF, DTS, PTM, EPB
RAPL: 690 sec. Joule Counter Range, at 95 Watts
cpu0: MSR_NHM_PLATFORM_INFO: 0x100070012200
16 * 100 = 1600 MHz max efficiency
34 * 100 = 3400 MHz TSC frequency
cpu0: MSR_IA32_POWER_CTL: 0x0004005d (C1E auto-promotion: DISabled)
cpu0: MSR_NHM_SNB_PKG_CST_CFG_CTL: 0x1e008403 (UNdemote-C3, UNdemote-C1, demote-C3, demote-C1, locked: pkg-cstate-limit=3: pc6)
cpu0: MSR_NHM_TURBO_RATIO_LIMIT: 0x23242526
[COLOR=#ff0000]35 * 100 = 3500 MHz max turbo 4 active cores
36 * 100 = 3600 MHz max turbo 3 active cores
37 * 100 = 3700 MHz max turbo 2 active cores
38 * 100 = 3800 MHz max turbo 1 active cores[/COLOR]
cpu0: MSR_IA32_ENERGY_PERF_BIAS: 0x00000006 (balanced)
cpu0: MSR_RAPL_POWER_UNIT: 0x000a1003 (0.125000 Watts, 0.000015 Joules, 0.000977 sec.)
...
```

---

### Post by user50 on 2014-10-14
Sorry for the late reply. I did not have access to the computer over the long weekend.

Typing uname -a returns:
```

Linux Wien2k 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```
I'm using Ubuntu 14.04.

Results of what Doug S asked me to run:
```

wien2k@Wien2k:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty
wien2k@Wien2k:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver
cat: /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver: No such file or directory
wien2k@Wien2k:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
cat: /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor: No such file or directory
wien2k@Wien2k:~$

```

It seems that I have no scaling driver or governor. I tried to look for drivers for my motherboard (ASRock Z97 Anniversary Edition), but could not find any linux driver from the manufacturer or for the Z97 chipset. The internet seemed to imply that linux should have the necessary drivers built-in.

The turbostat output looks correct. If I leave the default values enabled in the BIOS, I get 44x, 44x, 43x, 42x, CPU multipliers for 1, 2, 3, and 4 active cores, which is what they should be.

I got an CPU cooler (Cooler Master Hyper 212 EVO) today and installed it. With the processor clock set to 4.2GHz (fixed) on all cores, the maximum temperature under load that the computer reaches in Ubuntu is 64C before shutting itself off. This seems to imply that the issue is not CPU temperature (maybe PSU?). If I boot into windows and run a stress test, then everything seems stable. Core temp reaches 65C. The computer does not shut off. Also, if I underclock the CPU to 3.8GHz and boot Ubuntu, then everything runs fine with no crashes.

It seems that there is something very different about the behavior of Ubuntu and Windows 8.1 running on the same hardware. Is there any type of diagnostic file (crash dump) in Ubuntu that might be able to help me narrow down the reason for the crashes? Could there be a temperature spike that is faster than the monitoring software is recording (I'm using Psensor)? Could my power supply (350W) be dropping the voltages somewhere (but then why doesn't it happen in windows)?

Any help is appreciated.

---

### Post by tgalati4 on 2014-10-14
Error messages are recorded in /var/log/syslog.  What is the output of:

```
sensors
```

A power supply problem would show up with 12VDC dropping to 11VDC and 5VDC dropping to 4.5VDC.  

I think the problem is that you have no governor and hence anarchy rules in your system.

On a Dell system with a simple Core2 Duo:

> gates@GNAS ~ $ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver
acpi-cpufreq
acpi-cpufreq


Look through the log files for clues as to why no *cpufreq* module gets loaded.  If the processor can't go to idle speed, it will heat up quickly.  As you have discovered, you can only run 3.8 GHz in stable operation.  Without the ability to go up and down in frequency, you would need liquid cooling to maintain 4 gig and above.

---

### Post by user50 on 2014-10-15
I looked through the system logs, but did not see anything related to the cause of the crashes. Would something like a voltage drop even get logged there?

The output of sensors is below. The system is currently running under full load, but underclocked to 3.8GHz. Temperatures look pretty good to me.
```

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +48.0°C  (high = +80.0°C, crit = +100.0°C)
Core 0:         +45.0°C  (high = +80.0°C, crit = +100.0°C)
Core 1:         +48.0°C  (high = +80.0°C, crit = +100.0°C)
Core 2:         +44.0°C  (high = +80.0°C, crit = +100.0°C)
Core 3:         +43.0°C  (high = +80.0°C, crit = +100.0°C)

nct6776-isa-0290
Adapter: ISA adapter
Vcore:          +0.94 V  (min =  +0.00 V, max =  +1.74 V)
in1:            +1.85 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
AVCC:           +3.31 V  (min =  +2.98 V, max =  +3.63 V)
+3.3V:          +3.30 V  (min =  +2.98 V, max =  +3.63 V)
in4:            +0.90 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in5:            +1.71 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in6:            +0.80 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
3VSB:           +3.42 V  (min =  +2.98 V, max =  +3.63 V)
Vbat:           +3.25 V  (min =  +2.70 V, max =  +3.63 V)
fan1:          1390 RPM  (min =    0 RPM)
fan2:          1726 RPM  (min =    0 RPM)
fan3:             0 RPM  (min =    0 RPM)
fan4:             0 RPM  (min =    0 RPM)
fan5:             0 RPM  (min =    0 RPM)
SYSTIN:         +32.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPUTIN:         +40.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
AUXTIN:         +37.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
PECI Agent 0:   +47.0°C  (high = +80.0°C, hyst = +75.0°C)
                         (crit = +100.0°C)
PCH_CHIP_TEMP:   +0.0°C  
PCH_CPU_TEMP:    +0.0°C  
PCH_MCH_TEMP:    +0.0°C  
intrusion0:    ALARM
intrusion1:    ALARM
beep_enable:   disabled

```
I don't see anything refering to the 12V or 5V rails. I can check them in windows, so I'm not sure why ubuntu is not reading the sensors. Is there any way to continuously log this data, so that I can check if the voltages drop right before the system shuts off?

After a restart, I reran the scalaing-driver/governor commands and this is what I get:
```

wien2k@Wien2k:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver
acpi-cpufreq
acpi-cpufreq
acpi-cpufreq
acpi-cpufreq
acpi-cpufreq
acpi-cpufreq
acpi-cpufreq
acpi-cpufreq
wien2k@Wien2k:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand

```
I'm not sure why it was not showing anything before, but it seems that now the the drivers are loaded properly. Unfortunately, the crashes under high load are still there.

Is there a good way to directly check that the powersupply is or is not the issue? Is there a program that will log the system voltages? I don't have access to a working power supply that I can test with and I would rather not buy one until I know that that is the issue.

---

### Post by tgalati4 on 2014-10-15
You can install and run *xsensors* in a small window (set to Always on Top).  Then if your machine locks up, you will have the temperatures on top.

Use a voltmeter to measure the 5VDC on a spare power connector.  If it drops more that 5 or 10% during load, then that could indicate a weak power supply.  

You can arrange xsensors to just show voltages.  You can also add temperature/voltage widgets to your panels.

I don't think it is a heat or voltage issue.  I think there might be a glitch related to having 8 cores.  You might need a newer kernel that fixes this--if it has been flagged as a bug.  What did your bug search come up with?

---

### Post by user50 on 2014-10-15
I installed xsensors, but there still does not seem to be any fields showing the 12V or 5V rails. Also, when the computer crashes, the display does not freeze. Instead, the power shuts off the computer automatically restarts itself after a few seconds. So I need a log of the voltages so that I can look at the values after the fact. Do you know why the 12V and 5V lines are not showing up?

I don't have a voltmeter, but I'll try to borrow one.

The processor is an intel i7 4790K. It has 4 cores, but is hyperthreaded so it shows 8 logical cores. I've tried turning hyperthreadding off in the BIOS, but it did not help. A quick google search did not reveal any known issues with ubuntu and this specific processor, or 4-core intel processors more generally. Is there a better was I should be searching for knonwn bugs?

---

### Post by tgalati4 on 2014-10-15
Check the 5VDC and 12VDC values in BIOS--look in Health or Monitoring tab.  The sudden shutdown does seem to be a PSU issue.  Normally a kernel panic freeze will have the caps and numlock buttons flash.  A graphics freeze can be dumped to a terminal with Control-Alt-F1.  Otherwise, the shutdown that you describe sounds like the PSU stops supplying power for an instant--perhaps a current overload breaker inside the PSU is giving out.  

It could also be a motherboard resettable fuse that is giving out.  How old is the motherboard?  Any bulging or leaking capacitors?

Normally a bug report would include a specific error message and a set of repeatable steps to produce the behavior.  Since the behavior of your computer seems to depend on a bunch of conditions--CPU speed, running math-intensive tasks, searching for a bug may be difficult.

---

### Post by Yellow Pasque on 2014-10-15
> Any ideas why the processor is not underclocking (thermal throttling) in ubuntu even though it does in windows?

No, but I think that's the wrong question. Unless you're trying to set overclocking records, anything above 90C is too high for this CPU. Since you say the fan is running full blast, you may have an insufficient heatsink/fan, an improperly installed heatsink, or an inaccurate temp sensor. There could be other factors too, like a hot ambient temp, poor case airflow, or other components in the case generating heat and not exhausting it. I would reinstall the CPU heatsink first. Get some isopropyl/rubbing alcohol (I prefer the 90%) and cotton balls to clean the old thermal material off the heatsink and use quality thermal material when reinstalling (I prefer Arctic Silver 5).

> The sudden shutdown does seem to be a PSU issue.
Disagree. At 100C - 105C, it is the mobo issuing an emergency shutdown (through ACPI I believe) to prevent the magic smoke from escaping, i.e. cooked hardware.

---

### Post by user50 on 2014-10-16
tgalati4:

I checked the bios and all the voltages are normal, however, this is under zero load. I'm wondering if under heavy load the PSU might be dropping the voltages and causing the system to shut down. The motherboard is new and there is no physical damage or bulging/leaking capacitors. I'm trying to borrow a PSU from a friend. I'll let you know if it fixes my issue.

Temujin:

Since my initial post, I bought and installed a CPU cooler (hyper 212 evo) and now the temperatures do not exceed 70C before the machine shuts off. This is why I no longer think it an overheating issue and am starting to suspect the PSU instead.

If anybody knows why xsensors/sensors will not display entries for the +12V and +5V rails in ubuntu, please let know. If I can check if the voltages are dropping just before the machine shuts down, then I can either confirm or rule out the PSU as the source of the problems.

---

### Post by tgalati4 on 2014-10-16
Make a backup of /etc/sensor3.conf and modify it.  Voltages are typically defined as in1 through in8.  Your sensors output shows you are missing a few.  Define them in the config file and reboot.  Set tight limits and you will get messages in syslog.  Typical voltage drop under full load is -5%.  At -10%, Bad Things Happen(tm)

I agree with your assessment, your machine should not shut down at 70C.  I had a server running at 74C for 3 years, 24/7 before it gave up.  Xeon chips are tough, but not that tough.

Get a Kill-a-Watt meter and measure the wall power that is drawn under this load.  You might be surprised.  If it exceeds your PSU rating, then at is your answer.

One test is worth a thousand expert opinions.

---

