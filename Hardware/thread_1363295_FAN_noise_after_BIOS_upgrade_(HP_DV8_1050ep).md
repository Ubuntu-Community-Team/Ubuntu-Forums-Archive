---
title: "FAN noise after BIOS upgrade (HP DV8 1050ep)"
date: 2009-12-24
forum: Hardware
---

### Post by inoxllor on 2009-12-24
HP DV8 1050ep i7 18,4

Due to  Startup Error - System Temperature (90D) bug related to ubuntu 9.10 instalation,I upgraded my BIOS firmware to F.12 (released 2009-12-08),  that BUG was corrected but now the FAN is ALWAYS ON, making to much noise.

- Disabling the "FAN always on" option on the BIOS setup doesn´t make any difference.
- The BIOS update utility doesn´t allow me to downgrade back to the previous BIOS version.


So I am stuck with this horrible noise under windows 7 and under ubuntu... Any Ideas to solve this issue?

---

### Post by gambit73 on 2010-01-27
Hi inoxllor,

I have a dv8-1080e and had the same problem described by you.
I upgraded to F.12 and my fan got blowing to the max too, though the issue concerning booting up with an error about the temperature (90D) was solved.

The solution to let the fan run on a normal speed is to reset the bios settings to default.
Good luck and I hope this will solve your issue too.

Note: this fan speed issue is not related to linux or ubuntu, it occurred on the pre-installed win7-x64 OS too.

Gambit.

---

### Post by inoxllor on 2010-01-27
Thks. :D
HP released a new BIOS F15e and issue is gone.

---

