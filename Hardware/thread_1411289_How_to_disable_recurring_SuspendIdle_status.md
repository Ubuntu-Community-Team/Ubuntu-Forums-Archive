---
title: "How to disable recurring Suspend/Idle status?"
date: 2010-02-19
forum: Hardware
---

### Post by Amadameus on 2010-02-19
I am running a very basic rig (the specs are nothing special, 1TB HDD with an ASUS mobo and an AMD processor, both far from high-end) for use as a simple no-maintenance Transmission tower. It's running Ubuntu 9.10 and is fully upgraded.

This rig's sole purpose is to download and seed torrents. It will be used for nothing else.

However, there is a slight problem: despite my best efforts, the rig continues to enter "idle" and "standby" modes, logging out and killing all internet traffic.

I've turned all my Power Management and Screensaver options to "Never" and also used Transmission options to "prevent computer from idling while Transmission is active"

...and yet it idles. This is an infuriating bug, because it can only be reproduced every two hours. I change what I hope will be the correct option, and the next time I return to the rig I find that it's been off for a day and a half. RAGE ensues.

Anyway. I've changed all the settings that I could find in the GUI to no avail. I added these two lines to /etc/modprobe.d/blacklist.conf
```
# Blacklisted to prevent recurring system standby
blacklist apm
```

While this appears to have worked (no standby for almost 24 hours) I am starting to question the wisdom of this decision. Does anyone have advice or input? Similar problems?

---

### Post by pi/roman on 2010-02-20
Press alt/f2 and run "gconf-editor" then go to /apps/gnome-power-manager/actions/ and make sure nothing is marked "shutdown" then go to /apps/gnome-power-manager/disks/ and uncheck spindown disks then go to /apps/gnome-power-manager/general/ and uncheck "can_hibernate" and "can_suspend" and that should do it.

---

### Post by Amadameus on 2010-06-24
Working perfectly. Thanks!

---

