---
title: "compaq presario 2100"
date: 2009-07-30
forum: Hardware
---

### Post by moparmudder420 on 2009-07-30
hi, i have installed ubuntu 9.04 on my presario 2100 laptop and need help on finding the driver for ubuntu, or ndiswrapper. thanks

---

### Post by mdmarmer on 2009-07-30
your laptop has a broadcom 4306 wireless card.  Either ndiswrapper with bcmwl5.inf and the .sys file from Windows or the native drive (need to install fwcutter to use the native driver) should work.  Make sure both drivers are not loaded.  Use 32-bit driver for 32-bit install, 64-bit driver for 64-bit install

See here [http://ubuntuforums.org/showthread.php?t=25683&highlight=4306](http://ubuntuforums.org/showthread.php?t=25683&highlight=4306)

Mike

---

