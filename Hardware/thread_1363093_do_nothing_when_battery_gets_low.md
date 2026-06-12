---
title: "do nothing when battery gets low"
date: 2009-12-24
forum: Hardware
---

### Post by santiagozky on 2009-12-24
Hello,

I want to prevent ubuntu from doing anything when the battery power gets very low. This because my battery is old and if I unplug the AC just for 3 seconds it will try to hibernate (and don't wake up....).

The gnome power wizard does not have an option for doing nothing when "battery power is critically low"

Anyone knows how to do this?

Thank you.

---

### Post by mikewhatever on 2009-12-24
Open gconf-editor by typing that in Terminal, navigate to apps/gnome-power-manager/actions, and chhange the critical_battery value to 'nothing'.

---

### Post by santiagozky on 2009-12-25
thank you very much

---

