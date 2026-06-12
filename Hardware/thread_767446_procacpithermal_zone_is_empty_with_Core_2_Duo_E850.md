---
title: "/proc/acpi/thermal_zone is empty with Core 2 Duo E8500"
date: 2008-04-25
forum: Hardware
---

### Post by 23meg on 2008-04-25
With a Core 2 Duo E8500 (3.16GHz) running on a Gigabyte X38T-DQ6 motherboard with Hardy (64-bit), no temperature information is available under /proc/acpi/thermal_zone. 

```

$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     E8500  @ 3.16GHz
stepping	: 6
cpu MHz		: 2000.000
cache size	: 6144 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm
bogomips	: 6336.64
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     E8500  @ 3.16GHz
stepping	: 6
cpu MHz		: 2000.000
cache size	: 6144 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm
bogomips	: 6332.59
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

```

lm-sensors prompted me to load the "it87" module, and shows the following (weird) figures afterwards:

```
$ sensors
it8718-isa-0290
Adapter: ISA adapter
in0:         +1.02 V  (min =  +0.00 V, max =  +4.08 V)
in1:         +1.73 V  (min =  +0.00 V, max =  +4.08 V)
in2:         +3.30 V  (min =  +0.00 V, max =  +4.08 V)
in3:         +2.98 V  (min =  +0.00 V, max =  +4.08 V)
in4:         +0.30 V  (min =  +0.00 V, max =  +4.08 V)
in5:         +0.46 V  (min =  +0.00 V, max =  +4.08 V)
in6:         +0.06 V  (min =  +0.00 V, max =  +4.08 V)
in7:         +3.10 V  (min =  +0.00 V, max =  +4.08 V)
in8:         +3.10 V
fan1:       1214 RPM  (min =   10 RPM)
fan2:          0 RPM  (min =   10 RPM)
fan3:       1144 RPM  (min =   10 RPM)
fan4:          0 RPM  (min =    0 RPM)
temp1:       +27.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = transistor
temp2:       +23.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:        -2.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = transistor
cpu0_vid:   +2.050 V
$ sensors
it8718-isa-0290
Adapter: ISA adapter
in0:         +1.02 V  (min =  +0.00 V, max =  +4.08 V)
in1:         +1.73 V  (min =  +0.00 V, max =  +4.08 V)
in2:         +3.30 V  (min =  +0.00 V, max =  +4.08 V)
in3:         +2.98 V  (min =  +0.00 V, max =  +4.08 V)
in4:         +0.30 V  (min =  +0.00 V, max =  +4.08 V)
in5:         +0.46 V  (min =  +0.00 V, max =  +4.08 V)
in6:         +0.06 V  (min =  +0.00 V, max =  +4.08 V)
in7:         +3.10 V  (min =  +0.00 V, max =  +4.08 V)
in8:         +3.10 V
fan1:       1214 RPM  (min =   10 RPM)
fan2:          0 RPM  (min =   10 RPM)
fan3:       1144 RPM  (min =   10 RPM)
fan4:          0 RPM  (min =    0 RPM)
temp1:       +27.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = transistor
temp2:       +23.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:        -2.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = transistor
cpu0_vid:   +2.050 V

```

Suggestions?

---

### Post by 23meg on 2008-04-25
Some searches I've done seem to indicate I need the "coretemp" kernel module, but I get this when I try to modprobe it:

```

$ sudo modprobe coretemp
FATAL: Error inserting coretemp (/lib/modules/2.6.24-16-generic/kernel/drivers/hwmon/coretemp.ko): No such device

```

---

### Post by sdennie on 2008-04-26
I think that abnormalities in /proc/acpi are usually caused by an incompatible (or buggy) BIOS.  You could see if there is a BIOS update available for your machine or, failing that, compile a custom DSDT and see if that helps (it's not trivial to do but, googling for "custom dsdt linux" should get you started in the right direction).

---

### Post by Da_Coynul on 2008-05-13
I am having the same problem with my E8400 on a Gigabyte GA-G33M-S2L.  I think it might be a problem with the coretemp module. 

sudo modprobe cortemp results in this output from dmesg:

[  157.942643] coretemp: Unknown CPU model 17
[  157.942646] coretemp: Unknown CPU model 17

---

### Post by pedrogfrancisco on 2010-04-27
coretemp should be modprobable.

Anyway, here is the new palce:
> cat /sys/class/hwmon/hwmon0/device/temp1_input
cat /sys/class/hwmon/hwmon1/device/temp1_input

Apparently [/proc/acpi/ is being deprecated]("http://acpi.sourceforge.net/documentation/sleep.html").

---

