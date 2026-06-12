---
title: "After a recent Hardy update, on start up it says it could not detect my video card."
date: 2008-07-12
forum: General Help
---

### Post by DayOldPorridge on 2008-07-12
I've tried setting it to the right driver various times, but everytime I reboot, it seems to ignore the changes.  And no matter what resolution I choose, whenever GNOME starts up, everything's way too big.

Even using the older kernel, the resolution is still way off.

Any way to fix this?

---

### Post by DayOldPorridge on 2008-07-13
Bump?

---

### Post by dcstar on 2008-07-13
> **DayOldPorridge said:**
> I've tried setting it to the right driver various times, but everytime I reboot, it seems to ignore the changes.  And no matter what resolution I choose, whenever GNOME starts up, everything's way too big.
........

In 8.04 I believe that the video is auto-detected if there is a problem, so the incorrect xorg.conf file is ignored and a default one is created.

If it is doing this then you don't have the right hardware driver installed.

If you install video drivers using non-standard methods (like Envy) then these are not updated when a new Ubuntu kernel is released, you have to go through whatever process you used manually.

---

### Post by ghost_ryder35 on 2008-07-13
try uninstalling your video driver and reinstalling it
```

lspci

```
will tell you your video card

---

