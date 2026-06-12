---
title: "Gateway laptop doesnt let me live boot my USB"
date: 2012-09-24
forum: Hardware
---

### Post by TheRacerX on 2012-09-24
i just bought a Gateway NV7 Series laptop and when i try to boot Ubuntu off my thumb drive it will not work, i dont know if maybe the BIOS doesn't support USB booting or if its a hardware issue. Anyone has any ideas?

---

### Post by einonm on 2012-09-25
You'll need to enter your BIOS menu and take a look around.

There should be a boot order menu, and the relevant USB device should be higher in the menu than your current OS's HDD for booting to work (the BIOS will boot the first valid OS it finds in the list...).

Also, you could try and select a separate boot menu if there is one, and choose the USB drive if it is listed.

---

