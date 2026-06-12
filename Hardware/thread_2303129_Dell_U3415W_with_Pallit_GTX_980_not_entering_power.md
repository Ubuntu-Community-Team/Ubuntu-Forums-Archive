---
title: "Dell U3415W with Pallit GTX 980 not entering power saver mode"
date: 2015-11-16
forum: Hardware
---

### Post by draki on 2015-11-16
Hi - I have a new Dell U3415W connected to a Pallit GTX 980 via the Dell provided displayport cable, using DP 1.2

When the screen is idle it blanks (set via xscreensaver) but the backlight is still on and remains on indefinitely

```

xset -q
DPMS (Energy Star):
  Standby: 300    Suspend: 420    Off: 600
  DPMS is Enabled
  Monitor is On
```

(I also get no audio over DP, but wouldn't use it anyway)

it's actually entered power saver mode on a few (once per day maybe) occasions so I know it does work (it also works on Win 10).. I assume there's some process interfering with this, but I don't know enough about this area of Ubuntu to pin down the culprit despite being fairly ruthless with killing processes. I've played around with some settings on the monitor (DP 1.2, etc.) and also NV-Settings but to no avail

Ubuntu 15.10 4.2.0-18-generic
NV drivers 358.09 (tried with the proprietary drivers from the repos before upgrading to these)

Any ideas? Let me know if there's any useful information I can gather & post

thanks

---

### Post by draki on 2015-11-17
Hi - seems to have been an NVIDIA regression - fixed in Version: 352.63 (released 16/11/2015)
"Fixed a regression that prevented DPMS from working correctly on some DisplayPort displays."

all working fine now (so far!)

---

