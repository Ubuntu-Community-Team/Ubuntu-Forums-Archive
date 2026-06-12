---
title: "How to restore the default Radeon 9000 driver?"
date: 2009-01-30
forum: Hardware
---

### Post by void09 on 2009-01-30
I made a mistake. I installed the proprietary ATI driver without checking for compatibility. I need to undo that.

Apparently the ATI driver was NOT compatible with my Radeon 9000. X-window system gave errors and defaulted to some "low graphics" mode.

I have now removed all flgx-related packages. It doesn't really help. Compiz won't work. Hence: no good docks :(

Something is missing. What?

-----------
All ideas very much appreciated.

---

### Post by void09 on 2009-02-01
Solved:
I had to use Synaptic package manager to reinstall:
xserver-xorg-video-ati

---

