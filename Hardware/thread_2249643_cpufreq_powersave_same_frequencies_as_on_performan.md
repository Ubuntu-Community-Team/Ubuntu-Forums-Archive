---
title: "cpufreq powersave same frequencies as on performance - efi - 14.10 - i5"
date: 2014-10-23
forum: Hardware
---

### Post by erik.kubica on 2014-10-23
Hi,

today i have installed ubuntu 14.10 to try it, i have installed in ufei mode.

I have read about intel p_state (because i miss ondemand), but maybe i am wrong, but also with p_state, poversave does not need to be low freq?

```

+++ Processor
CPU Model      = Intel(R) Core(TM) i5-3210M CPU @ 2.50GHz

/sys/devices/system/cpu/cpu0/cpufreq/scaling_driver    = intel_pstate
/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor  = powersave
/sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq  =  3100000 [kHz]
/sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq  =  3100000 [kHz]

/sys/devices/system/cpu/cpu1/cpufreq/scaling_driver    = intel_pstate
/sys/devices/system/cpu/cpu1/cpufreq/scaling_governor  = powersave
/sys/devices/system/cpu/cpu1/cpufreq/scaling_min_freq  =  3100000 [kHz]
/sys/devices/system/cpu/cpu1/cpufreq/scaling_max_freq  =  3100000 [kHz]

/sys/devices/system/cpu/cpu2/cpufreq/scaling_driver    = intel_pstate
/sys/devices/system/cpu/cpu2/cpufreq/scaling_governor  = powersave
/sys/devices/system/cpu/cpu2/cpufreq/scaling_min_freq  =  3100000 [kHz]
/sys/devices/system/cpu/cpu2/cpufreq/scaling_max_freq  =  3100000 [kHz]

/sys/devices/system/cpu/cpu3/cpufreq/scaling_driver    = intel_pstate
/sys/devices/system/cpu/cpu3/cpufreq/scaling_governor  = powersave
/sys/devices/system/cpu/cpu3/cpufreq/scaling_min_freq  =  3100000 [kHz]
/sys/devices/system/cpu/cpu3/cpufreq/scaling_max_freq  =  3100000 [kHz]

---

analyzing CPU 0:
  driver: intel_pstate
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 0.97 ms.
  hardware limits: 1.20 GHz - 3.10 GHz
  available cpufreq governors: performance, powersave
  current policy: frequency should be within 3.10 GHz and 3.10 GHz.
                  The governor "powersave" may decide which speed to use
                  within this range.
  boost state support:
    Supported: yes
    Active: yes
    25500 MHz max turbo 4 active cores
    25500 MHz max turbo 3 active cores
    25500 MHz max turbo 2 active cores
    25500 MHz max turbo 1 active cores



```

**_I want to get some normal balance_**, my fan is nearly always going, and notebook is heater that it was before 14.10, or on opensuse.
It fully updated "clean" install with tlp, in powertop only 1 thing is shown as bad and it is missing ondemand.


Thank you

---

### Post by Doug S on 2014-10-23
> **erik.kubica said:**
> ...and it is missing ondemand.The intel_pstate driver does not have ondemand mode. For the intel_pstate driver the "powersave" frequency governor is roughly equivalent to, but typically has better performance than, the acpi-cpufreq driver using the "ondemand" frequency governor.

What do you get for this?:```
doug@s15:~/temp$ [COLOR=#ff0000]grep . /sys/devices/system/cpu/intel_pstate/*[/COLOR]
/sys/devices/system/cpu/intel_pstate/max_perf_pct:100
/sys/devices/system/cpu/intel_pstate/min_perf_pct:42
/sys/devices/system/cpu/intel_pstate/no_turbo:0
```That is what matters here.

---

### Post by erik.kubica on 2014-10-23
i know that there is no ondemand in new kernel that suports pstate but its crazy to have same freq scale on powersave as on performance.
Output with conected charger and selected powersave governor
```

erik@erik-Lenovo-B590:~/Downloads$ grep . /sys/devices/system/cpu/intel_pstate/*
/sys/devices/system/cpu/intel_pstate/max_perf_pct:100
/sys/devices/system/cpu/intel_pstate/min_perf_pct:100
/sys/devices/system/cpu/intel_pstate/no_turbo:0

```

---

### Post by Doug S on 2014-10-23
> **erik.kubica said:**
> i know that there is no ondemand in new kernel that suports pstate but its crazy to have same freq scale on powersave as on performance.Agreed.
It is not clear to me what is wrong. For a test, could you try using the acpi-cpufeq driver? How you would do it is: First, save a copy of your grub file:```
sudo cp /etc/default/grub /etc/default/grub.backup
```Second, edit the grub file and disable the intel pstate driver on the GRUB_CMDLINE_LINUX_DEFAULT line. Example, but other stuff on your line will probably be different)```
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 intel_pstate=disable"
```Note use sudo to edit, i.e.```
sudo nano /etc/default/grub
```but use whatever editor you like to use.
Third update grub:```
sudo update-grub
```Forth, reboot.
Let us know how the acpi-cpufreq driver behaves, and we'll go from there.

