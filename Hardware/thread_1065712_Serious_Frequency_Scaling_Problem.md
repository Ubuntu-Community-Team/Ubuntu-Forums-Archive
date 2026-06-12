---
title: "Serious Frequency Scaling Problem"
date: 2009-02-10
forum: Hardware
---

### Post by Ubangi on 2009-02-10
I turned on the frequency scaling monitor applet on the panel recently in connection with trying to control the fan of my Acer Aspire One.
It appeared to work, changing frequencies according to the governor regime selected. So did the fan, turning itself on and off.

However, I experienced serious problems with the laptop mousepad becoming unresponsive, and the whole machine freezing up frequently and requiring hard reboot.

I lowered the default fan temperature right down, using /etc/acerfand.conf
but this made no difference, nor did changing the governor regimes.

Finally I homed in on the frequency scaling itself and turned it off. This seems to have helped, my laptop is more responsive again and has not frozen for a few hours.

I just mention all this as a warning to anyone contemplating using the frequency scaling: do not do it!

---

### Post by Ubangi on 2009-02-10
Also, when I installed lm-sensors and Hardware Sensors Monitor, it says:
No sensors found!

---

### Post by boof1988 on 2009-02-10
> **Ubangi said:**
> Also, when I installed lm-sensors and Hardware Sensors Monitor, it says:
No sensors found!

Where was "No sensors found" displayed?

Did you...

```
sensors-detect
```

after installing the applications?

Also... if there are no sensors, they can't be detected.  I have a P3 600MHz that has no sensors.


For other peoples benefit... they might need to (after installing and running sensors-detect) right click on the Hardware Sensors Monitor applet and choose Properties to configure the display.

Hope this helps.

---

### Post by Ubangi on 2009-02-16
Thanks, I tried sensors-detect but it did not detect any on my Asus Acer One. No wonder the fan is not working properly when there aren't any sensors....

---

