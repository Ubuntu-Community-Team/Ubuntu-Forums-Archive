---
title: "Overclock CPU with nvidia chipset"
date: 2015-01-23
forum: Hardware
---

### Post by lambdafox on 2015-01-23
My chipset is compatible with the ntune program.  There is no option in BIOS. As I understand it, there is no PLL with this type of system.  The clock is on the chipset's south bridge instead.  I am a linux newbie, so sorry if this is stupid...  Can I use WINE to run nTune?    What if I run it within my XP virtual machine (QEMU)?  Other options?

---

### Post by Yellow Pasque on 2015-01-23
ntune requires low-level access, so I doubt it will work with wine and it won't work in a VM (much like updating the BIOS doesn't work with those methods).

From quick Googling, it looks like nvidia had plans to bring ntune to Linux, but never went through with it (probably because they left the x86 chipset business).

---

