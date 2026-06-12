---
title: "Two joysticks treated as one"
date: 2007-05-30
forum: Hardware &amp; Laptops
---

### Post by CapitalT on 2007-05-30
Hi all.

I have two joysticks that share the same usb plug (I'm not using a usb hub) and the system show only one joystick: /dev/input/js0. This joystick is controlled by any of the two joysticks.

After investigation it appeared that it takes input from each joystick one-at-a-frame. E.g. if you press start on joystick1 and select on joystick2 it  will input start-select-start-select...

I know this sound confusing, but they work as two under Windows. Please help!

---

