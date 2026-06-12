---
title: "Nvidia Geforce FX 5700LE Problem"
date: 2010-03-22
forum: Hardware
---

### Post by jleppers on 2010-03-22
Ok, i have been working at this for 7 hours and no luck i am running ubuntu 8.10 im trying to use an nvidia gefroce FX 5700LE graphics card and i keep getting errors like this

(EE) NV(0) : No valid FB address in PCI config space
(EE) Screen(s) found, but none have usable configurations 

I have tried to install the graphics driver from nvidia but it keeps telling me " installation failed unable to load kernel module nvidia.ko" 

Can someone please help, thanks!

---

### Post by Fafler on 2010-03-22
You can't use the newer Nvidia drivers. Support for the FX series stopped with version 173. What about using the opensource nv or noveau driver?

---

### Post by jleppers on 2010-03-22
i went to system administration and selected hardware drivers and it detected the nvidia driver 173 i installed it and now when it boots it says unable to load the nvidia module then it goes ....Aborting...

on a different machine i tried an Visiontek Radeon HD 2400 Pro and also got an error.

---

