---
title: "Led on gpio very dim (low voltage)"
date: 2020-10-02
forum: Hardware
---

### Post by evil-goat on 2020-10-02
I   am using a minnowboard turbot (kind of like a raspberry pi, except its   x86_64) When I boot it, the led connected to the gpio pins is normal   brightness.
After i create the gpio pin by typing  ***echo [pin number] >/sys/class/gpio/export***
it turns off. This is normal. After I change it to out and changing "value" to 1 by using ***echo 1 >/sys/class/gpio/gpio[pin-number]/value***
Then the led is very dim thus representing a lower voltage.

I   am using ubuntu 20.04. I did the same thing in a previous os (Linux   mint), and everything worked as expected. How can i make the led be   brighter, and the gpio output the correct voltage?

---

