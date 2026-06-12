---
title: "missing ac events from acpi on Sony laptop"
date: 2005-12-01
forum: Hardware &amp; Laptops
---

### Post by thebrother on 2005-12-01
the acpi ac module on my laptop isn't generating events when I plug/unplug the power supply.  /proc/acpi/ac_adaptor/state shows the correct state (on-line or off-line) but no events appear.  If I switch it on without the psu then /etc/init.d/acpi-support turns on the power saving (as it polls the ac state).   If I unplug the power supply after I've powered the laptop on it doesn't switch on all the relevant power saving options and therefore dies quite quickly.

Does anyone have any suggestions as to what might be wrong?

The laptop is a Sharp FS2158.

---

### Post by kairu0 on 2005-12-01
Is it Sharp or Sony?

---

### Post by thebrother on 2005-12-03
It's definately a Sharp PC-FS2518

---

