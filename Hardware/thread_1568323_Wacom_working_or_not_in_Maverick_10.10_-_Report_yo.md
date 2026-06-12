---
title: "Wacom working or not in Maverick 10.10 - Report your experience!"
date: 2010-09-05
forum: Hardware
---

### Post by e.m.fields on 2010-09-05
Hi all.
Might as well be the first one to get this ball rolling, with Maverick 10.10 release coming out in 5 days.

So, have you set up and configured a Wacom tablet in 10.10? Report your experience, good or bad, any lessons or tricks learned, and if possible your xsetwacom config files (if any?).

I'm using Maverick Alpha 3, and haven't had luck getting some configuration settings with xsetwacom.  Getting error message:

```
Note: The "core" keyword is not supported anymore and will be ignored.
```

So, no more "core key settings".  Apparently, I don't know how to set a non-alphanumeric character anymore. 

Anyone have any insight into this issue?

Post your results/insights/troubles here!

---

### Post by alexandre_bastien on 2010-10-16
Same problem. And the four buttons on the pad are not working anymore in Maverick. It seems that only key listed in this works.
```
xsetwacom list mod
```
Let me know if you find a workaround.

---

### Post by Favux on 2010-10-16
What's happening is core is deprecated in Xserver's 1.7 and higher.  So you just use "key whatever".

alexandre,

What kind of tablet do you have?

---

### Post by EseNoy on 2010-10-20
Working now, after re-compiling the drivers.

I'm triying to calibrate the tablet because it don't reach the lower border of the screen -_-' , any idea?

---

### Post by Favux on 2010-10-20
You can probably use xinput calibrator:

[https://launchpad.net/~tias/+archive/xinput-calibrator-ppa](https://launchpad.net/~tias/+archive/xinput-calibrator-ppa)

[http://www.freedesktop.org/wiki/Software/xinput_calibrator](http://www.freedesktop.org/wiki/Software/xinput_calibrator)

---

