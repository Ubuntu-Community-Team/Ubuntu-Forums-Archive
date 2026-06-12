---
title: "Is my fan dead?"
date: 2014-08-01
forum: Hardware
---

### Post by seal308 on 2014-08-01
I'm running lubuntu on an old eeebox.
Now after a while the eeebox shuts down and tried to turn back on, shuts down, tried to turn back on.
The only way I can stop this is to remove the power cable from the back and then after a while putting the power cable back into the eeebox and then it works fine for a while.
I don't know much about hardware but I'm thinking this is an overheating issue due to a damaged fan.
Does this sound right?
I have no idea how to replace it either. Eeebox's have a weird shape I guess I will have to disassemble and see what I can do.

---

### Post by tgalati4 on 2014-08-01
Was this computer operated on the floor?  Computers on the floor collect a lot of dust.  How old is the machine?  If you have not cleaned it in the past 2 years, then it is very likely full of dust.  You can check to see if the fan is spinning.  Boot into BIOS and look for fan speeds in the PC Health Management section.  It could also be a bad power supply or bulging/leaky capacitors on the motherboard.

---

### Post by mikewhatever on 2014-08-01
It could be. You might want to check the CPU temp with something like <cat /sys/devices/virtual/thermal/thermal_zone*/temp>.

---

