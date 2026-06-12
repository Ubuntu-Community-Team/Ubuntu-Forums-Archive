---
title: "Problem with sound over HDMI using Lenovo Ultradock Pro"
date: 2016-07-07
forum: Hardware
---

### Post by Martin.Weinberg on 2016-07-07
Since upgrading from 14.04 to 16.04, the system no longer enables the HDMI audio on the Lenovo dock.  In pavucontrol, for example, it is listed as 'unplugged'.  Using a series of Ubuntu Live CDs beginning at 14.04.1, 14.04.2 (which is kernel 3.16) confirmed that the problem arose in the next release.

HDMI audio works fine when plugged into the laptop itself, so that seems to point to the Displayport MST hub.

So the problem seems kernel related not software 16.04 software specific.  I filed a bug, [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1582414](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1582414), but this has very low priority.

Anyway, does anybody here have a clue?  Someway to override the 'unplugged' detection . . . 

My work around is to plug a 3.5mm audio cable from the headphone jack to the monitor.  Works fine. But I'd love to get it working properly.  Otherwise, the Lenovo T440s and Ultradock work well with 16.04.

---

