---
title: "Genius WizardPen - need help"
date: 2009-12-05
forum: Hardware
---

### Post by yanux on 2009-12-05
Hello there :KS

I have recently switched to Linux and dedicated some time to solving random problems, such as making devices (such as tv tuner and camcoder) work. Most things turned out to be fine, however, my Genius WizardPen 4x3 refuses to work.

After reading older threads I came accross
```
https://help.ubuntu.com/community/TabletSetupWizardpen
```

Tried two different packages:
```
wizardpen-0.7.0_alpha2-1_amd64.deb
xserver-xorg-input-wizardpen_0.7.1-0ubuntu3_amd64.deb
```

...and didn't get it to work! System responds to pressing buttons on the pen, I even managed to get calibration values (i.e. the tablet itself is alive!).

Xorg.0.log doesn't seem to show any errors:
```

...
(II) config/hal: Adding input device UC-LOGIC Tablet WP4030U
(**) UC-LOGIC Tablet WP4030U: always reports core events
(**) UC-LOGIC Tablet WP4030U: Device: "/dev/input/event6"
(II) UC-LOGIC Tablet WP4030U: Found 10 mouse buttons
(II) UC-LOGIC Tablet WP4030U: Found x and y relative axes
(II) UC-LOGIC Tablet WP4030U: Found scroll wheel(s)
(II) UC-LOGIC Tablet WP4030U: Found x and y absolute axes
(II) UC-LOGIC Tablet WP4030U: Found absolute touchpad
(II) UC-LOGIC Tablet WP4030U: Configuring as touchpad
(**) UC-LOGIC Tablet WP4030U: YAxisMapping: buttons 4 and 5
(**) UC-LOGIC Tablet WP4030U: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "UC-LOGIC Tablet WP4030U" (type: TOUCHPAD)
(WW) UC-LOGIC Tablet WP4030U: touchpads and touchscreens ignore relative axes.
(**) UC-LOGIC Tablet WP4030U: (accel) keeping acceleration scheme 1
(**) UC-LOGIC Tablet WP4030U: (accel) filter chain progression: 2.00
(**) UC-LOGIC Tablet WP4030U: (accel) filter stage 0: 20.00 ms
(**) UC-LOGIC Tablet WP4030U: (accel) set acceleration profile 0
(II) UC-LOGIC Tablet WP4030U: initialized for absolute axes.
```

I assume I have some problems with calibration, as the tablet refuses to act as a mouse. Does anyone know how to make it work on Ubuntu 9.10 (64-bit)?

---

### Post by Favux on 2009-12-05
Hi yanux,

Welcome to Ubuntu Forums!

See Dr Kurian's [HOW TO INSTALL WIZARDPEN DRIVER]("http://ubuntuforums.org/showthread.php?t=1337260").

Hope this is helpful.

---

### Post by yanux on 2009-12-05
Hey Favux!

Got it working, thank you very much! :KS

---

### Post by Favux on 2009-12-05
Hi yanux,

Great!  Your welcome.  Please be sure to also thank Dr. Kurian for his HOW TO.

---

### Post by drpjkurian on 2009-12-06
> **Favux said:**
> Hi yanux,

Great!  Your welcome.  Please be sure to also thank Dr. Kurian for his HOW TO.

:P:razz::P

---

