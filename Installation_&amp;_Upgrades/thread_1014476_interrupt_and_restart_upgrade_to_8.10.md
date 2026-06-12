---
title: "interrupt and restart upgrade to 8.10"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by DavidFourer on 2008-12-17
Can I do an on-line upgrade to 8.10 and intentionally interrupt the install?  This may sound kooky, but my trusty Dell Inspiron laptop has a cooling issue that I never solved.  An hour of download followed by and hour of configuring/installing the upgrade would be to risky.  If I can interrupt and run
cat /proc/acpi/thermal_zone/* 
then I would feel safer.  I suppose better to leave well enough alone.

---

### Post by iponeverything on 2008-12-17
:) put it in the fridge while its doing the upgrade.


seriously -- I have an interrupted upgrade plenty of times during the package download phase. The actual package installation phase can't be interrupted without the strong possibility that the system will be mucked. (was going to say inconsistent state, but mucked might be more precise)

---

### Post by DavidFourer on 2008-12-17
> **iponeverything said:**
> :) put it in the fridge while its doing the upgrade.Here in Chicago, I can put it outside my window.  I'm considering it.

---

