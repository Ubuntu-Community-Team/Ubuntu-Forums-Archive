---
title: "Core2Duo do not reach maximum frequency"
date: 2007-03-17
forum: Hardware &amp; Laptops
---

### Post by Strelock on 2007-03-17
Guys, a weired issue: I have a Core2Duo 2.16 MHz and no matter the load it doesn't wanna go above 1.67 according to System monitor applet and 
cat /sys/devices/system/cpu/cpu1/cpufreq/cpuinfo_cur_freq

Say now I have dvd::rip running and 
cat /sys/devices/system/cpu/cpu1/cpufreq/cpuinfo_cur_freq returns 1667000


cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies:
2167000 1667000 1333000 1000000

So it can go higher... Manual cpufreq-selector -c 1 -f 2167000 doesn't help...

Any ideas?

---

### Post by ahaslam on 2007-03-17
Have you tried the performance governor, or disabling power saving?

---

### Post by berylmichael on 2007-03-17
This is a long-shot but check the system BIOS to ensure that the processor is operating at required speed and isn't stepped down to a lower setting. 

Michael

---

### Post by Strelock on 2007-03-18
Just tried that - exactly the same - If I choose performance governor CPU freq do not go below 1.67, but even if i set it manually to 2.17 it still do not climb over 1.67....

BIOS shouldn't be a problem - the CPU cores are detected as 2.17... and under WinXP it was going all the way up...

---

### Post by Strelock on 2007-03-18
Well, just checked bios and disabled virtualization (didn't help except I think my fan's are running bit quiter) HP bioses are bit limited on parameters you can tune...

---

### Post by Strelock on 2007-04-11
Hmm IHmm I still do not have a solution... Anybody found out something?

---

### Post by Strelock on 2007-04-11
sorted it out! thanks to last post [here]("http://ubuntuforums.org/showthread.php?t=398616")
scaling_available_frequencies shows everything correctly, but scaling_max_freq was at 1670000... MAde a script to fix it...

---

