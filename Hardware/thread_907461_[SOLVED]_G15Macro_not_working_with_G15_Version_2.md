---
title: "[SOLVED] G15Macro not working with G15 Version 2"
date: 2008-09-01
forum: Hardware
---

### Post by R3N3G4D3 on 2008-09-01
I have g15daemon and g15composer installed and working fine with my g15 version 2. G15macro, however, does not seem to do anything (all 3 installed from Ubuntu 8.04 debs). When started, it does flash something on the LCD for a split second and M1 key lights up (and stays lit up while g15macro is running). But the G keys or the M keys don't seem to be doing anything (I have read the README about how to program the G keys). I've noticed that g15macro is expecting 18 keys instead of 6 as with the new g15, could that be the problem? I figured missing keys would just get ignored. I've tried to connect my old g15 version 1 instead, but g15daemon would refuse to restart, claiming that no g15 device was found, now claiming the same thing with my version 2. I think it needs a full PC reboot to re-detect it, so I will try that when I get the chance (I have rebooted after installing g15macro btw). Did anyone experience similar problems?

---

### Post by R3N3G4D3 on 2008-09-04
I connected version 1 of the keyboard, and restarted the computer. G15macro worked flawlessly with version 1. I guess I'll try looking at the source code for g15macro and see if I can figure the problem out and update it. It seems to be relying on X11 extensions, and unfortunately I have no experience at all with those.

---

### Post by R3N3G4D3 on 2008-09-05
The issue is resolved. Apparently versions 1.9.0 of g15daemon and 1.2.3 of libg15 (which are the debs used in Synaptic for Hardy) don't see the input from G keys on g15v2 keyboard, when g15daemon is compiled from 1.9.3/1.2.6 source, g15macro works fine. Thanks to Mike Lampard (g15macro author) for helping me solve the problem.

---

### Post by vinx on 2009-03-09
Found the easy solution on another forum.
You can just use the default g15macro without patch, but if you have a version 2 start it as:
g15macro --second

Record a macro:
- Select M1, M2 or M3
- Press MR
- Type the text you want to record
- Press the G-button you want to use for the command
The LCD will tell you now the macro is recorded.

---

