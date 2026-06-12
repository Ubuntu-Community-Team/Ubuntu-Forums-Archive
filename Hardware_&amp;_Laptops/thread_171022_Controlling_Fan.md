---
title: "Controlling Fan"
date: 2006-05-05
forum: Hardware &amp; Laptops
---

### Post by Technoviking on 2006-05-05
I want to make a script or icon to let me turn on/off my laptop fan. When I use the following command:
```
sudo echo force_on:1 > /proc/acpi/toshiba/fan
```
I get *bash: /proc/acpi/toshiba/fan: Permission denied*
It works if I su - or sudo -i, then
```
echo force_on:1 > /proc/acpi/toshiba/fan
```
but that does not script well.

Any ideas on how I can get this to work?

---

### Post by paritybit on 2006-05-05
I may be way off-base but I think what is happening is echo is executed as superuser but the redirect (">") isn't.
Easy way I would think is to make a script with just that line in it (" echo force_on:1 > /proc/acpi/toshiba/fan") then sudo <script>

EDIT
and of course you could make a bash script to toggle it.
My bash skills are severely lacking but it would be something like this:
#!/bin/bash
FANSTATE = `cat /proc/acpi/toshiba/fan`
if [ FANSTATE ne 'force_on:1' ] then
echo force_on:1 > /proc/acpi/toshiba/fan
else
echo force_on:0 > /proc/acpi/toshiba/fan
fi

(yes there are some serious problems with this but for the mostpart it is sorta right)

---

### Post by 23meg on 2006-05-10
Try getting ownership of the device with```
sudo chown *system_username* /proc/acpi/toshiba/fan 
```.

---

