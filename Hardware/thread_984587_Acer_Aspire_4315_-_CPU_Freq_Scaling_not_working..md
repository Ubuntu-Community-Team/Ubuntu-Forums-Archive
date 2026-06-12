---
title: "Acer Aspire 4315 - CPU Freq Scaling not working."
date: 2008-11-16
forum: Hardware
---

### Post by luddite666 on 2008-11-16
Hi all,

My CPU Frequency Scaling Monitor says that CPU Frequency Scaling is unsupported on this CPU. I have seen that others with Celeron M 530's and 540's can get frequncy scaling to work but i have had no such luck.

I have tried these threads and nada.

[http://ubuntuforums.org/showthread.php?t=248867](http://ubuntuforums.org/showthread.php?t=248867)
[http://www.uluga.ubuntuforums.org/showthread.php?t=431331](http://www.uluga.ubuntuforums.org/showthread.php?t=431331)
[http://www.howtoforge.com/cpu_frequency_scaling_ubuntu](http://www.howtoforge.com/cpu_frequency_scaling_ubuntu)
CPU Specs: Celeron M 540 1.86 GHz

I have done :	

luddite@ACER:~$ sudo modprobe p4_clockmod
[sudo] password for luddite: 
FATAL: Error inserting p4_clockmod (/lib/modules/2.6.27-7-generic/kernel/arch/x86/kernel/cpu/cpufreq/p4-clockmod.ko): No such device
luddite@ACER:~$ 
luddite@ACER:~$ cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
luddite@ACER:~$ 
luddite@ACER:~$ cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU

I know others running 8.10 and celeron M's can get the scaling working.

I have tried uninstalling powernod cpudyn and installing the other ones.

Currently i have this installed:

cpufrequtils
cpufreqd
kpowersave
powertop
lipowersave10
licpufreq0
laptop-mode-tools
powermgmnt-base
acpid

Thanks.
luddite

---

### Post by benander on 2009-01-20
Hi I have the exact same problem with my Acer Aspire 5315 running 8.10.  I have tried: powernowd, powersaved, emifreq-applet, but none of them will work since I can't load the module.  

Did you find a solution or figure out why we don't have /cpufreq  in our cpu directory?

---

### Post by luddite666 on 2009-02-23
Nope still looking into this every so often.

---

### Post by ngsupb on 2009-11-23
guys, do you know what to do? 

I have the same problem :(

---

### Post by benem3000 on 2010-06-03
Try this...

[http://ubuntuforums.org/showthread.php?t=190921](http://ubuntuforums.org/showthread.php?t=190921)

Worked for me. :)
Hope it does for you.

---

