---
title: "CPU policy governor"
date: 2009-11-11
forum: Hardware
---

### Post by ego1 on 2009-11-11
My cpufreq was not activate by default, and researching I found this doc

[http://technowizah.com/2007/01/debian-how-to-cpu-frequency-management.html](http://technowizah.com/2007/01/debian-how-to-cpu-frequency-management.html)

I could load the frequency driver, but **I couldn't the CPU policy governor because don't exist.**
I am running ubuntu 9.10 i386 on HP/Compaq nx9600

$ dmesg | grep ubuntu
[    0.000000] Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
$ lsmod | grep p4
p4_clockmod             4164  0
$ cpufreq-info 
cpufrequtils 005: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]cpufreq@vger.kernel.org[/email], please.
analyzing CPU 0:
  driver: p4-clockmod
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 375 MHz - 3.00 GHz
  available frequency steps: 375 MHz, 750 MHz, 1.13 GHz, 1.50 GHz, 1.88 GHz, 2.25 GHz, 2.63 GHz, 3.00 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 375 MHz and 3.00 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 3.00 GHz.
  cpufreq stats: 375 MHz:0.00%, 750 MHz:0.00%, 1.13 GHz:0.00%, 1.50 GHz:0.00%, 1.88 GHz:0.00%, 2.25 GHz:0.00%, 2.63 GHz:0.00%, 3.00 GHz:0.00%
$ sudo modprobe cpufreq_conservative
[sudo] password for user: 
FATAL: Module cpufreq_conservative not found.
$ ls /lib/modules/2.6.21.7/kernel/drivers/cpufreq/ 
ls: cannot access /lib/modules/2.6.21.7/kernel/drivers/cpufreq/: No such file or directory

The cpu policy governor modules are not present in my system, and don't know how add them. Thanks in advance.

---

### Post by bornagainpenguin on 2010-04-09
Friendly bump.

---

### Post by moetunes on 2010-04-09
afaik that needs to be enabled when the kernel is built - what does
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
return?

---

### Post by wojox on 2010-04-09
[Something like this?]("http://ubuntuforums.org/showthread.php?p=9051089#post9051089")

---

### Post by c0rrupt0r on 2010-12-02
Thank you wojox that worked for me on that link you provided, I am using ubuntu 10.10 Maverick and was having all the same issues and this solved every thing for me. :D

---

### Post by ego1 on 2010-12-02
This issue was fixed in some kernel update that came before.
Thanks people.

---

