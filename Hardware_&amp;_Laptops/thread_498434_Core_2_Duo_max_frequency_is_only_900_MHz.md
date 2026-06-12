---
title: "Core 2 Duo max frequency is only 900 MHz"
date: 2007-07-11
forum: Hardware &amp; Laptops
---

### Post by muriloq on 2007-07-11
I've got a Core 2 Duo E4300 1.8 GHz, and I'm running Feisty (kernel 2.6.20-16-generic #2 SMP), with powernowd. 

The frequency of the cores oscillates between 600 MHz and 900 MHz, and never reaches 1.8 GHz. Is this correct ? If not, how to fix it ? 
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq 900000
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_min_freq 600000
/sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies 900000 600000
/sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors powersave conservative userspace ondemand performance
/sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq 900000
/sys/devices/system/cpu/cpu0/cpufreq/scaling_driver acpi-cpufreq
/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor userspace
/sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq 900000
/sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq 600000
/sys/devices/system/cpu/cpu0/cpufreq/scaling_setspeed 900000

---

### Post by EXCiD3 on 2007-07-11
I noticed when i was running Kubuntu Feisty that i can change the settings on the Power Manager to use dynamic mode (clocking my processor down to 1.0 GHz) when on battery power and Performance (1.83 GHz) on AC power.

I dunno if you should modify those values or not. It probably isn't very safe modifying those values im guessing.

---

### Post by Rui Pais on 2007-07-11
> **muriloq said:**
> I've got a Core 2 Duo E4300 **1.8 GHz**, and I'm running Feisty (kernel 2.6.20-16-generic #2 SMP), with powernowd. 

The frequency of the cores oscillates between 600 MHz and **900 MHz**, and never reaches 1.8 GHz. Is this correct ? If not, how to fix it ?

well 900M+900M = 1800M = 1.8G

if you run an intensive multi-thread task or several intensive tasks your speed should hit the 1.8 G normally.

---

### Post by muriloq on 2007-07-12
I know the frequency is supposed to change according to the demand. The problem is that the *maximum* frequency of each core should be 1.8 GHz, not 900 Mhz. That's what happens in Windows, for example. 

The "1.8 GHz" in the CPU name does *not* means the sum of the clocks of each core.

Anyway, I fixed the problem updating the BIOS of my motherboard (Gigabyte GA-8I945GZME-RH), from F6 to F9. The website says the Core 2 Duo E4300 support was added only recently (the E4300, "Allendale", is a little bit different from the older and faster E6XXX, "Merom" and "Conroe").

---

### Post by davidsrsb on 2007-07-12
The 4300 has the same core speed, but lower ram clock

---

