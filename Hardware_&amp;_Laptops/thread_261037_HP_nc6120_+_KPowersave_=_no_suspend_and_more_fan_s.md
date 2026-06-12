---
title: "HP nc6120 + KPowersave = no suspend and more fan spinning ?"
date: 2006-09-19
forum: Hardware &amp; Laptops
---

### Post by ZiZi on 2006-09-19
I've recently installed powersaved + KPowersave to replace my KLaptop, because the Ubuntu wiki encouraged me to do so.

I like its clean interface and configuration, after a fresh start the computer is completely quiet, centrino speedstep working like a charm.

However, after a while, the fan starts to spin moderately, but for no apparent reason, which is annoying. Does someone have some experience with the HP notebooks and KPowersave?

I'm even thinking about going back to KLaptop + friends, that worked well enough. Tough luck, the powersaved approach seemed to be a somewhat 'cleaner' solution...

The other thing, which is not such a problem to me, is that my machine is not able to wake up from neither Suspend-to-disk nor Suspend-to-RAM state. All I've got is a fresh reboot, which is (according to the documentation) caused by some incompatible drivers. No idea which ones those might be :(

---

### Post by ZiZi on 2006-09-19
This is the output of "powersave -T". The fan should not be on, because no Active temperature limit is reached, but it IS in fact on.
```
Thermal Device no. 0:
Temperature: 40
Critical: 110
Passive: 110
Thermal Device no. 1:
Temperature: 26
Critical: 102
Passive: 60
Thermal Device no. 2:
Temperature: 37
Critical: 103
Thermal Device no. 3:
Temperature: 37
Critical: 102
Passive: 100
Active 0: 80
Active 1: 70
Active 2: 60
Active 3: 50
```

---

