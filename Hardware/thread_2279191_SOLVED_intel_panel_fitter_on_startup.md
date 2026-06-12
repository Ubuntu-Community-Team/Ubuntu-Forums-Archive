---
title: "SOLVED: intel_panel_fitter on startup?"
date: 2015-05-21
forum: Hardware
---

### Post by User-007 on 2015-05-21
Hi all,

I have to use intel_panel_fitter for tackling my hardware overscanning problems. But, since it has to be run as sudo, how it can be run on system startup? No success with /etc/rc.local .

Suggestions?
User JB

---

### Post by User-007 on 2015-05-22
Solved by myself. Created a script to /usr/bin for running intel_panel_fitter, autostart for it (as sudo) and modified /etc/sudoers.

---

