---
title: "Monitor rotation problem"
date: 2014-09-18
forum: Hardware
---

### Post by acecchin on 2014-09-18
Hi to all,
 I have an [AMD/ATI] Caicos XT [Radeon HD 7470/8470 / R5 235 OEM] VGA controller with two monitor connected.

Until yesterday I was using the default open source X.Org drivers and everything was working fine, with my primary monitor horizontal and the secondary one rotated as vertical.

Then I try the proprietary drivers and everything goes wrong!

I restore the default drivers and I reconfigure the Displays behaviors but when I try to rotate my secondary display the monitor (that is not changed!) found no signal.

I try to rotate clockwise and counterclockwise but nothing changed: my secondary monitor lost the signal. What is going wrong?

I try also using xrandr from console but nothing:

```
$ xrandr --output DisplayPort-0 --rotate right
```

has the same result as the GUI interface.

Thank you very much.

---

### Post by acecchin on 2014-09-18
Solved by myself.

xserver-xorg-video-ati was **not** installed.

In Software & Updates | Additional Drivers the corresponding radio button was selected but the .deb wasn't installed! This seems to be a bug!

---

