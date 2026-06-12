---
title: "problems getting intel gma x3100 driver work"
date: 2008-04-04
forum: Hardware &amp; Laptops
---

### Post by tanel?j on 2008-04-04
I did as instructed here:
[http://ubuntuforums.org/showthread.php?t=506744&highlight=X3100](http://ubuntuforums.org/showthread.php?t=506744&highlight=X3100)

it didn't work like it supposed to because if I restarted the system and chose my graphic card (intel 965 chipset family) and pressed OK, it still put default .. some vesa i810 thing (sorry don't remember exactly).

Have a Lenovo X61
# CPU: Intel Core 2 Duo 2.0GHz T7300
# Chipset: Intel 965 Express
# Memory: 2048MB DDR2 PC5300 (2x 1024MB)
# GPU:  Intel X3100 Integrated

Thanks, if anyone could help

---

### Post by acron1 on 2008-04-04
Are you running Gutsy? 
The GMA X3100 should be supported by default.
Did you try to boot with the live CD and see if that  picks up the correct driver?
If it does you can copy the xorg.conf from the live CD boot session and use it with your install.

---

