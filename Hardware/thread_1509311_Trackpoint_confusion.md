---
title: "Trackpoint confusion"
date: 2010-06-14
forum: Hardware
---

### Post by ATPJOE on 2010-06-14
I already found other threads regarding the IBM Trackpoint sensitivity and speed adjustment. I tweaked those settings, but they do NOT stick after reboot. It gets annoying having to re-tweak the settings every time. 

What I did: 
```
echo -n 220 > /sys/devices/platform/i8042/serio1/speed 
echo -n 250 > /sys/devices/platform/i8042/serio1/sensitivity
```

Added this:
```
SUBSYSTEM=="serio", DRIVERS=="psmouse", WAIT_FOR="/sys/devices/platform/i8042/serio1/sensitivity", ATTR{sensitivity}="220"
```

to /etc/udev/rules.d/10-trackpoint.rules

But it does not stick. What am I doing wrong? Is it coded incorrectly for the rules file?

Thanks in advance.

---

