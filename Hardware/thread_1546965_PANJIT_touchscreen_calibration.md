---
title: "PANJIT touchscreen calibration"
date: 2010-08-06
forum: Hardware
---

### Post by czarkoff on 2010-08-06
I own an ASUS R2Hv device that has PANJIT USB TouchSet onboard.

In Lucid it's supported by usbtouchscreen kernel module, and it works in X, but I can't find a right tool to calibrate it. By the way, I can't get the driver used by X, as X log states only that it is configured as "tablet", and o my knowledge there's no such input driver.

Anyone knows any means of getting this calibrated?

---

### Post by Z.K. on 2010-08-27
> **czarkoff said:**
> I own an ASUS R2Hv device that has PANJIT USB TouchSet onboard.

In Lucid it's supported by usbtouchscreen kernel module, and it works in X, but I can't find a right tool to calibrate it. By the way, I can't get the driver used by X, as X log states only that it is configured as "tablet", and o my knowledge there's no such input driver.

Anyone knows any means of getting this calibrated?

You could try Xinput_Calibrator at [http://www.freedesktop.org/wiki/Software/xinput_calibrator](http://www.freedesktop.org/wiki/Software/xinput_calibrator).  It works quite well at least for my use.  You do have to find a way to keep the settings though as if you reboot you will need to recalibrate again.  I put mine in the /etc/Profile file which takes effect after login.  If I could figure out how to set these settings just before the login screen, I would be very happy.  Still, this program might work for you.

---

