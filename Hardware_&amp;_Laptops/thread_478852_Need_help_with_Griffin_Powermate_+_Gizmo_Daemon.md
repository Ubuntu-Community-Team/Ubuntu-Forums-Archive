---
title: "Need help with Griffin Powermate + Gizmo Daemon"
date: 2007-06-19
forum: Hardware &amp; Laptops
---

### Post by wangdang on 2007-06-19
I'm trying to get it to work with KDEnlive, but it seems i cannot get it to perform as a mousewheel.
Using the following code (which i nicked from the the 211.powermate-mplayer.py)
# scroll slowly (create a mouse wheel event)
					Gizmod.Mice[0].createEventRaw(GizmoEventType.EV_REL, GizmoMouseAxis.WHEEL, Event.Value)

it just doesnt do anything, the only thing the wheel does is change gnome sound volume, which isn't what i'm after. (But by doing that, it proves it's getting some sorta signal at least)

---

