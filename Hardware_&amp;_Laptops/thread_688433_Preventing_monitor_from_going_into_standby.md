---
title: "Preventing monitor from going into standby"
date: 2008-02-05
forum: Hardware &amp; Laptops
---

### Post by Whitman on 2008-02-05
I'm using Kubuntu 7.10 and I'm trying to get a monitor to stay on and not go into standby mode.  I've unticked the power management setting in the display options and have also commented out Option "dpms" in xorg.conf (and restarted x) yet it still goes into standby mode.  No screensaver is set either.

Any ideas why this is happening and how I can stop it?

Thanks.

[Edit] Just read that the default is to turn DPMS on if not set in xorg.conf.  I've now set it to Option "dpms" "false"
Let's see if that works.

---

