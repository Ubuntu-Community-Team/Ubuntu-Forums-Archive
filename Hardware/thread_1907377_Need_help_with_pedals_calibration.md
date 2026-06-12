---
title: "Need help with pedals calibration"
date: 2012-01-11
forum: Hardware
---

### Post by ocirne94 on 2012-01-11
Hi all,
I've got a pedals set and I don't manage to calibrate the clutch pedal, while everything else works fine. Inside Joystick configuration (System Settings):

[LIST]
[*]The throttle and brake pedals give raw values ranging from 32767 to -32767 (from fully released to fully pressed).
[*]The clutch pedal, instead, gives a raw value of 0 to -32767 (released to halfway pressed), then jumps to 32767 and descends again to 0 (halfway pressed to fully pressed). Example sequence with jstest, from released to fully pressed to fully released:
[/LIST]
0 -4054 -9797 -17567 -27026 -32767 32767 26687 14188 4729 0 1351 10134 23647 32767 -32767 -20607 -8108 0

[LIST]
[*]These results make impossible to use the clutch pedal for more than halfway: in fact, as racing games use min/max values, if min raw value equals max value 
the clutch isn't even triggered.
[/LIST]
Any ideas?
Thank you very much,
Ocirne

---

### Post by ocirne94 on 2012-01-12
[FONT=Arial Black][SIZE=4][COLOR=DarkGreen]Bump[/COLOR][/SIZE][/FONT]

---

