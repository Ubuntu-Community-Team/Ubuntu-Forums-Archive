---
title: "HP dv7 ATI HD4650 dual monitors"
date: 2009-10-04
forum: Hardware
---

### Post by blacksadness on 2009-10-04
Hi,
I'm trying to setup a second monitor on my dv7 (dv7-2040us), i have the ati closed-source drivers installed, i tried opening the Display app from System-Preferences, but it barely loads if my second monitor is connected (tried analog and hdmi) the system also gets slow/barely usable, if i go on and set the second screen, its resolution is not optimal and the desktop is shared on both screens (maximize will go to both screens), and still the system will be too slow to use.

I tried with ATI Catalyst Control Center, it recognizes a new monitor, asks for restart, at restart it shows a really huge resolution on the second monitor, and keeps trying to restart the gnome-panel for some reason, enabling Xinerama from the Catalyst control center, after restarting crashed X and the system froze.

Any ideas?

---

### Post by markbuntu on 2009-10-05
Thry running the install script again with the monitor attached. do not use xinearama, it is not necessary to get two monitors working on one gpu.

---

