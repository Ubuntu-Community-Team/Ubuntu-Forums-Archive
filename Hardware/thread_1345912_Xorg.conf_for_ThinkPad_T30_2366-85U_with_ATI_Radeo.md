---
title: "Xorg.conf for ThinkPad T30 2366-85U with ATI Radeon 7500 Mobility GPU"
date: 2009-12-04
forum: Hardware
---

### Post by pi3832 on 2009-12-04
@

---

### Post by dneiman on 2009-12-09
This morning I upgraded my T-30 from 9.04 to 9.10 and the graphics/display was unusable.
I hit ctl-alt-F1 to login via a shell.
Then, as root, did the two steps above (saving the original xorg.conf for good measure), rebooted, and the display was fine.

Thanks!

Actually, after logging in from the shell I first shut down GDM:
sudo /etc/init.d/gdm stop

Then I did the above two fixes as root.
Exited root & restarted the GDM:
sudo /etc/init.d/gdm start

---

