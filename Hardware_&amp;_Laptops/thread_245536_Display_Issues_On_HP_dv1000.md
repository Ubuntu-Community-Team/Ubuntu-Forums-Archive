---
title: "Display Issues On HP dv1000"
date: 2006-08-28
forum: Hardware &amp; Laptops
---

### Post by jeffro on 2006-08-28
So I just put a fresh install of Dapper on my laptop (official model is dv1659us) and the system is mis-detecting the resolution at 1024x768. It should be 1280x768.  I tried to change the resolution through the System -> Preferences -> Screen Resolution pane, but no options except for 1024x768 exist.  I checked my /etc/X11/xorg.conf file and I checked for monitor settings and for every depth 1280x768 has been set.  I then checked /usr/share/xresprobe/xorg.conf and changed the monitor resolutions for all depths to 1280x768.  I restarted the computer and checked to make sure the file still hadn't changed.  After verifying that it hadn't I tried to change to the appropriate resolution and still couldn't.  I was wondering if anyone has any insight as to what else I could try in order to change my resolution.

Thanks.
Jeff

---

