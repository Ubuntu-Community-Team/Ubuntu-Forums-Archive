---
title: "Default Radeon Power Profile"
date: 2011-07-17
forum: Hardware
---

### Post by Martin Marshalek on 2011-07-17
Kind of a stupid question but here it goes...

So I have a Compaq laptop with pretty poor battery life but I'm trying to squeeze what I can from it. Right now I can get about an hour to hour and a half out of it if I'm lucky. I use the default radeon driver but I know the catalyst driver has much better power management. Trouble is that I'm using Gnome Shell so catalyst pretty much stabs GS if you try to even look in the general direction of a catalyst package :) I noticed that you cant edit the power management of the radeon driver by running a few commands and using the profile/setting you like best. So I run this:

```
sudo echo auto > /sys/class/drm/card0/device/power_profile
```

And this works nicely, clocking my card down to about half the total speed when on battery. However, the change doesn't stick and I was wondering how I could have that stay next time I reboot?

---

### Post by Martin Marshalek on 2011-07-17
Sorry, should have searched more, turns out simply adding the command to /etc/rc.local fixed it.

---

