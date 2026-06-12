---
title: "Twin GeForce 9500GT Cards (no nVidia Binary)"
date: 2008-12-31
forum: Hardware
---

### Post by BadServo on 2008-12-31
I've been running an Intrepid installation that was upgraded from Hardy.  The video card in this machine was a GeForce 8600GTS.  I was using the nVidia Binary driver that is included in the official repos  (177).

Yesterday I replaced the 8600GTS with 2 9500GTs with intent to use SLI under Windows for gaming.  I assumed that Ubuntu wouldn't hiccup, since the driver should also support these cards.  But upon reboot X wouldn't start.

I tried editing my xorg.conf to use the "nv" and "vesa" driver instead, but it didn't help.  Eventually, I just backed-up my home folder and reinstalled fresh.

Everything appeared to be working fine.  I attempted to install the Binary driver, and suffered the same problem.  I downloaded the latest nVidia Beta Driver (180.18) and attempted to install it.  This also failed to work.

At this point, I'm at a loss.  Can anyone offer any advise on getting 3D support for these cards?

---

### Post by BadServo on 2009-01-01
BUMP...

Any ideas, folks?

---

