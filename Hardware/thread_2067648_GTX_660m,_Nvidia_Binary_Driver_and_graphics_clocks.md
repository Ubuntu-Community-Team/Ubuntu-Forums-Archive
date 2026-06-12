---
title: "GTX 660m, Nvidia Binary Driver and graphics clocks"
date: 2012-10-07
forum: Hardware
---

### Post by HrKristian on 2012-10-07
My laptop GPU in unable to clock above 405MHz, I've tried several different Nvidia binary drivers, but they're all the same...

In nvidia-settings PowerMizer reports the Graphics Clock of all three states to be at 405, while Memory Clock ranges from 405 to 2500.

The laptop is an ASUS G55VW, it is not Optimus enabled.

Any solution to this? Or do I have to wait for Nvidia to release a driver that works?
(CoolBits hasn't worked since Fermi, this is Kepler.)

---

### Post by james.christie on 2012-10-21
It's not a solution but I have the exact same issue here. I have submitted a bug report here: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1069444](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1069444)

---

### Post by james.christie on 2012-11-06
According to an nVidia engineer, Kepler device clock reporting is totally borked atm, but the card should be running at the correct frequencies for each performance level, the VBIOS not the driver determines those.

---

### Post by HrKristian on 2013-01-23
That'd be nice but frankly, I don't think that's the case here...

I've tried playing various games and the GPU just can't handle anything demanding.

Nvidia just released 310.32 and I'm going to see if they fix the problem...

---

