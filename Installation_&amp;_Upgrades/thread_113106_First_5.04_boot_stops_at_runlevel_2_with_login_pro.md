---
title: "First 5.04 boot stops at runlevel 2 with login prompt."
date: 2006-01-05
forum: Installation &amp; Upgrades
---

### Post by reed on 2006-01-05
I loaded 5.04 from a Linux Magazine DVD.  Near the end of installation, it auto-connected to the internet and loaded security updates for about 20 hours.  (slow modem)  The phone connection went down several times, but it recovered nicely.

Problem is, when I boot the system after the install, it stops with a login prompt at runlevel 2.  No GUI.  I haven't gotten it to start X at runlevel 5, etc.

Any ideas?

One thought: I lost the phone link near the end of the install.  The last updates timed out (I think) and may not have gotten loaded.  If so, is there a way to get that gracefully finished?

I am familiar with SuSE Linux but totally new to Ubuntu.

Thanks ... Reed

---

### Post by 23meg on 2006-01-05
Type "startx" and report the errors you get, if any. Also post a copy of your /var/log/Xorg.0.log file if possible.

Also, what's your video hardware?

---

