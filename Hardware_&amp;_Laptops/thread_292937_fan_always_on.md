---
title: "fan always on"
date: 2006-11-04
forum: Hardware &amp; Laptops
---

### Post by kswenson on 2006-11-04
I have a dell pecision m60 and have just installed edgy...
   I've encountered a problem that didn't occur in hoary: the fan won't go off.

I have the temperature applet running so I know the the temperature does scale with processor load but the numbers seem to be too high (the temperature is 90farenheit) when idle.
So the temperature monitor seems to be kind of working and the CPU scaling works fine so there seems to be some subtle problem here...
   could anyone help me figure out how to scale down the temperature values that are being received?

I tried to install lm-sensors but it doesn't detect any chip and I'm not sure this is necessary since I seem to be getting some temperature readout from the kernel.

Thank you.

---

### Post by kswenson on 2006-11-04
Strange...
I continued my usual routine of installing a bunch of stuff from automatix including the proprietary nvidia driver.
When I rebooted the fan worked!
The only think I can think of the really changed was that driver.

---

