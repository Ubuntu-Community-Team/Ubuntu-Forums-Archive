---
title: "mga under horay"
date: 2005-04-08
forum: Hardware &amp; Laptops
---

### Post by mdelves on 2005-04-08
Have been playing around abit to get dual head working on my matrox g400 card. I have downloaded the mga drivers from the matrox site and these are the ones I have used on other distros and got it to work properly.

The main problem is that the default xorg packages are missing the I2C section. Thus when the mga and mga_hal drivers are loaded, I get unresolved symbol issues.

Apart from that, I am pleased with the way that ubuntu is put together and will continue to use it for the next little while.

Thanks and God bless,
Matthew Delves

---

### Post by mdelves on 2005-04-08
here are the errors from /var/log/Xorg.0.log

--
Symbol xf86I2CProbeAddress from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Symbol xf86I2CProbeAddress from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Symbol xf86DestroyI2CBusRec from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Symbol xf86DestroyI2CBusRec from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Symbol xf86DestroyI2CBusRec from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Symbol xf86I2CWriteByte from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Symbol xf86I2CWriteByte from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Symbol xf86I2CWriteByte from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Symbol xf86I2CWriteByte from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
Symbol xf86I2CWriteByte from module /usr/X11R6/lib/modules/drivers/mga_drv.o is unresolved!
--

It appears to most likely be an issue relating to I2C, to the best of my knowledge this is a kernel issue aswell as xorg, though I did a modprobe i2c_core which was successful, though it didn't resolv the issue.

Does xorg need to be recompiled with the correct options or are there packages out there with the required symbols.

Thanks and God bless,
Matthew Delves

---

### Post by holzel on 2005-04-21
apt-get install xserver-xfree86 did the trick for me. As far as I found out, mgadrv4.1 has no support yet for xorg 6.8.2. Maybe I shall switch back to X.org later, but for now I have my Dual Screen up and working.

---

### Post by mindhaq on 2005-06-16
[QUOTE=holzel]apt-get install xserver-xfree86 did the trick for me. As far as I found out, mgadrv4.1 has no support yet for xorg 6.8.2. Maybe I shall switch back to X.org later, but for now I have my Dual Screen up and working.[/QUOTE]
Did you get any other benefits out of that change, like any speed enhancements? I use the 6.8.1 drivers in 6.8.2, and this seems to work, except for some problems with playing video, but that has probably other reasons.

---

