---
title: "Screen goes dim after waking from suspend"
date: 2011-09-10
forum: Hardware
---

### Post by palz2015 on 2011-09-10
I put the 10.04 LTS on my Toshiba Tecra M2 today. It works better than 11.04 (even though it supports unity, it doesn't work for some reason), but when I wake from sleep (closing the lid), the screen brightness is very low. This happened before and I used "fnfx" to reset the brightness (kilall fnfxd, then fnfxd) but that is very roundabout and is not fixing the issue at all. How can I get it not to change?

side note: I do have function keys for brightness (not set up), however I'm looking for a way to keep it from changing rather than an easy way to change it.

---

### Post by Toz on 2011-09-16
Do you have a **/proc/acpi/toshiba/lcd** file? 

If so, does the following reset the brightness level:
```
echo 7 | sudo tee /proc/acpi/toshiba/lcd
```
(I think the valid list of values is 0 - 7)

If it does, we can create a script to do this automatically on resume from suspend.

---

