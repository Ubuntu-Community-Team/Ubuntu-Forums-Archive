---
title: "Scaling Frequencies Problem"
date: 2006-09-06
forum: Hardware &amp; Laptops
---

### Post by dutchman25 on 2006-09-06
I have a HP Pavilion dv5000 with a AMD Turion ML-37.  It should support cpu scaling from 800 MHZ to 2000 MHZ.  The system information available shows that to me: 

"cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
2000000 1800000 1600000 800000"

My powernowd did work fine previously, but suddenly, my processor will not scale to above 1600 MHZ.  It will step, but just not above 1600 MHZ.

I've tried "echo 2000000 > scaling_max_freq" and no errors are reporting, but when I "cat scaling_max_freq" it remains set at 1600 MHZ.

Does anyone have any idea what this problem might be from and how to fix it?

---

### Post by StarQuake on 2006-09-07
Did you try changing governor's or frequencies with the cpufreq-selector tool?

Like cpufreq-selector -g performance

or

cpufreq-selector -f 2000000

---

