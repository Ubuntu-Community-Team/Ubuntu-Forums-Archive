---
title: "Xubuntu 11.04 - disable touchpad tapping?"
date: 2011-05-09
forum: Hardware
---

### Post by tpprynn on 2011-05-09
I've entered

syndaemon -i 1 -d

in Settings > Session and Startup > Application Autostart as in previous versions of Xfce, but the tapping function is still working. I've always found that irritating in Windows and Linux alike, and it seems to mistrigger.

Has anyone found out what needs doing with the new Xfce for the same effect?

This is a Toshiba Equium L40 laptop, with a Synaptics touchpad. The simpler tick out the box method with Gnome has always worked. The new Xubuntu 11.04 is pretty good so I'd like to get past this niggle.

Thanks.

---

### Post by Anon7-2521 on 2011-05-09
Open up a terminal and type:

```

synclient MaxTapTime=0

```

if it works, add it to your startup.

---

### Post by tpprynn on 2011-05-09
It turns out that the line

Option "TouchpadOff" "2"

needed to be added to /usr/share/X11/xorg.conf.d/50-synaptics.conf


Thanks for the other suggestion anyway; I'm not certain but I think Xfce 4.8 needs something other than that as I'd tried something similar earlier.

---

### Post by kr0n1x on 2011-10-22
What should I do if I would want to disable tapping only (keeping scrolling on)?

---

### Post by tpprynn on 2011-10-22
If I remember right the line I mentioned there left the scrolling working and disabled the tapping. I just did it with the new Xubuntu and rebooted - bit easier than trying the same with LXDE as well...

---

### Post by kr0n1x on 2011-10-23
To me it disabled both scrolling and tapping.
To disable only the latter, I did this trick:

```
Option "MaxTapTime" "0"
Option "MaxTapMove" "0"

```

And I deleted the TouchpadOff option.

---

