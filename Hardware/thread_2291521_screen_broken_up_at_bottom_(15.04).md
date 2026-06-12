---
title: "screen broken up at bottom (15.04)"
date: 2015-08-20
forum: Hardware
---

### Post by pickarooney on 2015-08-20
I updated from 14.04 to 14.10 and then to 15.04 today and since then, when I log in I have this horizontal line breaking up the bottom of my screen. It occurs on the desktop, web browser, krusader etc. but not when playing back videos.
I guess it's some sort of graphics driver issue; I've tried installing the latest version 340.76 but it hasn't fixed the issue.

[ATTACH=CONFIG]263967[/ATTACH]

Does this look familiar to anyone?

---

### Post by kerry_s on 2015-08-20
sometimes the theme can cause that, try a different theme.

---

### Post by pickarooney on 2015-08-20
Turns out it was being caused by a combination of an XFCE Window Manager tweak for drop shadows in docks and the configuration of cairo-dock 3.4. I hadn't changed either from the previous Xubuntu installation but there you go...

---

