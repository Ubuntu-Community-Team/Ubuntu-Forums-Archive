---
title: "Synaptics not being recognized"
date: 2013-01-16
forum: Hardware
---

### Post by griffjon on 2013-01-16
I'm wrestling with a synaptics touchpad that I can't get Ubuntu (12.10/64bit) to "see."

I'm on a Dell Latitude E6430.

tpconfig recognizes it as "Found Synaptics Touchpad. Firmware: 8.96 (multiple-byte mode)"

synclient complains there is no driver loaded

System->Mouse and Touchpad doesn't have a tab for touchpad (because there's no driver).

I've tweaked and pulled in /usr/share/X11/*-synaptics into /etc/X11/xorg.conf and rebooted, to no avail.

I've tried and failed to install synaptics-dkps 
Where should I be looking to get the system to recognize my touchpad as such (it's listed and behaves as a PS/2 Mouse)?

Help?  I've searched across the web, but keep ending up at the same threads that I've tried out.

---

