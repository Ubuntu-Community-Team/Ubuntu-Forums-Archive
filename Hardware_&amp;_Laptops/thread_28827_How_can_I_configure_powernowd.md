---
title: "How can I configure powernowd?"
date: 2005-04-21
forum: Hardware &amp; Laptops
---

### Post by Rehevkor on 2005-04-21
I'm running Ubuntu Hoary on my Inspiron 8500, and I would like to adjust the cpu scaling. According to the CPU frequency monitor gnome applet, it only drops to 50% when idle (1.2ghz). I would like to set the minimum much lower, 20% perhaps, but I don't know where to do this.

I tried searching the forums, but I couldn't find anything on how to change powernowd's settings.

Oh, and how can I put the system into stand-by/sleep mode? I found hibernate in the shutdown options, but I'm not interested in that.

---

### Post by AlP on 2005-04-22
Hi, 

I would guess this is not possible (at least not efficiently). May be you can trottle down the CPU further, but it is quite normal, that you can only adjust do half the maximum speed, it is hardwired in the Penitium M CPUs which frequencies can be set. 

The savings eventhough would be minimal, 'cause the power consumption is not directly propotional to the CPU frequency. Half freqency does not mean halfe power consumption, but signifcantly less).

A thing you could do is setting your the frequncy govenour to _ondemand_, which means the handling of the frequency is done directly by the CPU, not by an userspace tool. 

Try 
# echo 'ondemand' > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
To see if ti works check if the CPUFrequencyApplet shows "ondemand" on mouseover.

HtH, AlP

---

### Post by Rehevkor on 2005-04-22
[QUOTE=AlP]Hi, 

I would guess this is not possible (at least not efficiently). May be you can trottle down the CPU further, but it is quite normal, that you can only adjust do half the maximum speed, it is hardwired in the Penitium M CPUs which frequencies can be set. 

The savings eventhough would be minimal, 'cause the power consumption is not directly propotional to the CPU frequency. Half freqency does not mean halfe power consumption, but signifcantly less).

A thing you could do is setting your the frequncy govenour to _ondemand_, which means the handling of the frequency is done directly by the CPU, not by an userspace tool. 

Try 
# echo 'ondemand' > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
To see if ti works check if the CPUFrequencyApplet shows "ondemand" on mouseover.

HtH, AlP[/QUOTE]
 Thanks. That did work, but it still only goes to 50%. I'm sure my CPU has more steps than that (it's a P4-M). 

In Windows I used an app called SpeedStep (or something) and I was able to actually set a max CPU speed when on battery. That helped noticably, especially considering that this laptop is nearly two years old, and the battery isn't holding a charge so well anymore. It lasts about 1.5 hours in Windows even with the brightness all the way down and SpeedStep running.

It's no big deal though. I only use this on battery for school, which is over for the summer in two weeks, so I can just leave it on AC power until I get a new laptop in the fall :)

---

### Post by Spif on 2005-04-23
Take a look at this topic: [http://www.ubuntuforums.org/showthread.php?t=14864&highlight=configuring+powernowd](http://www.ubuntuforums.org/showthread.php?t=14864&highlight=configuring+powernowd)

---

