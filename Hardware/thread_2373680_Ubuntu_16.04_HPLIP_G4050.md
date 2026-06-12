---
title: "Ubuntu 16.04 HPLIP G4050"
date: 2017-10-08
forum: Hardware
---

### Post by bostonblackie2 on 2017-10-08
I want to use a HP G4050 scanner with Ubuntu16.04. I search the different forums and found two (2009 and 2011). Both replies that the G4050 was not support. Since it 2017 I maybe it is supported now? If it is can someone point me to the installation manual.

---

### Post by DuckHook on 2017-10-08
Welcome to the forums, bostonblackie2:

The best way is simply to test drive it with a LiveUSB (if you don't already have Ubuntu installed). If Ubuntu is already installed, then just plug in the scanner and see.

To my knowledge, Ubuntu comes with all the drivers needed to run scanners. Since the HP G4050 is rather old, if it wasn't supported in the past, then it is unlikely to be supported now. However, you can't really tell about support without simply trial running it.

Here is the SANE support page detailing all makes and models: [http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD](http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD)

Unfortunately, yours doesn't appear on the database, although this doesn't mean that it won't work. The only way to really find out is to try it.

It is important to note that standalone scanners do not use HPLIP. HPLIP is only used for printers or all-in-one machines with a printer component. Therefore, you won't find the driver in HPLIP.

---

