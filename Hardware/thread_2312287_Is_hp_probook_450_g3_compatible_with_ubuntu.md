---
title: "Is hp probook 450 g3 compatible with ubuntu ?"
date: 2016-02-03
forum: Hardware
---

### Post by mehdi10 on 2016-02-03
Is hp probook 450 g3 compatible with ubuntu ?
Probook 450 g3 has amd radeon

---

### Post by Vladlenin5000 on 2016-02-03
Please post a link with the product specs. All the results I got from Google do NOT support the "Probook 450 g3 has amd radeon" assertion, i.e., all point to different Intel CPU/GPU configurations, not AMD.
Either way, why wouldn't it be compatible?

---

### Post by Yellow Pasque on 2016-02-03
The manual specifically lists Ubuntu Linux. A discrete Radeon R7 M340 was an option which may cause some issues. I still see users struggling with Intel/AMD hybrid graphics setups like this one.
At any rate, you'll need Ubuntu 15.10 for best compatibility. 16.04 will probably work even better since this is very new hardware.

---

### Post by profshiny2 on 2016-04-20
Did anyone get a chance to try this out? I'm looking at one for my wife and she won't want to use it unless it will run Ubuntu. I'm not seeing much online about using the M340 under Linux.

---

### Post by mastablasta on 2016-04-21
m340 will now have new opensource driver only called amdgpu. the support for these chips should improve towards the end of the year.

another option is to install an older version on it and use proprietary drivers (fglrx).

what is the exact model number of the laptop (including the stuff in brackets). because this US pages shows only intel GPU: [http://www8.hp.com/us/en/products/laptops/product-detail.html?oid=7834555#!tab=models](http://www8.hp.com/us/en/products/laptops/product-detail.html?oid=7834555#!tab=models)

anyway with full info you can check it's Linux compatibility. it might be Linux certified or even come Linux preloaded.

> AMD Dynamic Switchable Graphics technology requires either an AMD "A" series APU or an Intel processor, plus an AMD Radeon™ discrete graphics configuration and is not available on FreeDOS and Linux OS. With AMD Dynamic Switchable Graphics technology, full enablement of all discrete graphics video and display features may not be supported on all systems (e.g. OpenGL applications will run on the integrated GPU or the APU as the case may be).[FONT=HPSimplifiedLight][SIZE=1][FONT=HPSimplifiedLight][SIZE=1][/SIZE][/FONT][/SIZE][/FONT]

---

