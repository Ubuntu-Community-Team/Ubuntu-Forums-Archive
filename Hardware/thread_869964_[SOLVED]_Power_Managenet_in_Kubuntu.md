---
title: "[SOLVED] Power Managenet in Kubuntu"
date: 2008-07-25
forum: Hardware
---

### Post by uraldinho on 2008-07-25
Hi, 

I don't know where to start from, so this post might end up being a bit complicated. Please, bear with me. 

I recently noticed that my laptop doesn't perform well when on batteries. I've had the same Kubuntu installation since ver 6.10 and I'm on 8.04 now. When I was upgrading to 8.04 I did a bit of a clean up and I might have changed the settings for some programs. 

I use "guidance-power-manager" to set the power options. I setup the battery mode to "performance", and when on batteries the CPU stays at 1600MHz for a minute or two. The problem is that, my CPU goes down to 800MHz and doesn't step up to 1600MHz again. At this point the CPU is so slow that my laptop is practically unusable. 

I tried KPowersave and I have the same problem. 

I get the feeling that "guidance-power-manager" settings get overwritten somewhere and my laptop goes into power save mode. 

I have the following cpu, acpi, and powernow modules loaded by default: 

1.CPU:
cpufreq_userspace       5284  0
cpufreq_stats           7104  0
cpufreq_powersave       2688  0
cpufreq_ondemand        9740  1
freq_table              5536  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8712  0


2. ACPI: 
pata_acpi               8320  0
libata                159344  3 pata_atiixp,pata_acpi,ata_generic

3. powernow
powernow_k8            16704  0
cpufreq_powersave       2688  0
freq_table              5536  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
processor              36872  3 powernow_k8,thermal



I guess my question is, what's making my laptop go into power save mode and prevents it from going up again? 

Thanks 

PS: My CPU is AMD Turion 2.0GHz

---

### Post by uraldinho on 2008-07-25
Update: 

I have the following warnings in my log files: 
[   65.144071] Marking TSC unstable due to: cpufreq changes.
[   65.148072] Time: acpi_pm clocksource has been installed.
[   65.879927] Clocksource tsc unstable (delta = -99965795 ns)
[   67.698255] apm: BIOS not found.

I think these are related. I'll go a bit of searching and see if I can come up with something.

---

### Post by uraldinho on 2008-07-25
As I said in my first thread, I did a bit of a clean up and looks like I messed up. 

I had APM and ACPI running at the same time. I think it was the APM that was causing the problems. Basically, I had two power manager running at the same time. 

"apm: BIOS not found" line in the log files led me to a few forums that strongly advice using ACPI only. So I removed APM, and the problem is solved.

---

