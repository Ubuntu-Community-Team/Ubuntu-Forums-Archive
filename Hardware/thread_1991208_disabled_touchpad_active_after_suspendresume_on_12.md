---
title: "disabled touchpad active after suspend/resume on 12.04"
date: 2012-05-30
forum: Hardware
---

### Post by krimskrams on 2012-05-30
Hi,
on my Thinkpad x121e I installed Xubuntu 12.04 and disabled the touchpad via Settings -> Settings Manager -> Mouse and Touchpad (xfce4-mouse-settings) only the trackpoint is in use.

Whenever I suspend the system the touchpad is active after resume and I cannot disable it again through the above tool.

Any suggestions?
krimskrams

---

### Post by 2F4U on 2012-05-30
I don't know the X121e, but on my T60 there is an option in the BIOS which allows me to enable/disable trackpoint and touchpad separately. It sounds as if you want to disable the touchpad permanently, so it may be worth to check your BIOS whether such an option exists.

---

### Post by krimskrams on 2012-05-30
Hi,
I know hat BIOS Option Form my Txxx thinkpads, unfortunately the x121e does not allow to disable the touchpad in its BIOS.
Krimskrams

---

### Post by jacobmar1ey on 2012-10-26
I have the same issue on an Asus EeePC 1015PEM.
It includes an ETPS/2 Elantech touchpad. I also cannot disable it after suspend/resume.

A BIOS option wouldn't work in my case, as I only disable it when I plug in an external mouse or am going to be doing significant typing.

I'm on Xubuntu 12.04

**EDIT**
After reading [this bug report]("https://bugs.launchpad.net/touchpad-indicator/+bug/893408"), I found that un/replugging my external mouse, the 'Mouse and Trackpad' utility let me disable my trackpad again. I think the two issues are related (trackpad indicator and this one)

---

