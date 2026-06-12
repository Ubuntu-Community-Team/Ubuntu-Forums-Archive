---
title: "lm-sensors cannot detect CPU, or anything else"
date: 2013-10-28
forum: Hardware
---

### Post by morgan5 on 2013-10-28
Hi all,
Need help reading cpu temperature please!!!

I just built a new system as described below, then installed Ubuntu 12.04 LTS.  Everything seemed to fire up properly, except Psensor only detects temp1 which appears to be my wireless PCI card at 0 degrees, and cpu usage.  I reviewed the forum and thought I found the solution by running [sudo sensors-detect]  but this didn't detect anything additional. Only notable thing it detected was during the Super I/O sensors scan, "trying family 'VIA/winbondNuvoton/Fintek" it said "Found unknown chip with ID 0x1106".

Build:
Processor: AMD A6 5400K Dual-core 3.6 Ghz
Board:  MSI FM2-A55M-E33
RAM: ADATA Premier DDR3 1333 4 gGb
Graphics:  whatever is integrated in the APU

I looked at [http://lm-sensors.org/wiki/Devices](http://lm-sensors.org/wiki/Devices), but I don't understand what "family" of AMD chip I have. 

Is my hardware not supported by 12.04 LTS or am I just not doing something right?  Any thoughts appreciated.

---

### Post by QIII on 2013-10-28
Hello!

Could you please cut and paste the exact text you *do *get back from 

```
sensors
```

---

### Post by morgan5 on 2013-10-28
mogli@mogli-MS-7721:~$ sensors
k10temp-pci-00c3
Adapter: PCI adapter
temp1:         +1.4°C  (high = +70.0°C)
                       (crit = +70.0°C, hyst = +69.0°C)

mogli@mogli-MS-7721:~$ ^C
mogli@mogli-MS-7721:~$

---

### Post by QIII on 2013-10-28
k10temp-pci-00c3 is your processor temp sensor.

Obviously, however, it's either wrong or you have a very good cooler.

AMD chips are notorious for giving low temps (I use a script to add 10 degrees to the sensor reading before it is displayed on my conky), but clearly it should not be reporting a temperature a degree and a half above the freezing point of water.

I make sure this gets reported as 31 degrees on my conky:

```
k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +21.0°C  (high = +70.0°C)
                       (crit = +80.0°C, hyst = +75.0°C)


```

You may want to do some searching around the web for the behavior of that motherboard's sensor reports.

---

### Post by Yellow Pasque on 2013-10-29
It looks to be a Fintek F71868AD sensor chip, and lm-sensors has a datasheet but no driver yet. [http://comments.gmane.org/gmane.linux.drivers.sensors/32672](http://comments.gmane.org/gmane.linux.drivers.sensors/32672)

---

### Post by morgan5 on 2013-10-29
Thanks! A disappointing answer, but at least I know now.  Do i have an alternative to lm-sensors?  Is there a way to read the CPU temps from BIOS while operating under load with Ubuntu?  (Sorry, I'm new at all of this)

---

### Post by grahammechanical on 2013-10-29
On my system temp1 with lm-sensors is the graphic adapter. I have installed Psensors which I have found detects various sensor readouts without needing lm-sensors installed. And it is a real time readout and not just a one time readout like lm-sensors.

Might be more useful and can serve as a double check.

Regards.

---

