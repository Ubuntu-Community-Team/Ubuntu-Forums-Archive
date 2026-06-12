---
title: "System auto-shutdown whenever dual display is used"
date: 2012-04-04
forum: Hardware
---

### Post by Ang Way Chuang on 2012-04-04
Hi all,
   I'm using Ubuntu 11.10 (this applies to 2nd beta of the upcoming LTS, Fedora 15 and Fedora 16 too). My laptop auto shutdown by itself whenever dual display is used. The syslog prints out the following line:
 Critical temperature reached (100 C), shutting down.
   However, when I monitored the temperature using the following 2 command lines:
watch --interval=1 acpi -t
watch --interval=1 sensors
   The temperature was around 60 C when the system complains about the _critical_ temperature. My laptop is Dell Vostro 3350 and the GPU is Intel Sandy Bridge IGP. This problem is 100% reproducible and is reproducible with or without compositing. Can anyone provide any pointer? Manually setting the fan speed using `i8kfan 2 2` still resulted in reboot. I am getting very desperate because I cannot run any Linux distro on this laptop without getting occasional auto shutdown. I am pretty sure that it is not a hardware issue as I don't have this problem under Windows 7 with dual display.


The following is the output of the sensors program running on my laptop:
acpitz-virtual-0
Adapter: Virtual device
temp1:        +47.5°C  (crit = +99.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +49.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +49.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +44.0°C  (high = +86.0°C, crit = +100.0°C)

i8k-virtual-0
Adapter: Virtual device
Right Fan:   124080 RPM
CPU:          +47.0°C  


Thank you in advance.

---

