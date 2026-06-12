---
title: "PlayStation controller adapter not working"
date: 2011-01-23
forum: Hardware
---

### Post by racie on 2011-01-23
Hey everyone.  I have a PSX to PS3 adapter that is confirmed as working in Windows, so I know it's not an issue with the hardware.  However, when I plug it into Ubuntu, none of the buttons work.  Is there some sort of driver I need to install for it or something?  The joystick file /dev/input/js0 is created when I plug it in and lsusb gives:
```
054c:0268 Sony Corp. Batoh Device
```

Any ideas?

---

### Post by racie on 2011-01-23
Okay I solved the problem myself.  If anyone's curious, I think the controller expects me to press the PS button to turn it on like a regular PS3 controller.  The problem is that my PS2 and PS1 controllers don't have a PS button.  Luckily the mode button on the PS2 controller works for that.  If I want to play with the PS1 controller, I first press the mode button on the PS2 controller, then unplug it from the adapter and plug in the PS1 controller.

---

