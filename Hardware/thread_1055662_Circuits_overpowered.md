---
title: "Circuits overpowered"
date: 2009-01-30
forum: Hardware
---

### Post by Aroll605 on 2009-01-30
Hello. 

I have a question. Is it normal (this may look silly) that my motherboard circuits are overpowered a bit?

```

+5V:         +5.03 V  (min =  +2.12 V, max =  +0.83 V)   ALARM
+12V:       +12.10 V  (min =  +7.24 V, max =  +4.68 V)   ALARM
-12V:        +1.46 V  (min =  -6.77 V, max = -14.50 V)   ALARM
-5V:         +2.29 V  (min =  +0.88 V, max =  -0.48 V)   ALARM
V5SB:        +5.54 V  (min =  +6.26 V, max =  +3.44 V)   ALARM
VBat:        +3.49 V  (min =  +2.50 V, max =  +2.82 V)   ALARM

```

I have an ASROCK P4I65G

Aroll605

---

### Post by electrogeist on 2009-01-31
Yes there is a little tolerance, and often the PSU provides a little above, which is good because it may go down a little under heavy load.

but those min/max values look odd...or I am not reading it right at this time of night... is that list from the BIOS setup for setting an alarm?  

Also the negatives aren't of so much concern.  -5v has been somewhat discontinued in the last few years, I think was mainly needed for legacy ISA slots.  And -12v I don't think is too important anymore unless you have serial ports, but I could be wrong on that

---

### Post by Aroll605 on 2009-02-07
I used 'sensors' from ubuntu repository to access the temperature sensors.

---

