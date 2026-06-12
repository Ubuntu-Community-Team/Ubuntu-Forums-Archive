---
title: "CPU Scaling stopped working"
date: 2010-02-25
forum: Hardware
---

### Post by ridetheteapot on 2010-02-25
hey my laptop was scaling the cpu fine - until after i installed/uninstalled an applet called jupiter.
if your unfamiliar jupiter is a newer applet to help manage power usage on laptops.
I wanted to check it out, but that was a mistake - so far the .deb installer has left little bits of brokenness around my pretty little laptop. (All in all the app itself is nice but i didnt need it so uninstalled.)
The dirty little bugger did not replace my cpufreq governor settings. (maybe all it did was leave scaling_governor in performance mode.)
What does ubuntu use by default to govern cpu frequency?
/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor ?
and what is the default setting ? conservative or ondemand?

also is it as simple as setting scaling_governor for cpu0 & cpu1 on a dualcore?

_________EDIT__________
ok i just went ahead and set cpu0&1 to ondemand
i am still curious if this was the original setting though.
also a little curious if the cores can be set to different values and why would you.

-> final ->
/etc/init.d/ondemand is disabled by jupiter. it sets scaling_governor to ondemand on startup.

---

