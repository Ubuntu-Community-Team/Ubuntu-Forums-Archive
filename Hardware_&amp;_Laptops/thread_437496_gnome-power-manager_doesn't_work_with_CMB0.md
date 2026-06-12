---
title: "gnome-power-manager doesn't work with CMB0"
date: 2007-05-08
forum: Hardware &amp; Laptops
---

### Post by mbc2000 on 2007-05-08
I have a Presario 1720US running Ubuntu Feisty.  I previously had Kubuntu Edgy and klaptop worked fine with my battery.  But gnome-power-manager always shows 0%.  I tried the DSDT thing -- decompiled my existing one, 'corrected' the three warnings I got, and reconfigured.  That didn't make a difference.

Anyway, my battery is at /proc/acpi/battery/CMB0.  If I run 'cat state' in that directory, I get:

present:                 yes
capacity state:          ok
charging state:          charging
present rate:            177 mW
remaining capacity:      3555 mWh
present voltage:         16771 mV

This looks like good information to me.  Is this just an issue of gnome-power-manager not looking in the right place?

---

