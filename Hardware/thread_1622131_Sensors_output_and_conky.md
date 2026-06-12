---
title: "Sensors output and conky"
date: 2010-11-15
forum: Hardware
---

### Post by Jacdeb6009 on 2010-11-15
Hi there,

I have just completed a new build.  The spec is as follows:

Motherboard : Gigabyte GA-H55M-USB3
CPU : Intel i3 540

The rest of the hardware is not important to the problem that I have.

I have installed Lucid and everything works well.  Sound, network, graphics / video and so on.

I have just lost a laptop due to overheating problems (long story) and am therefore quite sensitive about this issue.

I installed lm-sensors and have gotten it working, however, I cannot determine what the output (specifically temperatures) refers to.  I have now spent quite a bit of time reading various forums, but am no closer to what this all means.

Below is the output from "sensors"

```
it8720-isa-0290
Adapter: ISA adapter
in0:         +0.98 V  (min =  +0.00 V, max =  +4.08 V)   
in1:         +1.57 V  (min =  +0.00 V, max =  +4.08 V)   
in2:         +3.39 V  (min =  +0.00 V, max =  +4.08 V)   
in3:         +2.98 V  (min =  +0.00 V, max =  +4.08 V)   
in4:         +0.00 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in5:         +3.17 V  (min =  +0.00 V, max =  +4.08 V)   
in6:         +0.00 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in7:         +3.01 V  (min =  +0.00 V, max =  +4.08 V)   
Vbat:        +3.15 V
fan1:        981 RPM  (min =    0 RPM)
fan2:        793 RPM  (min =    0 RPM)
temp1:       +38.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:       +25.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp3:       +21.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
cpu0_vid:   +0.000 V

```More specifically, as there is no graphics card installed (using the built GPU of the CPU), how can I see the temperatures of the two cores, or which of the above are the two core temperatures?

Anyone have any idea?

Also, how do I get this information to display in Conky, the conky file from the laptop does not do the trick on the desktop machine (I sort of understand why, but not how to fix it... :) )

Cheers!

---

