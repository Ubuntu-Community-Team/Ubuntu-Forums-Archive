---
title: "[SOLVED] No CDROM in WinXP VirtualBox 2.1 on Intrepid"
date: 2008-12-29
forum: Installation &amp; Upgrades
---

### Post by ancient_ee on 2008-12-29
Installed VirtualBox (closed source) in 8.10. Installed WinXP SP3 in that box. Now I finally got the USB working (yea!) and even was able to install VBoxGuestAdditions by mounting the .iso file. But the external CDROM drive does not appear as an icon in "my computer". It is enabled as host and passthrough is also enabled. The correct manufacturer name appears where it should, so everything should be cool...

Why can I mount an ISO file, but cannot mount a physical CDROM?

---

### Post by robr5454 on 2008-12-31
I had the same problem, with the same setup.

Try turning off the passthrough.  When I have the passthrough enabled, no drive.
When I disable the passthrough, I get cdrom drive D: in my Windows guest.

---

### Post by ancient_ee on 2008-12-31
Thanks! Whoda thunk!

---

