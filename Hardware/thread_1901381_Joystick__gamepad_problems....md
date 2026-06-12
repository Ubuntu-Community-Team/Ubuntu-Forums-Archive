---
title: "Joystick / gamepad problems..."
date: 2011-12-28
forum: Hardware
---

### Post by borisw37 on 2011-12-28
Trying to connect a Logitech gamepad to TrimSlice running Ubuntu 11.10.
Whenever I plug it in a new device shows up "/dev/input/event2"
If I open the file, it does get data from the gamepad.
But I'm not seeing the standad "/dev/input/js0" file.
"jscal -c /dev/input/event2" returns
error getting version: Invalid agrument.
 
what am i doing wrong? how come joystick is not detected as js0?
 
Thank you,
 
Boris.

---

### Post by Grumbel on 2012-02-07
> **borisw37 said:**
> what am i doing wrong? how come joystick is not detected as js0?
To access /dev/input/event2 you must use "evtest".
To access "/dev/input/js0" you must use "jstest" (or jscal for calibration, which you however should not use).

As for why js0 doesn't show up, it might be that the joydev module isn't loaded, so try:

```
modprobe joydev
```

If that doesn't help, run evtest on the device and post the output here.

---

