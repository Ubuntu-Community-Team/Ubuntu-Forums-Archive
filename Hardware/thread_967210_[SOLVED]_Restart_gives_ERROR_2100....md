---
title: "[SOLVED] Restart gives ERROR 2100:..."
date: 2008-11-01
forum: Hardware
---

### Post by gregkarr on 2008-11-01
Here's the full error message I get when I restart from Ubuntu:
-----------------
ERROR
2100: HDD0 (Hard disk drive) initialization error (4)

Press <ESC> to continue
-----------------
I then press <ESC>, and the screen just blank. However, if I turn the machine off and on again, I can boot back into Ubuntu fine.

Anyone know what could be causing this, or at least where I should start looking in order to diagnose it? (I know there is a log of bootup messages that is stored, so I guess there is a similar log of shutdown messages?)

---

### Post by gregkarr on 2008-11-09
I'm not having this problem anymore after following the tips in this post:
[http://ubuntuforums.org/showthread.php?t=603054](http://ubuntuforums.org/showthread.php?t=603054)

I went with acpi=force and a restart worked fine. Haven't tried the acpi=off option. 

I still get plenty of error messages from Network Manager whenever I shutdown or restart though.

---

