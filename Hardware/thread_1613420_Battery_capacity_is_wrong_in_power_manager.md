---
title: "Battery capacity is wrong in power manager"
date: 2010-11-04
forum: Hardware
---

### Post by The Foz on 2010-11-04
On my Acer 5670 laptop (running Ubuntu 9.10), the gnome-power-manager has the wrong value for the battery capacity. When I open the power history, it shows the battery at about 9% charge when it is full.

I have done some battery discharge tests to confirm that the battery itself is fine. It just seems that there is a wrong value in a configuration file somewhere. The laptop hardware is perfectly able to tell when the battery is charged - there is a lot that goes from amber to green when the battery is charged.

This doesn't sound like a major problem, but it does probably mean that the system will automatically suspend when there is actually still plenty of power left. 

Since I am about to start using it for business trips, I would like to fix this problem. Does anyone know how to tell the gnome-power-manager the correct battery capacity? I guess it is one of the many configuration files scattered around the system, but I have been unable to find it. There seems to be no GUI access to this setting.

---

### Post by The Foz on 2011-08-19
Bump.

---

