---
title: "Battery does not exist when using 2.6.20-16-generic"
date: 2007-06-29
forum: Hardware &amp; Laptops
---

### Post by spinstartshere on 2007-06-29
When I boot my laptop, in GRUB I see 2.6.20-15-generic and 2.6.20-16-generic.  When I use the former, Ubuntu informs me of the status of my battery.  When I use the latter, it doesn't, and where I expect to see a battery icon in the notification area, I see a plug.  When I hover the cursor over the icon, it says "Computer is running on AC power".  How can I fix this?

---

### Post by NilsE on 2007-06-29
> **SVT said:**
> When I boot my laptop, in GRUB I see 2.6.20-15-generic and 2.6.20-16-generic.  When I use the former, Ubuntu informs me of the status of my battery.  When I use the latter, it doesn't, and where I expect to see a battery icon in the notification area, I see a plug.  When I hover the cursor over the icon, it says "Computer is running on AC power".  How can I fix this?

Are you saying that you get the pop up that it is running on AC power even when it is not plugged in to AC?

The reason I ask is that the icon and pop up change from on AC to charging or draining.  In other words if it is plugged in and charged it will be a plug with the pop up that it is on AC.  If you unplug it it should show the time left on battery etc.

If none of that is true we will need to debug it since it should be the same in both versions of the kernel.

---

### Post by spinstartshere on 2007-06-29
Yep, that's right.

---

### Post by NilsE on 2007-06-30
Check and see if ACPI, gnome-power-manager, and gnome-applets are installed in synaptic.  

Most likely they are so you may just want to reinstall them.

---

### Post by walkerk on 2007-06-30
ensure gnome-power-manager is in System > Preferences > Sessions

---

### Post by NilsE on 2007-06-30
There seems to be a lot of this going around.  Check out this thread for a patch.

[http://ubuntuforums.org/showthread.php?t=457417](http://ubuntuforums.org/showthread.php?t=457417)

---

