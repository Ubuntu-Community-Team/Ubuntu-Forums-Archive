---
title: "Laptop is realy slow... untill rebooted."
date: 2007-12-30
forum: Hardware &amp; Laptops
---

### Post by Portable_Jim on 2007-12-30
My dad has an [Acer Travelmate 4234WLMI]("http://www.acercomputers.co.za/laptop-specifications.php?laptop=8135").
It has a [Core 2 Duo T5600]("http://processorfinder.intel.com/details.aspx?sSpec=SL9SG"), so it should not be too slow
My 933MHz desktop is faster than the Acer. Both have Ubuntu Gutsy and all updates intalled.

The laptop takes a few minutes to start up, and a few more to get ready once you have logged in. It would take at least 10-15 seconds to start up any program (including terminal). The CPU usage however stays down below 10%.

I have tried the idea of removing "quiet splash" and adding "vga=normal" but that has no effect.

The laptop is much faster the reboot.

Does anyone know what is wrong? Thanks in advance.

---

### Post by emptythevoid on 2008-01-07
Check your processes.  Is Trackerd eating up any CPU or "Nice"?

---

### Post by emptythevoid on 2008-01-07
I've had a machine that became crippled running 7.19 because trackerd was running as soon as boot was complete.  Uninstalling Tracker fixed it.

---

