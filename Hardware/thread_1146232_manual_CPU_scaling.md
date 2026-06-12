---
title: "manual CPU scaling"
date: 2009-05-02
forum: Hardware
---

### Post by zorbawic on 2009-05-02
Hello, 

the issue is a little more complicated than the title might say so I'll say it this way:

I got Intel C2D T5500 cpu. 

Under Windows XP I am not able to select any speed "manually" so I have been doing some tricks and this way I managed to find out that my cpu is able to go way down from 1.66 GHz to just 249 MHz. 
However I never managed to get below 997MHz without unplugging the power supply and using only the battery. 
On "battery saving" mode I was able to get either something like 350 MHz or 249 MHz depending on needs of processing power. 
All that was done only using OS and software supplied by the producer of my laptop. 

To sum up:  On AC I was able to "select" only between 1.66 GHz or 997 MHz. On Battery I was able to "select" between 997 MHz, 750 MHz*, 350 MHz* and 249 MHz.  

* - I don't remember the exact numbers as at that time they ware of no interest for me - only the other ones, but I am sure there ware those two at somewhere around those numbers


Now I want to be able to scale down my cpu freq manually and it appears that Ubuntu/Linux gives more freedom in manually selecting cpu scaling.

The thing is that I am able to use scaling governors (jaunty) and select only between 1.66 GHz, 1.33 GHz and 996 MHz. The trick with unplugging power supply does not work here and I still have the same three options from CPU frequency monitor. I want to be able to select the lower speeds which I was able to "select" on Windows. 

This is the output of cpufreq-info both on AC and battery:
```
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 996 MHz - 1.66 GHz
  available frequency steps: 1.66 GHz, 1.33 GHz, 996 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 996 MHz and 1.66 GHz.
                  The governor "powersave" may decide which speed to use
                  within this range.
  current CPU frequency is 996 MHz.
  cpufreq stats: 1.66 GHz:0,00%, 1.33 GHz:0,00%, 996 MHz:0,01%  (412)
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 1
  hardware limits: 996 MHz - 1.66 GHz
  available frequency steps: 1.66 GHz, 1.33 GHz, 996 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 996 MHz and 1.66 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 996 MHz.
  cpufreq stats: 1.66 GHz:0,00%, 1.33 GHz:0,00%, 996 MHz:0,01% (619)
```

Obviously the hardware limits are wrong as I am sure that those 249 MHz I had on Windows really ware 249 MHz as I have seen appropriate performance loss in benchmarks such as Sisoft Sandra AND - this way was the only way I was able to play an over 10 years old game which simply crashed after at most a few minutes after starting it on 997 MHz and upwards (the CPU was just too fast for the game).
Another thing is that I've never seen the speed of 1.33 GHz on Windows.

If anyone knows how would it be possible to make my CPU go below 996 MHz
- Please help 
as I either am doing something wrong or cpudynd, cpufreqd, powernowd (I've tried that just in case), emifreq-applet just doesn't work for me.

---

### Post by zorbawic on 2009-05-07
bumm...p

---

