---
title: "screen res not available since upgrade"
date: 2016-12-10
forum: Hardware
---

### Post by RumorsOfWar on 2016-12-10
I'm using a Nvidia 7300, after upgrading to 16.10 my monitors res is no longer available. Also most controls in the Nvida server-settings app are missing.
nvida driver 304 running (confirmed correct for that card)
xorg.conf shows correct res (1440x900) 
xfce4 display manager does not show 1440x900. 
dpkg -l grep linux shows:
 dpkg-query: no packages found matching linux
 ric@ric-NY545AAR-ABA-p6210y:~$ xrandr -s 1440x900
 Size 1440x900 not found in available modes

I've looked through similar threads with no luck.
Help!?

---

### Post by wildmanne39 on 2016-12-10
Thread closed. Please do not post duplicates, it dilutes community effort.

---

