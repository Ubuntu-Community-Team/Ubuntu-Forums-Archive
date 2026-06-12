---
title: "Apple Powerbook Screen bad after upgrade"
date: 2005-04-08
forum: Hardware &amp; Laptops
---

### Post by ChrisK on 2005-04-08
Warty was working and then I upgraded to Hoart (dist-upgrade method, following the release notes).

It is a Apple 15" AL powerbook (not a new one, but one from last summer).

The reboot went well until xfree86/gdm launched, then the screen was screwy: The scan lines were flickering horizontally out of position (HSync - like - problem?).  This was also true after switching back to the boot console on F1, where I could at least run "reboot" and go back to OS X to post this and [Bug 8809].

Anyone have a clue where to look for what changed?

---

### Post by wolrahnaes on 2005-04-09
Well a big change is that Hoary doesn't use XFree86 anymore, it uses X.org, so any X issues are likely related to the fact that the X server is completely different.

---

