---
title: "eGalaxTouchscreen calibration problems on Ubuntu 14.04"
date: 2015-09-28
forum: Hardware
---

### Post by viniciusdearaujob on 2015-09-28
Hello,

I work with a few computers running Ubuntu 14.04 and generic modules as evdev and mtdev for the eGalax touchscreen (EXC7200) - xinput list shows 2 entries for this touchscreen, one of them is the touch and the other is "Pen". xinput_calibrator gives me different values for each one of the devices.

Recently, one of those computers presented a strange behavior: with everything up & running, the touchscreen stopped working properly. Touching the center of the screen would make the pointer click in the bottom left of the screen as if it were un-calibrated. Resetting the machine solved the problem - but it's not ideal as we are running critical applications.

I could reproduce this behavior using xinput_calibrator with messed up values, but I have no idea what was the cause. Also, I don't have any system log and I couldn't find anything useful being logged when I tried to reproduce it.

Any ideas on how to avoid this behavior and/or possible causes? None of the other computers had similar issues and their 10-evdev.conf files don't have "Calibration" options. For now I am thinking about re-calibrating, saving the calibration options and implementing a hard reset for modules and X if needed.

Thank you, folks!

---

