---
title: "speedstep / acpi not working, fan spinng at 100% all time"
date: 2009-03-28
forum: Hardware
---

### Post by StuffedLion on 2009-03-28
Hi,

I just installed 9.04 beta on my Computer (fresh install).

It is all running fine but speedstep is not working (i.e. my CPU is running at 100% all the time) and it is loud since my fans spin all at 100% instead of beeing tuned down by the mainboard (like they do in windows). It seems to me like if the whole acpi is not working like it should...

I tried to add the gnome panel cpufreq-applet to control the cpu clock states. And I got an error message, telling me that my computer would not support it.

My hardware: intel E6750 @ 3.2Ghz | Gigabyte GA-G33M-DS2R | 4x 1024MB A-DATA Vitesta Extreme Edition | GeForce 8800GTS 512 | SATA: Samsung Spinpoint F1 750GB | SATA: Samsung SpinPoint T166 500GB | eSATA: Samsung SpinPoint T166 500GB | eSATA: Hitachi Travelstar 5K160 160GB | case: Asus TM-210 | Seasonic S12II 430W |


I tried to load the kernel modules:
```

bjoern@UbuntuLion:~$ sudo modprobe acpi-cpufreq
FATAL: Module acpi_cpufreq not found.
bjoern@UbuntuLion:~$ sudo modprobe p4_clockmod
FATAL: Error inserting p4_clockmod (/lib/modules/2.6.28-11-generic/kernel/arch/x86/kernel/cpu/cpufreq/p4-clockmod.ko): No such device
bjoern@UbuntuLion:~$ sudo modprobe  speedstep-centrino
[sudo] password for bjoern: 
FATAL: Module speedstep_centrino not found.
bjoern@UbuntuLion:~$ sudo modprobe speedstep-ich
FATAL: Module speedstep_ich not found.
```

I have no idea whats wrong. maybe the whole acpi is not working? At least I can not find acpi in the bootloader:

```
bjoern@UbuntuLion:~$ grep -i acpi /boot/grub/menu.lst
bjoern@UbuntuLion:~$ cat /proc/cmdline 
root=/dev/mapper/rootLVM-root ro quiet splash 

```

What can I do? How can I get speestep to work and my fans quiet? How can I find out if acpi is working correctly? how can I see fanspeed and things like that and how can I controll my CPU fequ?

thanks!!
lion

cat from the acpi files from my cpu:
```
root@UbuntuLion:/proc/acpi/processor/CPU1# cat info
processor id:            1
acpi id:                 1
bus mastering control:   no
power management:        no
throttling control:      yes
limit interface:         yes
root@UbuntuLion:/proc/acpi/processor/CPU1# cat limit
active limit:            P0:T0
user limit:              P0:T0
thermal limit:           P0:T0
root@UbuntuLion:/proc/acpi/processor/CPU1# cat power
active state:            C0
max_cstate:              C8
bus master activity:     00000000
maximum allowed latency: 2000000000 usec
states:
    C1:                  type[C1] promotion[--] demotion[--] latency[000] usage[00000000] duration[00000000000000000000]
root@UbuntuLion:/proc/acpi/processor/CPU1# cat throttling 
state count:             8
active state:            T0
state available: T0 to T7
states:
   *T0:                  100%
    T1:                  87%
    T2:                  75%
    T3:                  62%
    T4:                  50%
    T5:                  37%
    T6:                  25%
    T7:                  12%

```

---

### Post by StuffedLion on 2009-03-29
Hi,

I tried some other things, but I have no idea how to proceed now and desperatly need a working speedstep (computer is running almost 24/7 and is way to energy consuming and loud now).

 * I bootem from 8.10 live CD to check if the 9.04 beta causes the problem. same there.

 * I booted from openSuse 11.1 live DCD (gnome) - same problem there.

 * I tried powernowd - not working:  
```
* Starting powernowd...                                                         
* CPU frequency scaling not supported...      
```

 * I checked acpi status (acpi not found):
```
watch -n 1 acpi -V

Every 1,0s: acpi -V

sh: acpi: not found
```

* I tried intels PowerTOP (cant find acpi infos):
```
Detailed C-state information is not P-states (frequencies)
no ACPI power usage estimate available

```

 * I checked CPU information, there is no entry in CPU power managment:
```

watch -n 1 cat /proc/cpuinfo 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz
stepping        : 11
cpu MHz         : 3199.972
cache size      : 4096 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov
pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant
_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx smx est tm2 ss
se3 cx16 xtpr pdcm lahf_lm tpr_shadow vnmi flexpriority
bogomips        : 6399.94
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:
```

 * I added the bootoption acpi=force, same problem.

 * I double checked my BIOS options - everything related to thermal monitoring and frequency is enabled:

```
 
      CPU Enhanced Halt (C1E) Enabled
      CPU Thermal Monitor 2 Enabled
      CPU EIST Function Enabled
```

Guys... I have no idea why it is not working and I am not very experienced with Linux either. Right now I am just blindly guessing. Please please please give me a hand with this... :)

Thank you!

Best
Lion

---

### Post by StuffedLion on 2009-04-08
Just in case someone finds this: the problem was that I overclocked my cpu. As soon as I switched back to the standrad speed, speedstep would work again.

Is someone out there with a similar problem? or is someone out there who could actually overclock and still use intels speedstep in ubuntu/linux?

It is kind of wired that it works w/o any problems in windows but not at all in Linux.

best
Lion

---

