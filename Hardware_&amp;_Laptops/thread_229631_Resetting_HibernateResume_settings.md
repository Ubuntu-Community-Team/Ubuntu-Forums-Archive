---
title: "Resetting Hibernate/Resume settings"
date: 2006-08-04
forum: Hardware &amp; Laptops
---

### Post by diesis on 2006-08-04
Hello,
I had hibernate and resuming on my Compaq Evo N800v working good.
After mixing up kubuntu and ubuntu i cant' resume correctly anymore.
I get keyboard usb and video unrepsonsive, but sshing remotely to the machine works.

How do I reset all hibernate / resume settings (acpi and gnome-power-manager, I suppose) to thei clean install defaults ?

Any other way to try ?

Thnak you !!!

---

### Post by diesis on 2006-08-08
Hi have solved.
I had installed powersaved replacing powernowd, and powersaved overrides plain hibernating, but powersave does not work correctly on my machine.

I've reinstalled powernowd, purged powersaved, and everyting now works.

---

