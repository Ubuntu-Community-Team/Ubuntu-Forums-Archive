---
title: "Is my system running too hot?"
date: 2017-01-30
forum: Hardware
---

### Post by Superdude_123 on 2017-01-30
Is this normal temperatures for a Intel i5?

$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +27.8°C  (crit = +119.0°C)
temp2:        +29.8°C  (crit = +119.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +93.0°C  (high = +84.0°C, crit = +100.0°C)
Core 0:         +90.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:         +93.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:         +89.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:         +92.0°C  (high = +84.0°C, crit = +100.0°C)

---

### Post by DuckHook on 2017-01-30
I would suspect false readings or misconfigured settings before I would suspect anything else. Both readings are far from normal.

Is your computer a laptop? If so, is it running hot? Even a desktop will give indications of too much physical heat. Does your computer shut down by itself? At those CPU readings, it should. Your low temps don't make sense either. Both are far less than body temperature. Even though components are very power-efficient these days, they aren't *that* efficient.

Did you set up sensors initially with:```
sudo sensors-detect
```

---

### Post by Superdude_123 on 2017-01-30
So my system is a Desktop that's used mostly as a remote server with a raid 5 array. I checked my HDD temps, and they are all between 27-30 C.

The system has randomly shutdown, but I was suspecting that my problem was kernel related with my mother board. What's odd is that my CPU usage isn't too bad. Through htop, I can see some cores are at 100% for a few seconds, but otherwise hover under 30%.

---

### Post by DuckHook on 2017-01-30
HDDs temps will be about right. I thought they might have been GPU.

A remote server is very hard to diagnose in this way. The best course when confronted with such numbers is to reboot immediately into BIOS and see what it tells you (it's MOBO sensors being more reliable than lm-sensors). It is also standard to stick in a physical digital thermometer near the cpu and just get a raw temperature readout. 93°C is hot enough to boil water at high elevation. It will be very evident just by touching the case.

Random shutdown does not bode well, and the readings may very well be correct. Broken CPU fan? Clogged up vents? But then, the HDDs would be hotter too.

Ultimately, you will need to physically examine the box, which obviously cannot be done remotely.

---

### Post by Superdude_123 on 2017-01-31
Yes, and I had it automatically add it's findings in the config file.

---

### Post by Bucky Ball on 2017-01-31
Can I take a guess at a generic silver box power supply? if so, that could be heating the whole inside of the machine. They are not intended to last long, can go off with a bang due to lack of safety switches, and are incredibly inefficient. 

Just a thought. Stick your hand on the back of the machine where the PSU is and see what you can feel. Mine is blowing out cold air.

Your hard drives between 27-30C is normal.

---

### Post by Superdude_123 on 2017-01-31
While I would agree with you since conventional wisdom would say that you're most likely right, this time however, this PC is brand new (early Jan 2017), and the PSU is not from the bottom bracket of the store shelf. Here are the specs of the PC in question:

Mother Board: MSI Z170-A Pro ATX LGA1151
CPU: INTEL CORE I5-6400
Case: Fractal Design Define R4 ATX
Case Fan: Fractal Design Silent Series R2 140mm
PSU: Corsair AX760 760W ATX 80 Plus Platinum Modular Power Supply Active PFC 120MM Fan 

The case, with the added fan, I believe has 3 140 mm fans in total, and the PSU, being a platinum model, will modulate it's fan from 0 RPM to max as the load requires.

---

### Post by DuckHook on 2017-01-31
These considerations may be of academic interest, but they won't get you closer to a solution. In this situation, you (or someone nearer to the machine in question) must physically inspect it, physically take its temperature, and see what its BIOS readings are (as per my post above). If fans are or are not working, this can only be determined with a physical inspection. If the PSU is not working properly, ditto. If the cpu fan has fallen off, ditto. Or if the thermal paste is not making good contact, ditto.

There's little that anyone can do, whether on these forums or elsewhere, without such an inspection either ruling out or confirming a physical problem.

---

### Post by Superdude_123 on 2017-02-01
As it's good practice to share the lessons learned, the result that was found from a physical inspection is that the PC had 20 sq ft of bubble wrap stuffed inside the case, thus preventing air flow.

So the lesson learned is: checked for rogue bubble wrap!

---

### Post by Bucky Ball on 2017-02-02
> **Superdude_123 said:**
> ... the PC had 20 sq ft of bubble wrap stuffed inside the case, thus preventing air flow

Yikes!!! Lucky overheating was the worst thing that happened.

---

### Post by DuckHook on 2017-02-02
> **Superdude_123 said:**
> …checked for rogue bubble wrap!…in all my years on this and other forums, that's a first.

Thanks for putting a smile on my face today. ;)

…and glad it worked out in the end!

---

