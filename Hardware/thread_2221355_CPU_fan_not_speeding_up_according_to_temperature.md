---
title: "CPU fan not speeding up according to temperature"
date: 2014-05-01
forum: Hardware
---

### Post by john205 on 2014-05-01
So I got a new CPU fan for my dell DM5150 after the old one spun the bearings out, and I almost instantly noticed something. The heatsink gets incredibly hot, almost too hot to touch with the fan going nowhere soon. With the old fan, it would almost never stay at idle, while the heatsink was barely warm to the touch. I did replace the thermal paste when I got the new fan, but I don't see why its fan won't come out of idle for the CPU being this hot. 

Or am I just completely mistaken and this is how it's supposed to run?
UPDATE: I'm retiring this computer for now, as a new computer is being built ATM.

---

### Post by john205 on 2014-05-06
Bump.
UPDATE: There is a second CPU with a black heatsink on it and it's pretty cool to the touch. Is this where the fan gets the message to speed up?

---

### Post by Yellow Pasque on 2014-05-07
I think you're confusing the CPU and GPU. Look at sensors output  to see temps:
```
sensors
```

---

### Post by john205 on 2014-05-07
No, The CPU and GPU fans make two very distinct sounds at idle and when not. Removing the PWM wire gives it the full 12 volts like it should, so it isn't a fan problem. On power-up, the fan jumps to full speed for a split second. Maybe a PWM controller issue?
 Also, the Dimension 5150 doesn't give out tachometer and temp readings as far as I know. I've already tried.

---

### Post by Yellow Pasque on 2014-05-07
> **john205 said:**
> UPDATE: There is a second CPU with a black heatsink on it and it's pretty cool to the touch. Is this where the fan gets the message to speed up?

Sorry, I was the one who got confused. You were probably referring to the mobo chipset there. Anyway...

You may be able to see temp by looking directly at /proc/acpi/
Example: [http://www.thelinuxtips.com/2010/11/read-the-cpu-temperature/](http://www.thelinuxtips.com/2010/11/read-the-cpu-temperature/)

Also, do you have coretemp module loaded? It may allow you to see the temp using sensors command.
```
sudo modprobe coretemp
```

---

### Post by john205 on 2014-05-08
Don't think the 5150's temps are accessible at all, but we'll see.
EDIT: Nope, won't work.

---

