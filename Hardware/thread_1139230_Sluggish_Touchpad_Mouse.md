---
title: "Sluggish Touchpad Mouse"
date: 2009-04-26
forum: Hardware
---

### Post by rykel on 2009-04-26
Hi,

I am testing out Jaunty on Asus EeePC 4G (yes, the older 7" screen model) and I seem to get a sluggish mouse cursor that is unresponsive when I am at the Netbook Launcher Desktop. This behaviour does NOT take place if the mouse is moving on Firefox, Synaptic Package Manager or any other window.

Is there some bug in the Netbook Launcher Desktop that conflicts with the mouse cursor?

Thanks for advising!

---

### Post by syaman on 2009-04-27
Hi I resolved this issue on my EEE PC 701 4G by doing the following (as advised as another fellow forum user)

Add the following Option to /etc/X11/xorg.conf

Section "Device"
  Identifier    "Configured Video Device"
  Option "AccelMethod" "UXA"
EndSection

---

### Post by wvreeuwijk on 2009-04-29
Great syaman, that just did it!! I had the same problem as Rykel and the same netbook as yours

---

### Post by HeegeMcGee on 2009-05-14
This seemed to resolve the mouse issue on my Asus EEE 900. The effects are still sluggish, but the mouse is responsive, so it's mostly usable.

We really do need the option to disable the effects - not all netbooks have enough horsepower.

---

### Post by rykel on 2009-05-24
Hi,

I found another way to permanently solve this problem altogether - downgrade back to Intel driver 2.4. Just follow the steps here:

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

Hope that helps!!

---

### Post by Papasean on 2009-07-30
Have used your fix. Worked first time... Thanks

Papasean

---

