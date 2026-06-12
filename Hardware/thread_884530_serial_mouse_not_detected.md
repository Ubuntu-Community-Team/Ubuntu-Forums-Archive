---
title: "serial mouse not detected"
date: 2008-08-09
forum: Hardware
---

### Post by bugsvoid on 2008-08-09
hello all,

Previously I had installed gusty on my machine (Intel P4/264MB) which has 3 button serial mouse. The installation failed to detect my mouse. But i was able to run ```
cat /dev/ttyS0
``` and got characters printed on the console. After updating xorg.conf with ```
Option "Device" /dev/ttyS0
```, I got my mouse working.

Now I have installed hardy. Again, the installation process was not able to detect my mouse. My ```
xorg.conf
``` file has no entries for ```
Option "Protocol"
``` & ```
Option "Device"
``` in Pointer section. I tried to ```
cat /dev/ttyS[0-3]
``` & /dev/input/mouse0 from the console, but now it doesn't display anything if i move the mouse. Adding entries for Device & Driver in xorg.conf hasn't helped as expected.

So how do I get my mouse working here?

TIA.
~ bugs

---

