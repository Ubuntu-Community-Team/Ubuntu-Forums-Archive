---
title: "CPU frequency scaling issues"
date: 2010-11-26
forum: Hardware
---

### Post by novaraz on 2010-11-26
Hi everyone,
I have a persistent problem with Ubuntu on my desktop.  Starting with 9.04, then 9.10 and still with 10.04, 1 of the 4 cores seems stuck at the lowest scaling option.  Background: the CPU is Core 2 Quad Q6600, with 2 levels (1.6 and 2.4 GHz) on an Abit IP35 Pro mobo (latest BIOS).  All installs are AMD64.  Basically, I launch an app that uses 4 threads, and CPU0 runs at 1.6, while CPU1-3 run at 2.4GHz.  I see that many people have had variants of this problem, and I tried several different approaches to scaling (cpufreqd, etc).  Eventually, I went to vanilla 10.10, and the problem persists using the LiveCD.  The output of 
```
$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies 
2400000 1600000 
$ cat /sys/devices/system/cpu/cpu1/cpufreq/scaling_available_frequencies 
2400000 1600000
$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
1600000
$ cat /sys/devices/system/cpu/cpu1/cpufreq/scaling_max_freq
2400000
```
So it seems the policy is setup incorrectly for CPU0 on this processor.  Any ideas how to change it using Ubuntu's default cpu scaling implementation?

---

### Post by conradin on 2010-11-26
[http://embraceubuntu.com/2005/11/04/enabling-cpu-frequency-scaling/](http://embraceubuntu.com/2005/11/04/enabling-cpu-frequency-scaling/)
Check that out, its helped me.

---

### Post by Fafler on 2010-11-26
I thought all cores in Core 2 CPU's with more than one core had to run at the same speed. Have you done some test to establish that it's not just a false readout?

---

### Post by novaraz on 2010-12-03
Actually, it seems to be a false reading.  It's strange that the gnome applet show the freq jumping processor to processor, but some tests revealed perfect scaling, so I'm not going to worry about.

Threads	Freq	OMP_get_wtime()	Speed up (#threads)	Speed up (freq)
1	1600	15.557	1.00	1.00
4	1600	3.9612	3.93	1.00
1	2400	10.462	1.00	1.49
4	2400	2.6449	3.96	1.50

and 2400/1600 = 1.5, so thats as good as it gets :p

thanks for the advice.

---

### Post by novaraz on 2010-12-03
Actually, I've spoke too soon.  If an individual thread launches on CPU0, the result is ~15s.  So the freq governor is NOT working for CPU0...

---

