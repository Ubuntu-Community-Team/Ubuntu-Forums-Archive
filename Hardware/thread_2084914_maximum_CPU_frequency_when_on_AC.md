---
title: "maximum CPU frequency when on AC"
date: 2012-11-16
forum: Hardware
---

### Post by hani270 on 2012-11-16
hello,

i am using ubuntu 12.10 32-bit on my laptop DELL inspiron N4030 with ATI Mobility Radeon HD 5430 Series.

the problem is:

when Laptop on _AC adapter_, CPU frequency always be the **_maximum_** (2.39 GHz), **that's make out loud fan**, even i try to change that frequency, it returns automatically (to the maximum) as long as the laptop plugged in.

on the other hand ubuntu seems to (automatically) scaling the processors correctly in _battery-mode_. nevertheless i cannot change the CPU frequency In all cases.

what to do? i can't work comfortably when my laptop plugged in AC adapter!

[IMG]http://i1045.photobucket.com/albums/b456/badstuber/cpu-scaling-error.jpg[/IMG]

---

### Post by typhoon_tip on 2012-11-16
This is surely controlled by the BIOS. You should check the BIOS settings in regards to performance, when on AC mode, there should be something like "balanced mode" (allowing the scaling, and controlling the noise of the fan), probably now is set to max performance when on AC mode.

---

### Post by hani270 on 2012-11-20
there are no many options in my SETUP menu , i have tried to disable (intel speedstep)
and have errors such as:
> 
xxx@xxx-121Q-N4030:~$ indicator-cpufreq
Traceback (most recent call last):
  File "/usr/bin/indicator-cpufreq", line 81, in <module>
    ind = MyIndicator()
  File "/usr/lib/python2.7/dist-packages/indicator_cpufreq/indicator.py", line 95, in __init__
    self.update_ui()
  File "/usr/lib/python2.7/dist-packages/indicator_cpufreq/indicator.py", line 106, in update_ui
    fmin, fmax, governor = cpufreq.get_policy(self.cpus[0])
  File "/usr/lib/python2.7/dist-packages/indicator_cpufreq/cpufreq.py", line 143, in get_policy
    policy = (p.contents.min, p.contents.max, p.contents.governor)
ValueError: NULL pointer access
> 
xxx@xxx-121Q-N4030:~$ cpufreq-info
cpufrequtils 008: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to [EMAIL="cpufreq@vger.kernel.org"]cpufreq@vger.kernel.org[/EMAIL], please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 0.00 ms.
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 0.00 ms.
analyzing CPU 2:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 0.00 ms.
analyzing CPU 3:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 0.00 ms.

another point, if it controlled by bios, why windows 7 working fine and ubuntu 10.04 before

maybe ubuntu 12.10 cannot scaling my processors correctly, but why in AC adapter only
 
now i can scale processors by "cpufreq-set" command to lowest, but the fan is still out loud and laptop very hot and it returns automaticly to maximum after a while

this subject ([http://www.pantz.org/software/cpufreq/usingcpufreqonlinux.html](http://www.pantz.org/software/cpufreq/usingcpufreqonlinux.html)) maybe talking about my problem, but my processor is not exists between the lines

-----

UPDATE:: i have tested "indicator-cpufreq" on ubuntu 12.04 in same laptop and it working fine, i'll be glad if can solve the problem for 12.10

---

