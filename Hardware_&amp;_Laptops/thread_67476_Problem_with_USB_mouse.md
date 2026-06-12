---
title: "Problem with USB mouse"
date: 2005-09-20
forum: Hardware &amp; Laptops
---

### Post by Frankk on 2005-09-20
Hello everybody, i just installed Ubuntu 5.04 for the first time (i'm a long time slackware user) and i'm really positively impressed.

Btw, i'm having this problem with my usb mouse:

I have a Benq Joybook 7000 notebook that should have USB2.0 connectors.
At boot only the touchpad works and lsmod shows me that uhci_hcd and echi_hcd are loaded. If i do rmmod uhci_hcd and then again modprobe uhci_hcd that the usb mouse works perfectly.

I tryed to blacklist ehci_hcd in /etc/hotplug/blacklist but the problem was still there.

What can I do to have my mouse working at boot?

Thanks.
Frankk

---

