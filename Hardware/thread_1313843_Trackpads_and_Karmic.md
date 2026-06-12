---
title: "Trackpads and Karmic"
date: 2009-11-04
forum: Hardware
---

### Post by Citizen Bleys on 2009-11-04
I'm sure I'm not the only one who had a problem with mouse control on upgrade to Karmic, since the option (present in Jaunty) to disable the trackpad on laptops is completely absent from Karmic, and 100% of laptop users I know hate their trackpads, which were designed by Satan.

I found a solution--typically threads on this forum come up quite to the beginning of any google search, so I thought I'd post it.

To temporarily disable the trackpad, in a terminal window, type:

```

sudo modprobe -r psmouse

```

I did that and it did not affect the USB mouse that I actually use.  Of course, on reboot, the trackpad comes back.  Not much of a solution.

The permanent solution, of course, is to sudo nano -w /etc/init.d/rc.local and add the same line, sans sudo (as rc.local is run as root at bootup)

Anybody have a more elegant solution?

---

