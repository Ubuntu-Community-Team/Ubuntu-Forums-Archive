---
title: "ATI driver problem"
date: 2012-10-11
forum: Hardware
---

### Post by Herbalist on 2012-10-11
"Aditional Drivers" utility in "System Settings" i found there 2 proprietary drivers:

ATI/AMD proprietary FGLRX graphics driver (post-release updates)
ATI/AMD proprietary FGLRX graphics driver
when i activate first, it shows me error and it wont install. when i activate second, installs fine and asks for restart and after i restart graphics are slow and choppy, and youtube vids are slower then when was with no driver.

Graphics card : ATI Mobility Radeon HD 4500 Series

---

### Post by Herbalist on 2012-10-12
bump..

---

### Post by wanderingshaodw on 2012-10-15
> **Herbalist said:**
> "Aditional Drivers" utility in "System Settings" i found there 2 proprietary drivers:

ATI/AMD proprietary FGLRX graphics driver (post-release updates)
ATI/AMD proprietary FGLRX graphics driver
when i activate first, it shows me error and it wont install. when i activate second, installs fine and asks for restart and after i restart graphics are slow and choppy, and youtube vids are slower then when was with no driver.

Graphics card : ATI Mobility Radeon HD 4500 Series

I have a similar issue with the ATI Radeon HD 6670 on a Desktop running 12.04.  I have tried installing drivers from ATI including beta and all work fine except for the splash screen I see black and white lines but once in I am in the GUI all works fine.  Hoping someone knows how to remedy this problem.  Alternatively you can go to ATI site and download thier driver not the beta unpackage it, and right click the file go to permissions and then check the box to allow to run.  Then you can do a gui install from there.  See if that helps the choppy vids etc.  If anyone has seen my issue please let me know only happens on proprietary drivers.

---

### Post by Yellow Pasque on 2012-10-15
Note that ATI/AMD dropped support for RadeonHD 4000-series in their proprietary driver after Catalyst 12.6 (fglrx 8.961). It is best to use the open-source radeon driver that was installed by default.

---

