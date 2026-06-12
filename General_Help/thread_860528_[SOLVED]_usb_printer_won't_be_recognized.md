---
title: "[SOLVED] usb printer won't be recognized"
date: 2008-07-15
forum: General Help
---

### Post by moore.bryan on 2008-07-15
i used to be able to print to my hp deskjet 5550, but can no longer do so. when i try to add the printer in CUPS, i get nothing. i downloaded the latest hplip driver and installed it, but when it gets to the part where it should recognize the usb connection, it tells me no printer is there. i've tested both the printer and the cable in xp and it works fine, so i know it's not a hardware issue. i think it may be hal related... any thoughts?
=====
EDIT 1:
so, i'm fairly certain this is related to a udev/hal/bus/usb issue. my printer WILL NOT be seen when it is plugged-in. please? oh, and, "lsusb" returns NOTHING.
=====
EDIT 2:
more digging and the problem seems to lie in the ehci-hcd module. with it loaded, no usb printer; however, if i manually load uhci-hcd, i have the usb printer seen and everything is easy-peasy. uh, wtf is that about?

---

