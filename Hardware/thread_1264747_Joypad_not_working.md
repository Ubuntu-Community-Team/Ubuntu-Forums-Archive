---
title: "Joypad not working?"
date: 2009-09-12
forum: Hardware
---

### Post by xtremesupremacy3 on 2009-09-12
Hello again.

Btw, is it me or is Jaunty much buggier than other versions?

Anyway, I already have posts on ACPI error, my sound will play through headphones and speakers and theres nothing I can do, and now the following (but still will not turn away from Ubuntu ;-)):

I have purchased a joypad to use with ePSXe.
Now playing on epsxe is no problem, and works well...without joypad, but I wanted to use the joypad and well it wouldnt react to changing the settings in the program so I went to check if all is well...anyway, lsusb tells me that the joypad is: GreenAsia Inc. Joystick. (kinda odd since its a joyPAD and it has the name Speedlink on the pad), anyway heres the actual problem:

I wanted to check it using jscalibrator, so i installed it and when I run the program without joypad plugged in, it works with the obvious no joypad plugged in error, and some other errors in the terminal, but it works. However, when I have the joypad plugged in, and run jscalibrator, it just hangs, freezes and does nothing at all...my mouse stops to react, can't do nothing but hard reboot. There are the same errors as when I run it without pad plugged in:
```
GTK warning failed to load module "libcanberra-gtk-module.so": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
```
But that's not just for libcanberra, it also states the same for libgail.so, and libatk-bridge.so

Which is odd, because well I have checked and I have them (or at least according to synaptic.

Please help
lol

Arthur

EDIT: I have just started to play (or attempt to) on the ePSXe, just without the joypad...but I once again got the errors and it wouldnt react to anything.

---

