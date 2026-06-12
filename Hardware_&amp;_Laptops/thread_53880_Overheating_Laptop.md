---
title: "Overheating Laptop"
date: 2005-08-02
forum: Hardware &amp; Laptops
---

### Post by Staesys on 2005-08-02
My Sharp PC-GP22W has been running very hot lately, and the battery life when disconnected is very short (maybe 45 mins). Here's some info for you:

```
root@ubuntu:/home/paul # powernowd start
powernowd: PowerNow Daemon v0.96, (c) 2003-2005 John Clemens
powernowd: Found 1 cpu:  -- 1 thread (or core) per physical cpu
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq: No such file or directory
PowerNowd encountered and error and could not start.
Please make sure that:
 - You are running a v2.6.7 kernel or later
 - That you have sysfs mounted /sys
 - That you have the core cpufreq and cpufreq-userspace
   modules loaded into your kernel
 - That you have the cpufreq driver for your cpu loaded,
   and that it works. (check dmesg for errors)
If all of the above are true, and you still have problems,
please email the author: clemej@alum.rpi.edu
``` 

```
root@ubuntu:/home/paul # cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 2.20GHz
stepping        : 4
cpu MHz         : 2191.586
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm
bogomips        : 4325.37
``` 

```
root@ubuntu:/home/paul # cat /proc/cpufreq
          minimum CPU frequency  -  maximum CPU frequency  -  policy
``` 

DMESG:
```
ACPI: PCI interrupt 0000:00:02.6[C] -> GSI 5 (level, low) -> IRQ 5
ACPI: AC Adapter [AC] (on-line)
ACPI: Battery Slot [BAT0] (battery present)
ACPI: Power Button (FF) [PWRF]
ACPI: Sleep Button (CM) [SBTN]
ACPI: Lid Switch [LID]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
Access to /proc/cpufreq is deprecated and will be removed from (new) 2.6. kernels soon after 2005-01-01
``` 

I also get messages saying that the "P4 clockmod is intentionally disabled"

Can anyone help me with this?

Thanks!

---

### Post by simonjardine on 2005-08-02
[QUOTE=Staesys]My Sharp PC-GP22W has been running very hot lately, and the battery life when disconnected is very short (maybe 45 mins). Here's some info for you:

```
root@ubuntu:/home/paul # powernowd start
powernowd: PowerNow Daemon v0.96, (c) 2003-2005 John Clemens
powernowd: Found 1 cpu:  -- 1 thread (or core) per physical cpu
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq: No such file or directory
PowerNowd encountered and error and could not start.
Please make sure that:
 - You are running a v2.6.7 kernel or later
 - That you have sysfs mounted /sys
 - That you have the core cpufreq and cpufreq-userspace
   modules loaded into your kernel
 - That you have the cpufreq driver for your cpu loaded,
   and that it works. (check dmesg for errors)
If all of the above are true, and you still have problems,
please email the author: clemej@alum.rpi.edu
``` 

```
root@ubuntu:/home/paul # cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 2.20GHz
stepping        : 4
cpu MHz         : 2191.586
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm
bogomips        : 4325.37
``` 

```
root@ubuntu:/home/paul # cat /proc/cpufreq
          minimum CPU frequency  -  maximum CPU frequency  -  policy
``` 

DMESG:
```
ACPI: PCI interrupt 0000:00:02.6[C] -> GSI 5 (level, low) -> IRQ 5
ACPI: AC Adapter [AC] (on-line)
ACPI: Battery Slot [BAT0] (battery present)
ACPI: Power Button (FF) [PWRF]
ACPI: Sleep Button (CM) [SBTN]
ACPI: Lid Switch [LID]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
Access to /proc/cpufreq is deprecated and will be removed from (new) 2.6. kernels soon after 2005-01-01
``` 

I also get messages saying that the "P4 clockmod is intentionally disabled"

Can anyone help me with this?

Thanks![/QUOTE]
 My new Centrino Toshiba runs hot also, battery life is around 1hour,  I downloaded Xfce and have found it alot better than Gnome. 

Thats my 1pence worth.

---

### Post by Staesys on 2005-08-03
Are there any other suggestions?

---

### Post by varunus on 2005-08-03
For me, to get frequency scaling, I had to add p4_clockmod to /etc/modules.  I have a toshiba, so the screen brightness dimmer in fnfxd worked nicely for me too; not sure if sharp has something similar.

Can you post the output of "lsmod" in a terminal?

---

### Post by Staesys on 2005-08-04
I'll try, but when I went to my laptop this morning, it failed to power on, so it may be dead (hope not).

-Paul

---

