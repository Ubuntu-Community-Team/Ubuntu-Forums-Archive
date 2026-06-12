---
title: "R50e: Distortion when resuming from suspend"
date: 2008-05-01
forum: Hardware
---

### Post by Steve1961 on 2008-05-01
Apologies if this has been covered already and I've missed it.  I have a Thinkpad R50e that has been running Ubuntu since Dapper.  Normally I dist-upgrade but I decided to do a clean install of Hardy.  Anyway, everything seems to be working fine so far, with one exception.  When resuming after suspend to ram my screen isn't being drawn properly - the gnome panel and desktop is distorted.  Killing the gnome panel or restarting x seems to make no difference.  This is the graphics card the system has:

00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
	Subsystem: IBM ThinkPad R50e
	Flags: bus master, fast devsel, latency 0
	Memory at e8000000 (32-bit, prefetchable) [disabled] [size=128M]
	Memory at d0080000 (32-bit, non-prefetchable) [disabled] [size=512K]
	Capabilities: <access denied>


I would try changing from the intel driver to the old i810 but there aren't any entries for drivers in xorg.conf anymore.  Any suggestions?

---

