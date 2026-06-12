---
title: "Detecting sensors for fancontrol - 12.04, Asus P8H67 mobo"
date: 2013-09-09
forum: Hardware
---

### Post by bernard2 on 2013-09-09
[Despite what the forum thinks, I'm not a complete newbie - I just had to create a new ID!]

I'm having trouble with detecting sensors - for use with fancontrol - with an Asus P8H67 mobo.  I had a LOT of trouble with this when I first set up this machine on 11.04, a couple of years ago. The main cause being that the super i/o chip on this mobo didn't have a driver readily available. With some great help from this forum, I was talked through the process of locating a suitable driver and then pushing the right buttons to get the sensors detected. Great!

Now, however, I want to build a fresh install - same hardware, different disc partition. I've installed 12.04 and the fancontrol and lm_sensors packages. 12.04 seems to have the driver included, but I can't get it to work.

I ran "sudo sensors-detect" and it found the i/o chip, and added "w83627" to /etc/modules

After a restart, "dmesg | grep ehf" suggests that the i/o chip has been found... 
[    1.750315] w83627ehf: Found NCT6776F chip at 0x290

but running "sensors" indicates that the mobo sensors haven't been located, which of course means that pwmconfig is no use to me.

Sensors output:
coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +33.0°C  (high = +82.0°C, crit = +102.0°C)
Core 0:         +33.0°C  (high = +82.0°C, crit = +102.0°C)
Core 1:         +33.0°C  (high = +82.0°C, crit = +102.0°C)

Can anyone give me some clues as to what I'm missing? I KNOW the sensors are there because the 11.04 installation can find them!

---

### Post by bernard2 on 2013-09-11
Any suggestions? I'm banging my head against a brick wall at the moment, but I can't help feeling that I am missing something obvious...

---

### Post by Yellow Pasque on 2013-09-11
Try:
```
sudo modprobe -v nct6775
sensors
```

> This driver supercedes the NCT6775F and NCT6776F support in the W83627EHF
driver. It supports NCT6106D, NCT6775F, NCT6776F, NCT6779D, and NCT6791D.
-- [https://github.com/groeck/nct6775](https://github.com/groeck/nct6775)

---

