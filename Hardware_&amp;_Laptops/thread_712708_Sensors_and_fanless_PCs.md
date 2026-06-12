---
title: "Sensors and fanless PCs"
date: 2008-03-02
forum: Hardware &amp; Laptops
---

### Post by xfred on 2008-03-02
I've just (quite literally) finished putting together a new PC for a mythbuntu box and had some questions about the output when I run sensors.  I'm using passive cooling for the Intel dual core E2200 cpu with a thermalright Ultima-90I heatsink.  With no load I get (room temp around the 20C mark):

```
w83627dhg-isa-0290
Adapter: ISA adapter
VCore:     +1.27 V  (min =  +0.00 V, max =  +1.74 V) 
in1:      +12.25 V  (min =  +6.39 V, max = +11.72 V) ALARM
AVCC:      +3.23 V  (min =  +0.86 V, max =  +2.02 V) ALARM
3VCC:      +3.23 V  (min =  +3.41 V, max =  +3.66 V) ALARM
in4:       +1.34 V  (min =  +2.03 V, max =  +0.76 V) ALARM
in5:       +1.56 V  (min =  +1.62 V, max =  +1.20 V) ALARM
in6:       +4.30 V  (min =  +5.43 V, max =  +4.63 V) ALARM
VSB:       +3.23 V  (min =  +4.08 V, max =  +3.34 V) ALARM
VBAT:      +0.38 V  (min =  +3.01 V, max =  +3.79 V) ALARM
Case Fan: 1950 RPM  (min = 1366 RPM, div = 4)
CPU Fan:     0 RPM  (min = 10546 RPM, div = 128) ALARM
Aux Fan:     0 RPM  (min = 3515 RPM, div = 128) ALARM
fan4:        0 RPM  (min = 10546 RPM, div = 128) ALARM
fan5:        0 RPM  (min = 10546 RPM, div = 128) ALARM
Sys Temp:    +33°C  (high =   +14°C, hyst =   +24°C)   ALARM
CPU Temp:  +22.5°C  (high = +80.0°C, hyst = +75.0°C)  
AUX Temp:  +20.5°C  (high = +80.0°C, hyst = +75.0°C)  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +23°C  (high =   +85°C)                   

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +21°C  (high =   +85°C)
```

after about 10 minutes (EDIT: make that 20 - no change after the first 5 or so anyhow) running two instances of burnP6 (I'm assuming this is the correct one to run for the processor?) in parallel this changes to:

```
w83627dhg-isa-0290
Adapter: ISA adapter
VCore:     +1.34 V  (min =  +0.00 V, max =  +1.74 V) 
in1:      +12.20 V  (min =  +6.39 V, max = +11.72 V) ALARM
AVCC:      +3.23 V  (min =  +0.86 V, max =  +2.02 V) ALARM
3VCC:      +3.23 V  (min =  +3.41 V, max =  +3.66 V) ALARM
in4:       +1.34 V  (min =  +2.03 V, max =  +0.76 V) ALARM
in5:       +1.56 V  (min =  +1.62 V, max =  +1.20 V) ALARM
in6:       +4.28 V  (min =  +5.43 V, max =  +4.63 V) ALARM
VSB:       +3.23 V  (min =  +4.08 V, max =  +3.34 V) ALARM
VBAT:      +0.38 V  (min =  +3.01 V, max =  +3.79 V) ALARM
Case Fan: 1896 RPM  (min = 1366 RPM, div = 4)
CPU Fan:     0 RPM  (min = 10546 RPM, div = 128) ALARM
Aux Fan:     0 RPM  (min = 3515 RPM, div = 128) ALARM
fan4:        0 RPM  (min = 10546 RPM, div = 128) ALARM
fan5:        0 RPM  (min = 10546 RPM, div = 128) ALARM
Sys Temp:    +33°C  (high =   +14°C, hyst =   +24°C)   ALARM
CPU Temp:  +47.5°C  (high = +80.0°C, hyst = +75.0°C)  
AUX Temp:  +20.5°C  (high = +80.0°C, hyst = +75.0°C)  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +52°C  (high =   +85°C)                   

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +52°C  (high =   +85°C)
```

What I'm wondering is:
- is this temperature range ok?  Or am I headed for a fall if I keep running this thing passive?
- what's with all of the voltage alarms?  The 430W power supply is brand new, so I can't see how it would be faulty already.

 Here's the complete system specs:

Motherboard: Asus P5KPL
CPU: intel dual core E2200
RAM: 1gb
HDD: 320GB
Optical: DVD burner
Video: Asus 7200GS HTD PE
TV tuner: LeadTek winfast DTV2000H
Powersupply: Antec Earthwatts 430
Case: silverstone LC17
Heatsink: thermalright ultima-90I

---

### Post by Yellow Pasque on 2008-03-02
It looks good. silentpcreview.com is a great resource for this kind of thing and you may have already looked there. If not, you lucked out by putting together a very efficient system and using a great heatsink. (Thermalright is the best)

I would ignore the alarms. The system wouldn't be running if those readings were correct, and as you can see, some of the conditions don't even make sense.
> in6:       +4.28 V  (min =  +5.43 V, max =  +4.63 V) ALARM
VSB:       +3.23 V  (min =  +4.08 V, max =  +3.34 V) ALARM

I congratulate you on an awesome build. I use only 2 120mm fans running off 5V myself (very quiet system). What kind of 320 GB drive did you get? Samsung?

---

### Post by xfred on 2008-03-02
That's good to hear - thanks.

I've never tried for a quiet pc before - most of my previous builds tend to end up sounding like jet engines.  And you're right - silentpcreview got me only thermalright.  I couldn't fit the 120 in the system so had to scale back to the 90I.

The 320GB hdd is WD and unfortunately the noisiest part of the system.  I'm looking into installing a nice quite laptop drive instead just as soon as I've got the mythbuntu thing sorted.

---

