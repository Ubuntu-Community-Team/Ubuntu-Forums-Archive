---
title: "A105 | lcd Brightness | Touchpad issues"
date: 2007-02-08
forum: Hardware &amp; Laptops
---

### Post by jvictor on 2007-02-08
Looks like my eyes may burn off as there is no way of controlling the LCD brightness..its really  causing havoc because I need to work long hours and **_need_** to control the brightness .. 

Has anyone had luck with this ? also the touch pad doesn't allow to scroll if u place the finger at the right hand corner and drag.. ironically both work on windows..

---

### Post by jvictor on 2007-03-27
It appears that there is a way now, I upgraded to the latest bios from toshiba v 5.50

once that is done the function keys start to respond.

to reduce the brightness, use the following commands in a terminal

sudo -s (will log you in as super user)

cat /proc/acpi/video/GFX0/LCD/brightness (will give u the supported brightness levels)
levels:  75 35 10 25 35 50 60 75 90 100

echo 10 > /proc/acpi/video/GFX0/LCD/brightness (sets the current brightness level)

---

