---
title: "printer not working"
date: 2007-12-05
forum: Hardware &amp; Laptops
---

### Post by android6011 on 2007-12-05
I had this working a long time ago, but then i removed ubuntu for awhile. now i have the 64bit version installed and the driver install seemed to go ok, but when i print something the jobs manager says it is processing for a second then it just says stopped. how can i figure out whats wrong?

---

### Post by Friek on 2007-12-06
Maybe the printer was disabled by cups for some reason. You can check this by running 'lpstat -a'. if it's disabled, you can enable it with 'sudo cupsenable printername'.

---

