---
title: "Flickering problem if not using Nvidia driver in Ubuntu 12.04"
date: 2012-10-09
forum: Hardware
---

### Post by Fiable.biz on 2012-10-09
Hello.

It seems I have a partial incompatibility problem between my NVidia 9500GT graphic card and my Athena CTR monitor. For Ubuntu 10.10, the problem had been solved by configuring the resolution to 1024 × 768 and refresh rate to 60Hz through Gnome, rather than through Nvidia X server settings interface.

Recently I reinstalled Ubuntu 12.04, because of many problem (not display-related) since the upgrade. Thanks to the "nomodeset" boot option, and configuring the resolution through Gnome, I could get a display, but with a flickering pointer, whatever be the monitor. It's not possible any longer to configure the refresh rate through Gnome, but using ```
xrandr --output default --rate 60
``` didn't solve the problem.

If I install and use NVidia current driver, this solves the problem for the other monitors, but I get a black screen on my Athena monitor.

Any suggestion?

---

