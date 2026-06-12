---
title: "lm_sensors &amp; ASUS M2NPV-VM"
date: 2007-05-29
forum: Hardware &amp; Laptops
---

### Post by zkab on 2007-05-29
My MB is ASUS M2NPV-VM with AMD 64 X2 Dual Core Processor 4800+ where I have installed Ubuntu 7.04
In BIOS ACPI APIC support and Q_Fan are enabled

Followed the guidelines how to install lm_sensors and after some struggling my results are below.

What I don't understand in sensor output is:

   - why is Core0/1 displayed with 2 temps
   - what is CPU Temp (=+43°C ... I have a dual core system)
   - why is CPU fan going so fast when core temp is so low
   - what is temp3
   - how do get rid of these displayed ALARMs
   - why is the documentation so bad for lm_sensors

I have been checking all kind of sensor-forums but I am lost ... 

Any help appreciated ...
/zkab 

1) sensors displays:

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +24°C
Core0 Temp:
             +22°C
Core1 Temp:
             +20°C
Core1 Temp:
             +24°C

it8716-isa-0290
Adapter: ISA adapter
VCore:     +1.23 V  (min =  +0.00 V, max =  +4.08 V)   
3.3V:      +3.25 V  (min =  +0.00 V, max =  +4.08 V)   
5V:        +4.73 V  (min =  +0.00 V, max =  +6.85 V)   
12V:      +11.65 V  (min =  +0.00 V, max = +16.32 V)   
5VSB:      +4.62 V  (min =  +0.00 V, max =  +6.85 V)   
VBat:      +2.85 V
CPU_PWM:  1483 RPM  (min = 3245 RPM)                   ALARM
Rear   :   403 RPM  (min = 3245 RPM)                   ALARM
CPU Temp:    +43°C  (low  =    -1°C, high =  +127°C)   sensor = diode   
M/B Temp:    +42°C  (low  =    -1°C, high =  +127°C)   sensor = thermistor   
Temp3:       +25°C  (low  =    -1°C, high =  +127°C)   sensor = thermistor   
VID:      +0.000 V

2) uname -a gives:

Linux 2.6.20-16-generic #2 SMP Wed May 23 01:46:23 UTC 2007 i686 GNU/Linux

3) cat /proc/cpuinfo displays:

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 107
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4800+
stepping        : 1
cpu MHz         : 2505.293
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8legacy ts fid vid ttp tm stc [6]
bogomips        : 5014.83
clflush size    : 64

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 107
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4800+
stepping        : 1
cpu MHz         : 2505.293
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8legacy ts fid vid ttp tm stc [6]
bogomips        : 5010.80
clflush size    : 64

4) /etc/sensors.config looks like:


chip "it8716-*"
#---------------------------------------------------------------------- ZKAB

# Voltages

label  in0  "VCore"
label  in1  "3.3V"
label  in3  "5V"
label  in4  "12V"
label  in7  "5VSB"
label  in8  "VBat"

ignore in2
ignore in5
ignore in6

compute in3  ((6.8/10)+1)*@ , @/((6.8/10)+1)
compute in4  ((30/10)+1)*@  , @/((30/10)+1)
compute in7  ((6.8/10)+1)*@ , @/((6.8/10)+1)
 	
# If vid (nominal CPU voltage) isn't correct, hardcode the correct value
# instead.
#    set in0_min  vid * 0.95
#    set in0_max  vid * 1.05
#    set in2_min  3.3 * 0.95
#    set in2_max  3.3 * 1.05
#    set in3_min    5 * 0.95
#    set in3_max    5 * 1.05
#    set in4_min   12 * 0.95
#    set in4_max   12 * 1.05
#    set in7_min    5 * 0.95
#    set in7_max    5 * 1.05
# The chip does not support in8 min/max
	
# Temperatures
 	
# If you are lucky, the BIOS has set the proper sensor types for you.
# If your temperature readings are completely whacky you probably
# need to change the sensor types. Adujst and uncomment the
# appropriate lines below.
#
# 2 = thermistor; 3 = thermal diode; 0 = unused
#   set sensor1  3
#   set sensor2  3
#   set sensor3  3
 	
# If a given sensor isn't used, you will probably want to ignore it
# as well (see ignore statement right below).
# The CPU sensor can be any of temp1, temp2 or temp3 - it's motherboard
# dependent. Same for the motherboard temperature.
 	
   label  temp1  "CPU Temp"
   label  temp2  "M/B Temp"
   label  temp3  "Temp3"
#   ignore temp3
 	
#   set temp1_over  60
#   set temp1_low   10
#   set temp2_over  50
#   set temp2_low   10
 	
# Fans
 	
# The CPU fan can be any of fan1, fan2 or fan3 - it's motherboard
# dependent. Same for the case fan.
 	
   label  fan1 "CPU_PWM"
   label  fan2 "Rear   "
   ignore fan3
   label  vid "VID"
#   ignore vid
 	
#   set fan1_min 2000
#   set fan2_min 2000
 	
# -------------------------------------------------------------------------------------------------

---

