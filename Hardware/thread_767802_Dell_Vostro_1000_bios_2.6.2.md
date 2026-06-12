---
title: "Dell Vostro 1000 bios 2.6.2"
date: 2008-04-25
forum: Hardware
---

### Post by garcol on 2008-04-25
running from CD:
During intial setup: Language selection, loading kernel, ubuntu cylon-graphics work full-screen with NO problem. 

BUT both the Beta and LTS 8.04 version generate multiple dozens of horizontal lines from the bottom of screen to about 1/3 from top of screen, making reading barely possible.

Top 1/3 is crystal clear! Turning off (default) desktop makes no change.
I can connect to network, watch video play music and use mouse and kb, but with 2/3 of screen unusable, real operation is impossible.
System > preferences > screen resolution : has no data; cannot select up/down resolution; detect display does nothing. Apply makes entire screen go black ......with many dozens of white horizontal lines.....

Suggestions...?

---

### Post by terencelhl on 2008-07-04
> **garcol said:**
> running from CD:
During intial setup: Language selection, loading kernel, ubuntu cylon-graphics work full-screen with NO problem. 

BUT both the Beta and LTS 8.04 version generate multiple dozens of horizontal lines from the bottom of screen to about 1/3 from top of screen, making reading barely possible.

Top 1/3 is crystal clear! Turning off (default) desktop makes no change.
I can connect to network, watch video play music and use mouse and kb, but with 2/3 of screen unusable, real operation is impossible.
System > preferences > screen resolution : has no data; cannot select up/down resolution; detect display does nothing. Apply makes entire screen go black ......with many dozens of white horizontal lines.....

Suggestions...?

Try these:

1) Hold ALT and F4. This will bring you to terminal session
2) run "sudo aptitude" and perform upgrade (NOT sudo apt-get upgrade!!!)
3) Once done, restart.

Mine works after the upgrade.

Good luck.

---

