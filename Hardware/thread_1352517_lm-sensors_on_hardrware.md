---
title: "lm-sensors on hardrware"
date: 2009-12-11
forum: Hardware
---

### Post by mobrien118 on 2009-12-11
Hi there,

I REALLY would like to get lm-sensors working on this machine.

It is an "Abit AL8" motherboard and has the uGuru thingy. I have 4 fans and would really like to know what they are actually doing. The BIOS reads them just fine.

I already ran "sensors-detect" as root, which detected "w83627ehf" and put the module in /etc/modules. After this, all of the sensors show up, but none of them are updating.

I checked the lm-sensors website and my board is not one that is listed!

There are some 30 or so page threads on this, but I have read a couple of them and gotten nowhere, so I'm starting my own. Also, I've read a lot of the lm-sensors site and haven't found anything there that I haven't tried.

Thanks, in advance, to anyone who can help!

--mobrien118

P.S. When I run "sensors" this is what I get:

```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +20.0°C  (crit = +85.0°C)                  

w83627ehf-isa-0290
Adapter: ISA adapter
VCore:       +2.04 V  (min =  +2.04 V, max =  +2.04 V)   ALARM
in1:        +13.46 V  (min = +13.46 V, max = +13.46 V)   ALARM
AVCC:        +4.08 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
3VCC:        +4.08 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
in4:         +2.04 V  (min =  +2.04 V, max =  +2.04 V)   ALARM
in5:         +2.04 V  (min =  +2.04 V, max =  +2.04 V)   ALARM
in6:         +6.53 V  (min =  +6.53 V, max =  +6.53 V)   ALARM
VSB:         +4.08 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
VBAT:        +4.08 V  (min =  +4.08 V, max =  +4.08 V)   ALARM
in9:         +2.04 V  (min =  +2.04 V, max =  +2.04 V)   ALARM
Case Fan:      0 RPM  (min =    0 RPM, div = 128)  ALARM
CPU Fan:       0 RPM  (min =    0 RPM, div = 128)  ALARM
Aux Fan:       0 RPM  (min =    0 RPM, div = 128)  ALARM
fan4:          0 RPM  (min =    0 RPM, div = 128)  ALARM
Sys Temp:     -1.0°C  (high =  -1.0°C, hyst =  -1.0°C)  ALARM  sensor = diode
CPU Temp:     +0.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = diode
AUX Temp:     +0.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = diode
cpu0_vid:   +0.000 V
```

---

### Post by IcarusR on 2009-12-12
> I checked the lm-sensors website and my board is not one that is listed!

If your mobo is not listed as supported then you will not get accurate results, as is seen in your list of sensors out put.

---

### Post by mobrien118 on 2009-12-12
> **IcarusR said:**
> If your mobo is not listed as supported then you will not get accurate results, as is seen in your list of sensors out put.

Sorry, I'm not trying to be argumentative, but from the lm-seosors webbsite:

"[We don't support boards, we support chips. See What chips are on motherboard XYZ.]("http://www.lm-sensors.org/wiki/FAQ/Chapter2#DoyousupportmotherboardXYZ")"

And according to [this page]("http://www.lm-sensors.org/wiki/Devices"), my "chip" is listed (Abit - µGuru) as supported. This is the chip on the Abit AL8 motherboard.

I'm just trying to get it to work with Ubuntu. Just wondering if anyone has done this, and if so, how? I'm wondering if using a custom DSDT would fix it, since mine has bugs, but, as I understand it, Karmic disabled the "easy" way to do this.

I wanna add that I did try replacing "w83627ehf" with "abituguru" and/or "abituguru3" in the /etc/modules file, but it just crapped out.

I'm looking for the "easiest" solution to this problem. If that solution is "write a new kernel module" then so be it. (But I suspect there is an easier way...) Of course, if I succeed in my goal, I plan to contribute my findings back to to the community so that others may benefit.

Thanks again,

--mobrien118

---

### Post by IcarusR on 2009-12-12
Nope I'm not trying to be argumentative either !

> 
"We don't support boards, we support chips. See What chips are on motherboard XYZ."

Fair enough.

It was you that said 

> I checked the lm-sensors website and my board is not one that is listed!

Judging by the output of sensors it does not know how to interpret the info very accurately. 

This is my output on an MSI K7N2 Delta2 mobo which actually uses the same chip, but makes more sense.

```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +34.5°C  (crit = +100.1°C)                  

w83627hf-isa-0290
Adapter: ISA adapter
VCore 1:     +1.66 V  (min =  +1.44 V, max =  +1.86 V)   
VCore 2:     +1.73 V  (min =  +1.44 V, max =  +1.86 V)   
+3.3V:       +3.33 V  (min =  +2.82 V, max =  +3.79 V)   
+5V:         +5.00 V  (min =  +6.83 V, max =  +2.15 V)   ALARM
+12V:       +12.22 V  (min =  +9.91 V, max = +13.92 V)   
-12V:       -11.87 V  (min = -10.80 V, max =  +0.72 V)   ALARM
-5V:         +3.54 V  (min =  +2.84 V, max =  -2.54 V)   ALARM
V5SB:        +5.56 V  (min =  +1.26 V, max =  +1.45 V)   ALARM
VBat:        +2.77 V  (min =  +0.06 V, max =  +3.14 V)   
fan1:          0 RPM  (min = 8881 RPM, div = 4)  ALARM
fan2:       2721 RPM  (min = 1950 RPM, div = 4)
fan3:          0 RPM  (min = 1377 RPM, div = 4)  ALARM
temp1:       +32.0°C  (high = +127.0°C, hyst = -82.0°C)  sensor = thermistor
temp2:       +34.5°C  (high = +120.0°C, hyst = +115.0°C)  sensor = thermistor
temp3:       +24.5°C  (high = +120.0°C, hyst = +115.0°C)  sensor = thermistor
cpu0_vid:   +1.650 V
beep_enable:enabled

```

Good luck getting it to work.

---

### Post by mobrien118 on 2010-12-10
Well, it's been about a year since I started this thread and I'd still really like to get lm-sensors working on this hardware (especially since I just had to blind diagnose a failing power supply).

Any information anyone has on how to manually try anything (I can code, if pointed in the right direction), I would greatly appreciate it. I tried messing around with one of the settings files for chipsets back when I originally was dealing with this, but the changes I was making weren't taking affect. I haven't really toyed with it much since then, except for running "sensors-detect" every time a new release comes out, hoping that the chipset works now.

Thanks in advance!

--mobrien118

---

