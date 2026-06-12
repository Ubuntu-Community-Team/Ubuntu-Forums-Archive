---
title: "joydev params for axes/buttons"
date: 2004-12-20
forum: Hardware &amp; Laptops
---

### Post by fuzzix on 2004-12-20
joydev loads on boot and detects my cheapo USB pad on startup, but the device has too many axes/buttons.

```
$ jstest --normal /dev/input/js0
Joystick (Austgame USB PAD) has 9 axes and 12 buttons. Driver version is 2.1.0.
Testing ... (interrupt to exit)
Axes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0  6:     0  7:     0  8:     0 Buttons:  0: off  1: off  2: off  3: off  4: off  5: off  6: off  7: off  8: off  9: off 10: off 11: off
```

There are 2 axes and 10 buttons.
Axes 1 and 2 respond to input, but games etc expect input from 0 and 1 with the effect that L-R acts like U-D.

Is there a way to pass parameters to joydev to correctly process this device?

---

