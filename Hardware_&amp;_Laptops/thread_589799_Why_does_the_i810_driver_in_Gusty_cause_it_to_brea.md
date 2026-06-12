---
title: "Why does the i810 driver in Gusty cause it to break?"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by spotdog14 on 2007-10-24
I have been having issues with gusty. The first was i upgraded from Edgy and was using the i810 for my integrated intel video card, but the upgrade broke it, ended up doing the intel driver instead, and everything worked. Then i ended up doing a fresh install of Gusty and was trying to get my external monitor to work, so i switched to the i810 driver because that was the only one that allowed me to use the new external monitor screen stuff (under the "screens and graphics" option) and it worked until i rebooted and ended up with the same black screen at startup as i had before.

So i went into recovery mode and fixed my xorg.conf file after some tinkering. Anywho WTF is wrong with the i810 driver in Gusty?

---

### Post by Thelasko on 2007-10-24
I believe it's just grandfathered in because the developers of the Intel driver are worried some people might find it buggy.  They recommend using the Intel driver.

---

### Post by dietrying on 2007-10-24
the i810 driver works very good for me......just in the opposite to the intel driver wich seems indeed very buggy (trying to restart the xserver freezes my system, vga-out doesn't work as expected). In your case i would try to configure x (and screen switching) without the buggy graphic tool.

---

