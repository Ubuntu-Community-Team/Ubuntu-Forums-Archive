---
title: "Temperature sensor on INTEL D510MO in Ubuntu"
date: 2010-05-31
forum: Hardware
---

### Post by antwerp-avp on 2010-05-31
Hi, guys,

I have installed Ubuntu 10.04 on my new nettop based on Intel D510MO. Everything works perfectly except temperature sensors - I see the temperature in BIOS, but I cannot get it in Ubuntu. I tried to use comptertemp widget and XSensors application but all of them show me errors like "No thermal monitor support!". Seems that it is need to install some drivers for that.

Can anybody tell me what it is need to install and where I can get it?

Thanks

---

### Post by bra|10n on 2010-05-31
you need to install lm-sensors and then run in a terminal  [COLOR=#C20CB9]****[/COLOR]sudo sensors-detect

  answering **Yes** (default) to **all questions**,  *even that last one that defaults to No*
 Now restart your session and in a terminal:
  sensors

---

### Post by dino99 on 2010-05-31
> **bra|10n said:**
> you need to install lm-sensors and then run in a terminal  [COLOR=#C20CB9]****[/COLOR]sudo sensors-detect

  answering **Yes** (default) to **all questions**,  *even that last one that defaults to No*
 Now restart your session and in a terminal:
  sensors

not the solution as most of the modules exist with actual kernel:

[http://www.lm-sensors.org/wiki](http://www.lm-sensors.org/wiki)

need to install fancontrol and set it into /etc/fancontrol (into console run: sensors)

---

### Post by antwerp-avp on 2010-05-31
Thank you for fast responses!

I have tried to do both suggestions and currently got next output:

gn0me@gn0me-desktop:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +51.0°C  (crit = +100.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +50.0°C  (crit = +100.0°C)                  

w83627thf-isa-0290
Adapter: ISA adapter
in0:         +1.12 V  (min =  +0.00 V, max =  +3.84 V)   
in1:         +1.07 V  (min =  +0.19 V, max =  +1.14 V)   
in2:         +1.97 V  (min =  +0.85 V, max =  +1.28 V)   ALARM
in3:         +3.01 V  (min =  +0.27 V, max =  +3.17 V)   
in4:         +3.36 V  (min =  +0.51 V, max =  +1.02 V)   ALARM
in7:         +3.01 V  (min =  +1.54 V, max =  +3.10 V)   
in8:         +3.31 V  (min =  +3.44 V, max =  +3.71 V)   ALARM
fan1:          0 RPM  (min = 7670 RPM, div = 8)  ALARM
fan2:          0 RPM  (min = 56250 RPM, div = 4)  ALARM
fan3:          0 RPM  (min = 11440 RPM, div = 2)  ALARM
temp1:       +53.0°C  (high = +37.0°C, hyst = +42.0°C)  ALARM  sensor = thermistor
temp2:       +34.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
temp3:       +34.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
beep_enable:enabled

But computertemp widget still doesn't work properly

---

### Post by jap1968 on 2010-05-31
I have this same board, and I want to remark some things:

1.- Voltage sensors seem to report wrong values.
2.- Apart from these 3 temperature sensors, I can see four additional sensors for every processor core (but the processor has just two cores).
These four additional sensors some days work, whereas other days I can see just 2 out of 4, and even in some occasions, all of them report error (i.e. no value readings).
3.- temp1 seems to correspond to the NM10 southbridge chip. This chip gets hot and I have seen it having a passive cooler on boards from other manufacturers. Can anyone confirm if this temperature corresponds to the NM10 chip?

---

### Post by antwerp-avp on 2010-06-01
jap1968, this CPU has hyperthreading mode by default that is why you see 4 different cores in Ubuntu. You can switch off this option in BIOS.

Temperature of mine D510 is about 55-65 degress and what's yours?

---

### Post by jap1968 on 2010-07-13
> **antwerp-avp said:**
> jap1968, this CPU has hyperthreading mode by default that is why you see 4 different cores in Ubuntu. You can switch off this option in BIOS.

Temperature of mine D510 is about 55-65 degress and what's yours?

I know that HT is the cause of the OS viewing 4 cores, but I find strange that temperature sensors are also detected twice, or something like that.

Regarding the main sensor, mine is in the range of 45 deg when the case fan is connected (a small 6cm fan running at about 1500rpm). If I unplug the fan, the system reaches temperatures of about 60 deg.

I have glued a small cooler (as those used for memory chips in some powerful graphic cards) to the NM10 chip. The cooler lowered temperature just about 2 - 4 deg. I was expecting a better improvement.

I wanted to use this computer without case fan, but I find temperatures too high for that. I have always the case fan plugged and working.

Anyway: Have a look at these topics:
[Erroneous CPU temperature readouts on D510MO]("http://communities.intel.com/thread/10614")

The problem seems to have been fixed with the latest Bios update (20100705). :D

---

### Post by linutx on 2010-07-23
> **jap1968 said:**
> I know that HT is the cause of the OS viewing 4 cores, but I find strange that temperature sensors are also detected twice, or something like that.

Regarding the main sensor, mine is in the range of 45 deg when the case fan is connected (a small 6cm fan running at about 1500rpm). If I unplug the fan, the system reaches temperatures of about 60 deg.

I have glued a small cooler (as those used for memory chips in some powerful graphic cards) to the NM10 chip. The cooler lowered temperature just about 2 - 4 deg. I was expecting a better improvement.

I wanted to use this computer without case fan, but I find temperatures too high for that. I have always the case fan plugged and working.

Anyway: Have a look at these topics:
[Erroneous CPU temperature readouts on D510MO]("http://communities.intel.com/thread/10614")

The problem seems to have been fixed with the latest Bios update (20100705). :D
[jap1968]("http://ubuntuforums.org/member.php?u=164546"),
have you updated yours to the latest bios (20100705 - 0303) and observed no ill effects?
this [link]("http://communities.intel.com/message/96816#96816") seems to indicate that there is an issue with the new bios update where the MO
will **not** boot from flash drive
I really wanna see the temperature sensor working properly, but I do not wanna turn my NAS into a door stopper:(
Cheers

---

