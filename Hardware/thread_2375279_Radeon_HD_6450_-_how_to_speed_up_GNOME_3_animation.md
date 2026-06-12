---
title: "Radeon HD 6450 - how to speed up GNOME 3 animations using this card and radeon driver"
date: 2017-10-23
forum: Hardware
---

### Post by Djzn.BR on 2017-10-23
Last night I've installed 17.10 on a machine with HD 6450 (CAICOS).
It's pretty alright, though I notice that Gnome Shell is having stuttering on animations.
Is there a workaround to get rid of those stutters?
Or is there a 'radeon' driver tweak setting to speed things up?

It happens on Xorg and Wayland, same thing.

Thanks.

---

### Post by mastablasta on 2017-10-25
swtiches are documented in xorg radeon website. [https://www.x.org/wiki/RadeonFeature/](https://www.x.org/wiki/RadeonFeature/)

but you need to know what is causing the stuttering in the first place. since i don't know of a good way i would run Phoronix test, and see where the deficiencies are.

another option is to try out a different desktop such as KDE (in live session) to see if the issue is only present on Gnome. after all they use different methods to draw windows on screen.

---

### Post by Djzn.BR on 2017-10-25
Thanks, I will check that.

---

