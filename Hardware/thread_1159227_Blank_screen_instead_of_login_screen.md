---
title: "Blank screen instead of login screen"
date: 2009-05-14
forum: Hardware
---

### Post by Loopk1n on 2009-05-14
Some time ago I installed Xubuntu 8.10 to my better half's not so new laptop. It's a Fujitsu-Siemens Amilo L 6825. Everything else works like a charm, except sometimes when starting up I get blank/black screen instead of login screen and desktop. Sometimes it can be revived with Ctrl-Alt-BackSpace or by swithing to terminal and back with Ctrl-Alt-F1/Ctrl-Alt-F7, but not nearly always.  A cold boot works most of the time, but rebooting never gives picture after the loading screen. When logging out it also leaves black screen with no login screen.

I have tested the issue with some live cd:s, Ubuntu 8.10 and Xubuntu 8.04. Most of the time I can't get over the point when the desktop should load, 8.04 seems to work more times than others. Now I have upgraded to 9.04 and the issue seems to gone even worse.

I don't think this problem has anything to do with the fact that the derivate in question is Xubuntu, because I get the same issue with ubuntu live cd.
I think the problem might be with the video drivers or xorg or something, the integrated video device is:

```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03).
```Oh, and everything works when booting with external VGA monitor.

So anyone have any ideas?

*Edit: Same issue with plain Debian.*

---

