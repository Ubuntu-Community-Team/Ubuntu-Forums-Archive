---
title: "nVidia 6800, no GDM/Gnome"
date: 2008-01-20
forum: Hardware &amp; Laptops
---

### Post by winter_mute on 2008-01-20
I've recently switched out my Radeon 9800 in favor of a Geforce 6800.  I first used the Restricted Drivers manager to install the nVidia drivers, but they resulted in the monitor not recieving a signal once it passes the boot screen, ie, when it reaches GDM.  So I used Envy, which resulted in the same issue.  Now I'd heard that nVidia was just a breeze to set up, but this seems like an odd problem, and one I'd like solved sooner rather than later.  Any help here would be great.

There's no error messages in xorg.0.log, and nothing in dmesg about it at all.  I'm utterly befuddled.

---

### Post by winter_mute on 2008-01-21
Okay, I figured out the issue - it was switching over to the VGA port.  Is there any way I can get the card to stay on the DVI port?  I'd much prefer to use the DVI cable I already have.

---