---

### Post by erik.kubica on 2014-10-24
with acpi i have all of frequencies
```

erik@erik-Lenovo-B590:~$ cpupower frequency-infoanalyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 1.20 GHz - 2.50 GHz
  available frequency steps: 2.50 GHz, 2.50 GHz, 2.40 GHz, 2.30 GHz, 2.20 GHz, 2.10 GHz, 2.00 GHz, 1.90 GHz, 1.80 GHz, 1.70 GHz, 1.60 GHz, 1.50 GHz, 1.40 GHz, 1.30 GHz, 1.20 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 2.00 GHz and 2.50 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 2.00 GHz.
  cpufreq stats: 2.50 GHz:62,04%, 2.50 GHz:0,00%, 2.40 GHz:0,93%, 2.30 GHz:0,21%, 2.20 GHz:0,04%, 2.10 GHz:0,03%, 2.00 GHz:36,76%, 1.90 GHz:0,00%, 1.80 GHz:0,00%, 1.70 GHz:0,00%, 1.60 GHz:0,00%, 1.50 GHz:0,00%, 1.40 GHz:0,00%, 1.30 GHz:0,00%, 1.20 GHz:0,00%  (134)
  boost state support:
    Supported: yes
    Active: yes
    25500 MHz max turbo 4 active cores
    25500 MHz max turbo 3 active cores
    25500 MHz max turbo 2 active cores
    25500 MHz max turbo 1 active cores


```

---

### Post by Doug S on 2014-10-24
O.K. That is very interesting.

Your cpufreq stats are also very interesting, and your Computer seems to be very busy.

Are you willing to try to investigate what is going on with the intel_pstate driver or do you just want to proceed using the acpi-cpufreq driver? If you are willing to investigate, it'll take me a bit to think of the next step, but meanwhile do you see anything in the logs (/var/log/kern.log /var/log/boot.log) that might help?

---

### Post by erik.kubica on 2014-10-25
i want to try it, it will help in feature developement and i am open to new things
[ATTACH]257480[/ATTACH]
To the cpu is busy part, only firefox is running with this page opened.

---

### Post by Doug S on 2014-10-25
From your boot.log file I see that your computer has other issues also.

I missed this the other day:```
current policy: frequency should be within 2.00 GHz and 2.50 GHz.
```And that doesn't seem correct either.
I wonder if you have competing resources. Do you have a file here "/etc/laptop-mode/conf.d/cpufreq.conf"? If yes, what are the contents of the file.

---

### Post by erik.kubica on 2014-10-25
i have removed cpufrequtils, disabled acpi, removed thermald, enabled systemd instead of upstart
and now
```

erik@erik-Lenovo-B590:~$ grep . /sys/devices/system/cpu/intel_pstate/*
/sys/devices/system/cpu/intel_pstate/max_perf_pct:100
/sys/devices/system/cpu/intel_pstate/min_perf_pct:38
/sys/devices/system/cpu/intel_pstate/no_turbo:0
--
analyzing CPU 0:
  driver: intel_pstate
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 0.97 ms.
  hardware limits: 1.20 GHz - 3.10 GHz
  available cpufreq governors: performance, powersave
  current policy: frequency should be within 1.20 GHz and 3.10 GHz.
                  The governor "powersave" may decide which speed to use
                  within this range.
  boost state support:
    Supported: yes
    Active: yes
    25500 MHz max turbo 4 active cores
    25500 MHz max turbo 3 active cores
    25500 MHz max turbo 2 active cores
    25500 MHz max turbo 1 active cores

```
i dont know which step from above were the fix, but it seems to work.
Thank you for help

---

### Post by Doug S on 2014-10-25
> **erik.kubica said:**
> i have removed cpufrequtils, disabled acpi, removed thermald, enabled systemd instead of upstart
and now
...
i dont know which step from above were the fix, but it seems to work.I don't know either, but glad you got it working and thanks for reporting back.

Edit: I suspect thermald, but have no proof.

---

### Post by Mike_Beckerle on 2014-12-11
I did sudo apt-get remove cpufreqd

And now my system is running properly again. The problem I was having was that the whole system, due to some update since 14.04 first was released, became slow. As if it was stuck at 800Mhz, though lscpu and various other things showed faster speed clock numbers, a tiny C program that I used to check CPU performance was running at about 25% the speed it was when 14.04 was first installed. After removing cpufreqd, things are back to normal.

---

### Post by Mike_Beckerle on 2014-12-11
My system was different, but still a CPU frequency problem. This started sometime in the past month with some patch release to 14.04. My system was running way too slowly. A little C program I use as a benchmark was running at 25% the speed it used to, though lscpu and the frequency thingy in the menu bar were showing 2.5Ghz.

sudo apt-get remove cpufreqd

fixes it.

---

### Post by pfeiffep on 2014-12-12
Not entirely certain if this applies to 14.10 since I'm only running 14.04 LTS ... I have CPU Frequency Scaling Monitor listed in start-up. This enables me to both monitor and switch frequencies ... an added benefit to me is the last setting is maintained on reboot.

---

