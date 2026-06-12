---
title: "replaced cpu with higher model"
date: 2011-05-08
forum: Hardware
---

### Post by ryadav on 2011-05-08
i decided to update my cpu from athlon x64 dual-core to a phenom II quad-core, will this affect my current linux system stability? should i do a clean install when my new cpu is put in??

---

### Post by silkworm2.5 on 2011-05-08
As long as the processor supports 64 bit, it should not affect your linux system.

---

### Post by ryadav on 2011-05-09
thanks, that is what i thought, still better to ask =)

---

### Post by mastablasta on 2011-05-09
> **silkworm2.5 said:**
> As long as the processor supports 64 bit, it should not affect your linux system.
 
 
and it does. as well as 32bit
 
In linux drivers are part of kernel (core) and are loaded/configured/used automaticly on boot.
 
the only instability would be if you replaced/upgraded a device with proprietary drivers (for example graphcis card). on that case both in Windows as well as Linux require you to uninstall previous drivers and then perform the hardware upgrade. after that is done boot into system and install new drivers (in this part you might need to boto into safe mode or this is done automaticly for you by the OS).
 
processors usually don't require any additional proprietary drivers.

---

