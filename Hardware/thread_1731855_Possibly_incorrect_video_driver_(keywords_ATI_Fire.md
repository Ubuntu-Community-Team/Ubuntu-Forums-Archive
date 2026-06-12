---
title: "Possibly incorrect video driver (keywords: ATI FireGL, HD4250, X Updates)"
date: 2011-04-17
forum: Hardware
---

### Post by 3602 on 2011-04-17
Hello all,

Recently I played a bit with Ubuntu Tweaks and enabled the X Updates PPA. I got new *fglrx* and other stuff.
No, nothing is crashing. It's just that 1080p YouTube videos, when played fullscreen, are somewhat choppy. It's not the Internet speed as the video always caches faster than it plays (still happens if I let the pale red bar fill up before playing).
I went into Additional Drivers and I see that I'm using ATI FireGL driver. However, this computer has AMD Premium Vision, which according to grepping VGA, is:
```
lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]

```The computer box says HD4250. So clearly not a FireGL which is a line of actual cards with fans and all.
Everything else works fine, 3D games and all. It's just the slightly choppy YouTube videos.

Is this normal? Shall I leave it as-is?

Thank you very much.

---

### Post by Yellow Pasque on 2011-04-17
It's normal. Flash video isn't accelerated on ATI in Linux. Use Flash-aid extension to replace Flash with a real video player on YT. As for the naming, the Linux Catalyst driver has always been called fglrx, as it was originally aimed at the workstation market (a half-arsed attempt to compete with nvidia).

---

### Post by 3602 on 2011-04-17
OK *fglrx* actually *means* FireGL... Thanks.
Also thanks for the Flash-aid extension. I clicked Execute and the video (the only 1080p I watched to date) isn't chopping anymore on fullscreen. Thanks a bunch! :thumbsup:

EDIT: Oh and nVidia Optimus doesn't work *at all *on Linux. So that.

---

