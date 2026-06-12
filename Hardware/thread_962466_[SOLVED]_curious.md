---
title: "[SOLVED] curious"
date: 2008-10-29
forum: Hardware
---

### Post by theozzlives on 2008-10-29
The ad on my laptop said it's a 2GHz Dual Core, but Ubuntu says I have 2 1.73GHz processors. I was wondering which one was wrong.

---

### Post by phidia on 2008-10-29
What specific make and model do you have and how are you seeing that output? When you noticed that were you on battery or AC?

From a terminal enter "sudo lshw" I believe that will show your processor.

---

### Post by theozzlives on 2008-10-29
It's a Dell Inspiron 1525, the output is in the CPU load in the GNOME panel and I'm running on AC. I'll try your command and see what it says.

---

### Post by theozzlives on 2008-10-29
> **phidia said:**
> What specific make and model do you have and how are you seeing that output? When you noticed that were you on battery or AC?

From a terminal enter "sudo lshw" I believe that will show your processor.

     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) Dual  CPU  T2370  @ 1.73GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          slot: Microprocessor
          size: 1733MHz
          capacity: 1733MHz
          width: 64 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm cpufreq

---

### Post by JMorg on 2008-10-29
Did you buy the laptop straight from the manufacturer or from a retail store? If from a retail store, it is a possibility that you got the model of PC just with a different model processor. The best way to tell is to grab the actual model off the ad and look it up online and see what the core clock speed is out of the box. I couldn't imagine an ad stating the possibility of what the CPU can safely be overclocked to but I guess it's a possibility?

---

### Post by theozzlives on 2008-10-30
My mom bought it as a b-day present from Best Buy

---

### Post by theozzlives on 2008-10-30
I have Windows  Vista and XP in a virtual box for educational purposes. The system properties on those say I have a dual CPU 1.73GHz. so I guess I don't have a 2.0GHz.

---

### Post by JMorg on 2008-10-30
> **theozzlives said:**
> My mom bought it as a b-day present from Best Buy

Yep, I, for a fact, know that Best Buy advertises an upgraded version of their models in their ads. The unit you're looking at is an upgraded model of what you got :). But no worries, your 1.73Ghz Dual Core is plenty powerful enough! That extra boost to 2Ghz on a laptop will not do too much for ya. My laptop has a dual core 2Ghz processor and I rarely max it out with a virtual machine of Cent-OS 5.2 while in XP. Also, the Dual-Core technology truly kicks in once you start multitasking such as doing a data transfer, while listening to music, while typing a spreadsheet lol. But hopefully this information helps ya out!

---

