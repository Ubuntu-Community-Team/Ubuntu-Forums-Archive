---
title: "Three monitors, two mirroring?"
date: 2015-05-17
forum: Hardware
---

### Post by SimonHGR on 2015-05-17
Hi all, I want to set up two external monitors on a laptop (three monitors total) with one of the external ones mirroring the internal display. Is this possible? It seems that when I add a third monitor, the "mirror" option goes away, and it's not clear what I'd do to select which pair of monitors are cloning, and which remains independent.

Should this work? What should I do? TIA!

---

### Post by SimonHGR on 2015-12-28
I finally solved this. Using xrandr

[FONT=Courier New]xrandr --output HDMI1 --same-as "eDP1"
xrandr --output VGA1 --right-of "eDP1"[/FONT]

eDP1 is the built in, and is now mirrored by HDMI1, while the VGA display provides extra workspace to the right of them.

---

