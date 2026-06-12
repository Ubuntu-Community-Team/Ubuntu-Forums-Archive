---
title: "CPU Fan Speed Detector Failing - CPU frequency doesn't change. Ubuntu 11.04"
date: 2011-10-18
forum: Hardware
---

### Post by nolace on 2011-10-18
Dear all,

This is my first post on the forums. I thought my problem is half hardware, half software so I decided to posted it here. 

I have Dell Vostro 1500 with 2.5Ghz Dual Core cpu and Nvidia 8600M GT, 3GB Ram.


While ago, my cpu fan stopped working. I opened my laptop, took it out, and checked it with an external source and it was ok. After hours of motherboard checking, I found out that the Pin for speed detection and control was damaged and not working. 

I smoldered the fan to a usb controller voltage/ground pin and added manual key and some diodes for high/low speed.

After that every time that my cpu temperature rises over 51 degree, the cpu frequency locks itself on the lower possible frequency which is 800Mhz. This only happens on Linux, on windows I use a program that has the power to force it up.

I first faced this problem on Ubuntu 10.04, I searched a lot and found an exact similar well-known bug in which this behavior was observered (cpu locking on temperature higher than 51). But all those computers had normal working Fans. It was stated that the bug is not there anymore in the new versions. I upgraded to 10.10 and then to 11.04 and I still have the problem.

Does anyone know whether there is a way to some how completely deactivate this defensive mechanism? I would even go for Kernel recompilation if required but I need some clues to start.

I also apologize if I posted this post on a wrong location. Inform me to relocate it if required.

Thank you.

---

### Post by 2F4U on 2011-10-18
Have you already tried to use a different governor such as performance instead of ondemand?

---

### Post by diasf on 2011-10-18
Use cpufreqd and create your own .conf file...

---

### Post by nolace on 2011-10-18
I have tried every possible method of forcing cpu to the specified frequency, either manual or dynamic via governors.

The command that I use is 

sudo cpufreq-selector -c 0 -f 2500000
sudo cpufreq-selector -c 1 -f 2500000

to force both cpus to the specificed frequency but it doesn't work

I also tried to use cpufreqd but the daemon doesn't respond anymore after cpu lock

When I also check the cpu scaling information in

cat /sys/devices/system/cpu/cpu0/cpufreq/ 

both scale max and scale min are 800000.

In order to be totally sure I will install a new linux from scratch and post the results.

---

### Post by nolace on 2011-10-18
Update!

I installed new clean version of 11.10.

I installed the cpufreqd and successfully put a config file ignoring any temperature and putting a high performance profile.

Result: When the temperature goes over 51, the cpu frequency again locks at 800Mhz. I restarted the daemon several times, but it is a no go. 

Any other suggestion or maybe tweaks for config file?

The config file I used is 
I both used 100% and 2500000 for the min and max frequency.
```



[General]
pidfile=/var/run/cpufreqd.pid
poll_interval=2
verbosity=7
enable_remote=1
remote_group=root
[/General]

[Profile]
name=Performance High
minfreq=2500000
maxfreq=2500000
policy=performance
#exec_post=echo 8 > /proc/acpi/sony/brightness
[/Profile]


##
# Basic states
##
# when AC use performance mode
[Rule]
name=AC Rule
ac=on                    # (on/off)
profile=Performance High
[/Rule]
 
# stay in performance mode for the first minutes
[Rule]
name=AC Off - High Power
ac=off                   # (on/off)
profile=Performance High
[/Rule]





```

---

