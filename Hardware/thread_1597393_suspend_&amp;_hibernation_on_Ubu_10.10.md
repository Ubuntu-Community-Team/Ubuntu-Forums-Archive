---
title: "suspend &amp; hibernation on Ubu 10.10"
date: 2010-10-15
forum: Hardware
---

### Post by rohrbach on 2010-10-15
on my device - ASUS P5Q Deluxe, Intel Core 2 Duo, GeForce 8800, 4GB RAM, USB keyboard and mouse never had problems with suspend and hibernation in Ubuntu. Until the latest version 10.10. Both before and after installing the proprietary Nvidia drivers, the system enters the sleep and hibernate but I can not wake up properly. Specifically, while it looks as it starts up, but not fires up the X server. Oddly - operate only CTRL + ALT + F1-12. You can switch to the text cosole, see the "incentive" to sign but other keys do not work and nothing can be entered. Not working CTRL + ALT + DEL as well, so you need to turn off the system power.

Please for some advanced help

---

### Post by koni-ubuntu on 2010-10-15
Lenovo T400 with Intel Integrated Graphic Card;
Since upgrading from Kubuntu 10.04 32bit to 10.10 hibernate stopped working. Suspend works without problems. It seems the X Server terminated unexpectedly.

---

### Post by ianmillington on 2010-10-15
@koni-ubuntu - Hibernate is fine on my dell 630m laptop with intel graphics, although suspend has never worked properly for me.

Is it possible that the power management seeting that you had in 10.04 have been wiped on the upgrade to 10.10? Check in system setting/power management.

@rohrbach - I don't know the answer to your issue I'm afraid. However, I recommend that instead of hitting the power switch you hold down alt+sysreq and type reisub to do a soft reboot.

---

### Post by rohrbach on 2010-10-15
> hold down alt+sysreq and type reisub to do a soft reboot.

not working already - typing "print screen + alt" not giving any results.

---

### Post by ianmillington on 2010-10-15
The alt+sysreq key combination will not of itself do anything. But keep them held down while you slowly type reisub. Each time you then press one of the letters something will happen and on the final one the machine will reboot.

Fuller info is here

[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

---

### Post by koni-ubuntu on 2010-10-18
@rohrbach: Is it possible that the power management setting that you had in 10.04 have been wiped on the upgrade to 10.10? Check in system setting/power management.
I played around, but no changes.
What worked was to use a Lucid kernel:
2.6.32-25-generic

Hibernate now works as before. Sleep works aswell,
but already before.
Will stay with this kernel version for the moment!

---

### Post by UrbenLegend on 2010-10-19
I am getting the same issue in Kubuntu 10.10. Is it a framebuffer problem?

---

