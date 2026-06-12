---
title: "Batttery not recognised on boot. Suspend and login fixes the issue though."
date: 2011-01-22
forum: Hardware
---

### Post by graham73may on 2011-01-22
Hi

I am using the Gnome Power Management tool that came preinstalled with ubuntu 10.10.

When I turn my laptop on (Acer Aspire One) the symbol in the tray (which I had to set to ALWAYS show) is just of a plug. This happens whether I am on AC or not, and also if there is a battery present or not. 

One thing I have noticed is that in the power manager there is only "Generel" and "On Mains Power". There is no "On Battery Power". Why is this?

I have found that if I suspend ubuntu then log back in, it recognises that I am only on battery, and everything works accordingly (but STILL no on battery power tab!).

Also if i plug the AC adapter in it realises that something is going on and the icon changes to a battery charging. (but STILL no battery tab).

I can view battery info with fn + f1 and also if I click on the icon to get its info, it shows me all the details...

Does anyone know of a what would be causing this issue? How can I fix this? 

Thanks!

---

### Post by graham73may on 2011-01-24
bump 

Does anyone know of any similar battery issues? or ANYTHING?

---

### Post by graham73may on 2011-04-03
SOLVED:

I made a startup application, with the command:

> cat /proc/acpi/battery/BAT0/state

And now it checks the battery state on boot, which gives gnome-power-manager a kick up the backside to show the battery state.

After months of logging in and out, this has made me VERY happy!

---

