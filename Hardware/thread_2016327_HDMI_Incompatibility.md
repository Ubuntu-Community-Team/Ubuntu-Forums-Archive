---
title: "HDMI Incompatibility"
date: 2012-07-04
forum: Hardware
---

### Post by MartianTek3 on 2012-07-04
Only thing about Linux that bugs me is the HDMI output 

We have an HDTV and I connected my Dell laptop via HDMI cable 

After it was connected nothing happened Kubuntu didn't even recognize the HDTV 

The HDTV read 'No Signal'

Is there some command i can do to Activate video HDMI output in Linux?

Graphics Card: Nvidia GT540 M

Any help will suffice. 

Sincerely,
MartianTek3

---

### Post by ahallubuntu on 2012-07-04
On my Dell laptop, I have to hit Fn + F2 to toggle the video mode between laptop LCD and external monitor.

My media center box running Ubuntu is connected to a flat screen TV using HDMI and works great.

---

### Post by cortman on 2012-07-04
With the HDMI monitor plugged in, what's the output of

```
xrandr
```

You may need the Nvidia proprietary driver.

---

