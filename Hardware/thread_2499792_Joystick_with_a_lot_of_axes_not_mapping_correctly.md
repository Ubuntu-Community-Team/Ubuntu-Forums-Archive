---
title: "Joystick with a lot of axes not mapping correctly"
date: 2024-08-10
forum: Hardware
---

### Post by carmiac on 2024-08-10
I have a joystick with a lot of axes and am having difficulties getting it to work correctly in Ubuntu.

Specifically, I have a VKB GNX with the GNX-THQ add on.  It works fine in Windows, though it shows up as multiple joysticks, presumably to get around the 8 axes per joystick windows limit.

In Ubuntu 22.04, it mostly works, but shows up as one joystick (/dev/input/js2) with 10 axes and 80 buttons. This is almost correct, except that the main grip Y axis and the rightmost throttle on the THQ both are mapping to Axis 0.  There should be 11 axes total so that they don't overlap.  How do I fix this?

---

