---
title: "CPU Overheating?"
date: 2011-03-30
forum: Hardware
---

### Post by josefnpat on 2011-03-30
Hey guys, i've been getting a lot of this on on the other tty's:

```
Temperature above threshold, cpu clock throttled (total events = 14961)
```

and not only that, at some points, my machine just shuts down, and refuses to start back up for a while. Makes me think my cpu-fan is croaking. I'm running an intel i920.

A quick sensors shows the following:

```
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +94.0°C  (high = +80.0°C, crit = +100.0°C)  ALARM  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +93.0°C  (high = +80.0°C, crit = +100.0°C)  ALARM  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +97.0°C  (high = +80.0°C, crit = +100.0°C)  ALARM  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +91.0°C  (high = +80.0°C, crit = +100.0°C)  ALARM  

it8720-isa-0290
Adapter: ISA adapter
in0:         +0.91 V  (min =  +0.00 V, max =  +4.08 V)   
in1:         +1.54 V  (min =  +0.00 V, max =  +4.08 V)   
in2:         +3.38 V  (min =  +0.00 V, max =  +4.08 V)   
in3:         +3.02 V  (min =  +0.00 V, max =  +4.08 V)   
in4:         +0.66 V  (min =  +0.00 V, max =  +4.08 V)   
in5:         +3.06 V  (min =  +0.00 V, max =  +4.08 V)   
in6:         +0.34 V  (min =  +0.00 V, max =  +4.08 V)   
in7:         +3.01 V  (min =  +0.00 V, max =  +4.08 V)   
Vbat:        +3.25 V
fan1:       1962 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
fan4:          0 RPM  (min =    0 RPM)
temp1:       +36.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:       +95.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:       +59.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
cpu0_vid:   +0.000 V
```

Any ideas?

Thanks in advance!

---

### Post by josefnpat on 2011-03-31
Well, looking back at this thread, this seriously must look like I'm trolling. To be perfectly honest, I didn't know what this screen was supposed to look like. I ran sensors at my machine at work:
```
max1617-i2c-8-18
Adapter: SMBus I801 adapter at 3000
temp1:        +0.0°C  (low  = +16.0°C, high = +66.0°C)  
temp2:        +0.0°C  (low  =  +0.0°C, high =  +0.0°C)  

max1617-i2c-8-1a
Adapter: SMBus I801 adapter at 3000
temp1:        +0.0°C  (low  = +16.0°C, high = +66.0°C)  
temp2:        +0.0°C  (low  =  +0.0°C, high =  +0.0°C)  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +39.0°C  (high = +87.0°C, crit = +97.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 0:      +37.0°C  (high = +87.0°C, crit = +97.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 1:      +37.0°C  (high = +87.0°C, crit = +97.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 1:      +35.0°C  (high = +87.0°C, crit = +97.0°C)  

coretemp-isa-0004
Adapter: ISA adapter
Core 2:      +39.0°C  (high = +87.0°C, crit = +97.0°C)  

coretemp-isa-0005
Adapter: ISA adapter
Core 2:      +38.0°C  (high = +87.0°C, crit = +97.0°C)  

coretemp-isa-0006
Adapter: ISA adapter
Core 3:      +37.0°C  (high = +87.0°C, crit = +97.0°C)  

coretemp-isa-0007
Adapter: ISA adapter
Core 3:      +36.0°C  (high = +87.0°C, crit = +97.0°C)
```

I think the first thing that tipped me off was the fact that the word "ALARM" is missing. I've shut down my machine at home, and am planning on looking at the cpu-fan.

If anyone has a reason, other than it being the cpu fan, I'd be more than interested to hear.

---

### Post by TBABill on 2011-03-31
Those temps are far higher than I have ever allowed my machine to knowingly get. Have you given that thing a thorough internal cleaning to be sure there are no duct obstructions from your fan to the inlets and outlets? And have you checked heatsinks to make sure they are securely in place?
 
If you have done those things, then something is running at max speed constantly to generate that kind of heat. Most likely CPU and GPU. Does the system run sluggishly before getting to those temps?
 
CPUFREQ should be set already by default within a current system. To check what setting your machine is at, run ```
cpufreq-info
``` and it will tell you in quotes ("")  what each CPU is set to. Ideally they should all be set to "ondemand", which scales to about half speed until system demand is high enough to require more. If it's not set to ondemand, just ```
sudo cpufreq-set --governor ondemand
```
 
Do you have a proprietary driver for your graphics card available? That should help a great deal as well.

---

### Post by Yellow Pasque on 2011-03-31
If the sensor is accurate, it's definitely time to dust the vents and possibly reattach the heatsink if that doesn't help. I've seen laptops with cheap thermal pads that get progressively worse and start melting even more with overheating. 90C is very alarming. If you keep doing that, you'll soon be in the market for an RMA and/or new CPU.

Oh, and it's not a solution, but use Flash-aid extension to avoid Flash video, as watching video directly through the Flash plugin is very inefficient and uses a lot of CPU.

---

### Post by josefnpat on 2011-03-31
Thank you guys very much for the helpful replies. I'm going to check for dirt/obstructions and such later tonight when I get home.

@TBABill
I'm pretty sure it's already set to ondemand, but I'll check when I get home. Thank you very much, I wouldn't have thought of this otherwise.

@Temüjin

I'm going to try that flash-aid extension. Flash always seems to be a biggie.

---

### Post by josefnpat on 2011-04-01
Well, I cleaned off the CPU etc, and when not running CPU intensive stuff it dropped down to high seventies. Then I went and throttled the CPU in the bios, and it doesn't go above 60 degC now.

Thanks guys!

---

