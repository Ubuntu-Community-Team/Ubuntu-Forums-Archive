---
title: "Lid open/close not registering"
date: 2007-05-20
forum: Hardware &amp; Laptops
---

### Post by declan77 on 2007-05-20
How can I get the laptop lid to register open/close events?

ACPI is running. When I run lshal --monitor and open/close the lid nothing gets registered. If I plug/unplug power or add a USB device then these get registered. The laptop lid is always registered as closed which I can see using the command:
cat /proc/acpi/button/lid/LID0/state

Any tips? Running Kubuntu 7.04 on a samsung x50.

---

### Post by NilsE on 2007-05-20
Check the settings in the config editor and see what the lid is set to do. 

System Tools/Configuration Editor/apps/gnome-power-management

---

