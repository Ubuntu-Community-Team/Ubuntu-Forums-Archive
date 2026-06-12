---
title: "Laptop behaves as if always running on battery"
date: 2014-05-17
forum: Hardware
---

### Post by Ivan_Marti-Vidal on 2014-05-17
Dear Ubuntu people,

I've been using Ubuntu and Xubuntu for almost 5 years, on different laptops, and never faced the problem I'm reporting here. I've googled quite a bit for an answer with no success, and would be very thankful if you could enlighten me.

I bought and HP Pavilion a few weeks ago and installed Xubuntu 14.04 on it. I solved a few problems (especially regarding the wifi) and now everything works fine with one exception: the computer seems to react as if it was always running on battery. For example, it doesn' t matter what actions do I set in the power manager for the close-lid event when running on AC, it always does the action configured for the case of running on battery. For instance, it always suspends when I close the lid, even if I set it to blank screen when running on AC. 

In addition, I cannot decrease the screen brightness using the corresponding Fn buttons, and I don't see in the power manager any option to decrease screen brightness when running on battery.

Maybe, all these problems have a common cause. I tried to solve this by changing the acpi option in grub to either "linux" or "vendor" with no success. 

Thank you in advance for your kind help!

     Best Wishes,

             Ivan

---

### Post by Ivan_Marti-Vidal on 2014-05-17
Sorry if I've not been clear enough in the previous message: I've tried to set "acpi_osi" to "Linux" and/or "acpi_backlight" to either "Linux" or "vendor"  (all combinations) with no success.

---

