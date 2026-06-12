---
title: "CPU temperature &quot;stuck&quot; at 127 F/53 C"
date: 2018-01-19
forum: Hardware
---

### Post by henry-j-spare on 2018-01-19
Psensor shows my CPU temperature as 127 degrees F, regardless of load.

The issue started after I upgraded the machine's CPU and BIOS. The old CPU was a Pentium E2160, and the new one is a Core 2 Duo E7400. IIRC the BIOS doesn't have a CPU temperature readout, soI'm not 100% sure whether or not the issue is only in Lubuntu.

The computer is an HP rp5700 running Lubuntu 16.04.1.

---

### Post by QIII on 2018-01-19
It is likely that either the CPU has a thermistor or the motherboard gets a temperature at the socket.  At the very least, that would be how it regulates the HSF.  I would find it strange if the motherboard were not making either of those available to the OS.

If you can, get in to the BIOS and check carefully for a temperature reading.

You may have to do 

```
sudo sensors-detect
```

(or the appropriate command) again if you are using something like lm-sensors or psensor.

---

### Post by henry-j-spare on 2018-01-19
Here's the result of sudo sensors-detect:
```

Driver `smsc47b397':
  * ISA bus, address 0x580
    Chip `SMSC SCH5317 Super IO' (confidence: 9)

Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)

```

---

### Post by kansasnoob on 2018-01-19
Is the cooler mounted properly? With fresh thermal paste/grease? Is the fan working properly?

I recently used several Pentium Dual Core E5700 CPU's (all used off Ebay) and out of them one ran hot in two different motherboards. Other than running hot it worked OK but I still tossed it in the trash - hardly worth returning a $4 CPU. I'd be willing to bet that if everything is OK cooling wise that it's just a defective CPU.

---

### Post by henry-j-spare on 2018-01-19
> **kansasnoob said:**
> Is the cooler mounted properly? With fresh thermal paste/grease? Is the fan working properly?

I recently used several Pentium Dual Core E5700 CPU's (all used off Ebay) and out of them one ran hot in two different motherboards. Other than running hot it worked OK but I still tossed it in the trash - hardly worth returning a $4 CPU. I'd be willing to bet that if everything is OK cooling wise that it's just a defective CPU.

I guess I'll try replacing the CPU, since they're only $4 anyways.

---

### Post by QIII on 2018-01-19
I'd still check that you did a good job installing the HSF.  Might save you some aggravation.

---

