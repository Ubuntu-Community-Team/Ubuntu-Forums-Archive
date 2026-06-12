---
title: "USB Touchscreen stopped working"
date: 2012-01-23
forum: Hardware
---

### Post by gohanman on 2012-01-23
I'm having sudden severe problems with a USB touchscreen. Behavior in Ubuntu is frustratingly inconsistent.

Last week, the touchscreen worked flawlessly. I ran xinput_calibrator, touched the little crosses, and everything behaved.

This week, the touchscreen barely works. When I run xinput_calibrator most touches don't seem to register at all and those that do are nowhere near where I actually touch. After touching the screen for awhile, the system stops registering clicks entirely - I can move the cursor with my mouse, but clicking no longer works. I can't find any rhyme or reason to what causes this. Running xinput_calibrator once or twice won't affect the mouse, but at some point after five or ten minutes of trying to calibrate the touch screen the mouse button stops working.

I have not updated or installed any packages. I began to notice problems after changing the screen resolution from 1024x768 to 800x600, but that may be coincidence. Returning the resolution to 1024x768 doesn't make any difference. I do not believe there have been any other configuration changes.

Ubuntu is 10.04 LTS. xinput_calibrator identifies the device as "eGalax Inc. USB TouchController". Touchscreen still works in Windows so I don't think it's a hardware problem.

---

### Post by gohanman on 2012-01-25
Update: behavior seems to vary depending on which USB port I plug the touchscreen into. Not entirely satisfying as to why, but at least it works in some ports.

Next problem:

xinput_calibrator suggests that I put the following in /etc/X11/xorg.conf.d/99-calibration.conf to make calibration persist across reboots:
```

Section "InputClass"
        Identifier      "calibration"
        MatchProduct    "eGalax Inc. USB TouchController"
        Option  "Calibration"   "139 3878 214 3775"
EndSection

```
This does not seem to do anything. I still have to run xinput_calibrator after every reboot. I did have to create the xorg.conf.d directory. Do I have to do anything else to make X notice this configuration? Create an empty or skeleton /etc/X11/xorg.conf file?

Finally, is there any way to adjust sensitivity? I don't see any options in xinput_calibrator's man page and I'm not sure what the right terminology is to google the problem. I want to change the threshold for registering a click vs a drag.

---

