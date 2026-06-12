---
title: "Dual monitor problems"
date: 2014-06-21
forum: Hardware
---

### Post by falaca on 2014-06-21
I have a dual monitor setup and I'm having some problems with getting Ubuntu to treat my right-hand side monitor as the primary display. My setup is as follows:

-Main display: 27" @ 2560x1440 (on the right)
-Secondary display: 24" @ 1200x1920 (portrait mode, on the left)
-Video card: AMD Radeon R7 260X, using the latest Catalyst
-Ubuntu 14.04

My secondary display is on the left-hand side, and this seems to cause a number of issues, e.g. desktop icons and WINE system tray icons always appear on the left monitor. SDL games also launch by default on the left monitor but I fixed that by setting SDL_VIDEO_FULLSCREEN_DISPLAY=0 in /etc/environment.

The reason for this appears to be that Xorg always sets the bottom left corner of the left-most display to position 0x0. I tried setting the bottom-left corner of my right display to 0x0, and using a negative position for the left display, but that didn't work at all. It seems like Xorg pushes the job of properly handling the displays to the desktop environment. Is there a way that this behaviour can be fixed, or do I need to submit a bug report (and if so, for which package?).

Thanks!

---

### Post by mbuller10 on 2015-03-06
**Bump** having this issue as well, someone please help

---

### Post by Mark Phelps on 2015-03-06
I have a dual monitor setup and the way I addressed this was in the Display settings, changing the positions of the two monitors.  When the Displays window first comes up, the monitor positions were reversed, with my right-most monitor showing on the left in the panel.  BY dragging the left-most monitor symbol to the right and applying the changes, I switched the monitor positions to match what they are physically.  Have not had any problems with this since.

---

