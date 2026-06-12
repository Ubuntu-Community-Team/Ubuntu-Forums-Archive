---
title: "Howto disable software temperature protection"
date: 2009-08-18
forum: Hardware
---

### Post by luki.sk on 2009-08-18
How can i disable temperature protection in ubuntu 9.04 ?

My laptop ASUS F3E sometimes shutting down after critical temperatute reached...

from kern log:
Aug  18 15:49:20 luki kernel: [42332.730718] ACPI: Critical trip point
Aug  18 15:49:20 luki kernel: [42332.730737] Critical temperature reached (90 C), shutting down.

cat /proc/acpi/thermal_zone/THRM/trip_points 
critical (S5):           90 C
passive:                 87 C: tc1=2 tc2=10 tsp=100 devices=P001 P002

if my cpu reach 87 C (on playing games .. ), fan is kicked up to full speed, and cpu frequency is set down to 50%...
But sometimes temp reach 90 C and then shutting down.... 

Is possible tuneup trip_points? set crit. temp to 100C or passive temp to 83C or disable this stupid protection ??

On win xp i don`t have this problem....

temp from acpi and sensors in the same time:
acpi -t
     Battery 0: Full, 100%
     Thermal 0: ok, 70.0 degrees C
sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +70.0°C  (crit = +90.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +63.0°C  (high = +85.0°C, crit = +85.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +61.0°C  (high = +85.0°C, crit = +85.0°C)
Why are temperatures from acpi and cores not equals?

other info:
- system is up to date..
uname -a
Linux luki 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 i686 GNU/Linux
cat /proc/cpuinfo 
processor       : 0, 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 Duo CPU     T5250  @ 1.50GHz
stepping        : 13
cpu MHz         : 1000.000
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
apicid          : 0
initial apicid  : 0
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips        : 2992.55
clflush size    : 64
power management

---

