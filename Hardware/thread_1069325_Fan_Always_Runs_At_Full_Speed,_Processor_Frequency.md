---
title: "Fan Always Runs At Full Speed, Processor Frequency Scaling Doesn't Work"
date: 2009-02-13
forum: Hardware
---

### Post by gnoob on 2009-02-13
Hi all,
I have a problem. The fan on my desktop (an old Sony) running 8.04 will not stop running at full speed and it is very loud and annoying. In probably related news, my cpu constantly runs at 1.2Ghz (full speed) and says it does not support frequency scaling.

I am pretty sure the hardware itself is not the problem because I have a dual boot with Xp and the fan is much quieter in Xp.  In Xp the system manager shows the processor changing loads.

I have spent a while looking around and none of the suggestions have helped. I actually dont care if the processor continues to run at 1.2Ghz, I really just want the fan to be quieter.

Here is some info which might help:
```
$ cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU

```

```
$  cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 11
model name	: Intel(R) Celeron(TM) CPU                1200MHz
stepping	: 1
cpu MHz		: 1202.787
cache size	: 256 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
bogomips	: 2407.53
clflush size	: 32

```

```
$ sensors
w83627hf-isa-0290
Adapter: ISA adapter
VCore 1:     +1.42 V  (min =  +1.25 V, max =  +1.66 V)
VCore 2:     +2.46 V  (min =  +1.25 V, max =  +1.66 V)
+3.3V:       +3.26 V  (min =  +2.82 V, max =  +3.79 V)
+5V:         +5.03 V  (min =  +6.72 V, max =  +6.80 V)
+12V:       +11.86 V  (min = +11.31 V, max =  +5.23 V)
-12V:       -12.61 V  (min =  +0.47 V, max =  +4.33 V)
-5V:         -5.15 V  (min =  +1.79 V, max =  -5.75 V)
V5SB:        +5.43 V  (min =  +5.05 V, max =  +5.59 V)
VBat:        +0.51 V  (min =  +2.83 V, max =  +4.05 V)
fan1:       5273 RPM  (min = 3571 RPM, div = 2)
fan2:       2689 RPM  (min = 21093 RPM, div = 2)
fan3:          0 RPM  (min = 6958 RPM, div = 2)
temp1:       -45.0°C  (high = -37.0°C, hyst = +45.0°C)  sensor = thermistor
temp2:       +32.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
temp3:       +29.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
cpu0_vid:   +1.450 V
beep_enable:enabled

```

```
$ sudo modprobe acpi_cpufreq
[sudo] password for ****: 
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.24-23-generic/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko): No such device

```

Any help would be greatly appreciated.
AKS

---

### Post by luxorvan on 2009-02-13
On my socket 754 sempron I had to switch the scaling package in synaptic theres two choices cpudyn and powernow. Try switching between the two, you shouldn't have to restart but you will need to remove the cpu frequency monitor from the panel then re-add it after installing each one to see if either works. It worked for me, however for my socket 468 p4 just isn't supported!

---

### Post by gnoob on 2009-02-14
Thanks for the advice.
Switching between powernowd and the other didn't help though. Im beginning to think my old Celeron just does not support scaling.  although it worked on Xp...

---

### Post by gnoob on 2009-02-17
bump. Does anyone think maybe a new quieter fan would help? I am using the factory installed fan.

---

### Post by gnoob on 2009-02-26
bump. replacing the fan is not an option. there is only the cpu fan and it is hidden behind the power supply case which is riveted in. stupid sony.

---

