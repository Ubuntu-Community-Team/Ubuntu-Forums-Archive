---
title: "2 problems with Dell Inspiron under Breezy."
date: 2005-11-24
forum: Hardware &amp; Laptops
---

### Post by polpak on 2005-11-24
The first is an error that keeps showing up in dmesg:

[4297801.327000] cpufreq: change failed with new_state 0 and result 0
[4297805.235000] cpufreq: change failed with new_state 1 and result 0
[4297817.026000] cpufreq: change failed with new_state 0 and result 0
[4297818.925000] cpufreq: change failed with new_state 1 and result 0
[4297903.565000] cpufreq: change failed with new_state 0 and result 0
[4297906.504000] cpufreq: change failed with new_state 1 and result 0
[4298025.253000] cpufreq: change failed with new_state 0 and result 0
[4298043.288000] cpufreq: change failed with new_state 1 and result 0
[4298063.929000] cpufreq: change failed with new_state 0 and result 0

etc....


I'm not sure what the issue is there. The second is more frustrating. Periodically the mouse pointer will jump about the screen and click randomly (bringing up the trash, the desktop, etc). I have a logitech mouseman plugged into the PS 2 port, and am primaraly using that for curser movement which may have something to do with it.

Here's the errors that show up in dmesg when it happens:

[4297796.890000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 2 bytes away.
[4297801.327000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.

etc.

Any ideas?

I'm trying to get this set up and working for my brother in-law as an introduction to a non-windows world. But these minor problems (specifically the mouse one) really detract from the experience.

Thanks

---

### Post by invalid on 2005-11-24
Try
```
sudo killall powernowd
```

Cheers,
Cb

---

