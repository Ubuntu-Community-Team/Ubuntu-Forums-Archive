---
title: "Random kernels freezes on dell 3147"
date: 2015-11-15
forum: Hardware
---

### Post by kreoouzis on 2015-11-15
I have installed ubuntu 15.10 in Dell 3147 laptop but i have a lot of Random kernel Freezes.The system totally hang and i cant see anything in log files.I am sure it is something about with kernel 4.x cause the system is totally stable with kernel version 3.x..

Any suggestions what cause this problem with kernel series 4.x?

---

### Post by Frank_Estrada on 2015-12-08
[COLOR=#000000]Random kernel Freezes.The system totally hang and i cant see anything in log files.[/COLOR]
No answers for me either, I am also having this issue with 
[COLOR=#000000][FONT=Ubuntu]Canonical [/FONT][/COLOR]15.10 on a 
Dell 3147
 8 GB of Ram and an 
SSD HD
Processor: Intel® Pentium(R) CPU N3530 @ 2.16GHz × 4 
Graphics:  Intel® Bay Trail 
OS Type: 64-bit

---

### Post by kashenko on 2015-12-15
Same here. Solved it about a month ago by adding intel_pstate=disable to kernel boot parameters and using cpupower with acpi-cpufreq driver. Using 4.1.14-1-lts kernel on Arch &#8212; it's a common Linux 4.x problem with this laptop (or Bay trail/intel 915 itself).

Not a single freeze until today. In the last 24 hours I've got a couple of freezes again. Maybe it's related to bios update A09 I've performed today or that I've switched from entire Gnome stack to i3wm.

I'll wait for the next freeze, check some logs further, compile linux-mainline 4.4, downgrade to A07 bios I've used before. Hate this.

---

### Post by arseny1991 on 2016-03-04
Any one know of a fix yet? I just installed last night Ubuntu 15.10 (64-Bit). Got around 4 freezes. Most seem to happen when i watch a few YouTube videos. 

Dell 3147 (N3530)
8Gb Hyper-X Ram 
Samsung 850 SSD (250GB)

---

