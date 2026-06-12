---
title: "no cpu temperature sensor on asrock 990fx extreme9 amd fx-9590 cpu"
date: 2015-10-22
forum: Hardware
---

### Post by mike4ubuntu on 2015-10-22
I just built out a new system (Ubuntu 14.04.1) with an AMD CPU FX-9590 which is probably currently one of the fastest amd cpu's.  You can see how it stacks up against Intel and other AMD cpus here:

[http://www.cpubenchmark.net/high_end_cpus.html]("http://www.cpubenchmark.net/high_end_cpus.html")

Wow, is it a power hog at 220W.  AMD recommends at least a 1000W power supply.  It also gets really hot.  It's tricky to pair up with motherboards because a lot of the AMD3+ socket motherboards can't handle the power requirements.  So I chose an ASRock 990fx extreme9, which seems pretty nice.  I'm concerned that the cooler may not cool enough when running a heavy cpu intensive load.  I have a Cooler Master V8 GTS cooler installed now, but I'm thinking about switching to a Cooler Master closed loop liquid cooler.  The problem I'm having is that I can't monitor the cpu temperature.  I've installed psensor and lm-sensors but the sensors-detect won't detect the cpu temperature monitor.  It seems to get the video GPU, Motherboard temperature, fan speeds, but not the cpu temperature itself.  Has anybody gotten that to work for this cpu motherboard combination?

---

### Post by Yellow Pasque on 2015-10-22
> Wow, is it a power hog at 220W
You should have done your homework **before** you bought it. Anyway...
Please show output of:
```
uname -a
sudo modprobe -v k10temp
sensors
```

---

### Post by Yellow Pasque on 2015-10-22
Also, if the temperature reported does not seem accurate, see: [http://ubuntuforums.org/showthread.php?t=2246208](http://ubuntuforums.org/showthread.php?t=2246208)

---

### Post by QIII on 2015-10-22
The k10temp module should already be loaded if you installed lm-sensors and answered yes to all of the questions.

But go ahead and modprobe it as Temüjin suggests and give us the output of 

```
sensors
```

As an add-on to the thread Temüjin indicated, please also see [this article]("http://theleftcoastgeek.net/index.php/general-interest/5-lm-sensors-conky-and-amd-temperatures") on my blog for what I now think may be a better solution that just adding 10 degrees to the k10temp reading.  If you don't use conky, you can just run the script from the command line on occasion.

---

### Post by mike4ubuntu on 2015-10-23
> You should have done your homework before you bought itYeah, I normally stay away from AMD cpu's anyway, but it was much cheaper than a comparable benchmark power Intel cpu (that's the trap).  However, I had a 1000W ps already, so I thought what the heck.  Of course, then I find I have to spend more $$ on a cpu cooler too.  so yeah, not worth in the long run, probably.  However, it does function ok (mostly), and I will say it is pretty powerful.  Although, I'm having problems with the integrated sound as well, but with the external sound cards I use, that may not be a problem.  However, I haven't tried to tackle the sound issue yet.

I can see that the cpu temperature in the BIOS HW monitor consistently runs about 46 C (light cpu load) and the mobo temperature is about 24 C, so I'm guessing TEMP 1 is the mobo temp.  I just noticed the CPUIN temp is about 31 C so I'm guessing that is really not the CPU temp, and the psensors indicator app doesn't report that anyway.  Although, maybe I can add that to the indicator config.

I checked out "How to check core temp cpu amd-9590" thread mentioned above, but after I run sensors-detect, I don't see anything like "coretemp-isa-0000".  Although, that thread also seems to suggest that AMD CPUs are for crap when trying to instrument CPU temp.


```

uname -a
Linux studio4 3.19.0-31-generic #36~14.04.1-Ubuntu SMP Thu Oct 8 10:21:08 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

```

$ sudo modprobe -v k10temp
$ sensors
nouveau-pci-0500
Adapter: PCI adapter
temp1:        +24.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

nct6776-isa-0290
Adapter: ISA adapter
Vcore:          +1.50 V  (min =  +0.00 V, max =  +1.74 V)
in1:            +1.85 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
AVCC:           +3.30 V  (min =  +2.98 V, max =  +3.63 V)
+3.3V:          +3.28 V  (min =  +2.98 V, max =  +3.63 V)
in4:            +1.38 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in5:            +1.69 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in6:            +0.63 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
3VSB:           +3.46 V  (min =  +2.98 V, max =  +3.63 V)
Vbat:           +3.38 V  (min =  +2.70 V, max =  +3.63 V)
fan1:          1422 RPM  (min =    0 RPM)
fan2:             0 RPM  (min =    0 RPM)
fan3:             0 RPM  (min =    0 RPM)
fan4:             0 RPM  (min =    0 RPM)
fan5:             0 RPM  (min =    0 RPM)
SYSTIN:         +28.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPUTIN:         +31.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
AUXTIN:          +6.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
PCH_CHIP_TEMP:   +0.0°C  
PCH_CPU_TEMP:    +0.0°C  
PCH_MCH_TEMP:    +0.0°C  
intrusion0:    ALARM
intrusion1:    ALARM
beep_enable:   disabled

fam15h_power-pci-00c4
Adapter: PCI adapter
power1:      141.39 W  (crit = 219.76 W)

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +11.0°C  (high = +70.0°C)
                       (crit = +70.0°C, hyst = +67.0°C)


```

---

### Post by QIII on 2015-10-23
At the bottom of the sensors output, k10temp is your reported CPU temp.  If you read the blog article indicated, I discuss the temperature reading.  It's a pseudo temperature used to control the HSF on your mobo, not a physical temperature.

The temp1 reading is likely the socket temp.

---

### Post by mike4ubuntu on 2015-10-23
yeah, I see.  Looks like there's not much that can be done except monitor temp1.  Oh, well, thanks for your help anyway.  when I monitor in the BIOS it seems that the cooler does a pretty good, but I'm not sure what's going to happen when I put a load on it.  I guess if the cpu burns up, it burns up and that's it.  As long as it doesn't burn the house down in the process :icon_frown:

---

