---
title: "Installed ATI Catalyst app - Desktop not working"
date: 2010-06-17
forum: Hardware
---

### Post by Manny-Ubt on 2010-06-17
:confused:

Ub: 10.04 (NetBook Env)
Video Card: Radeon Mobility X1600 (HP Dev 30b4)

Issue:

Installed ATI Catalyst app, b/c problem w/ dual screens, and to enhance resolution. After install (reboot) my desktop lost all functionality, shortcut, mouse right click, etc. System boots w/o any obvious problems. However, keyboard shortcut are working, etc.

---

### Post by gradinaruvasile on 2010-06-17
Have you seen the documentation for the proprietary Ati driver?

Ati dropped support for the cards up to the 2000 series on newer drivers - those older cards are supported only by the older versions of the proprietary Ati driver - and those older versions dont work on newer Linux versions.

So you have 2 choices:

1. Use the default opensource driver that comes with Ubuntu
2. Use an older Ubuntu version - up to Ubuntu 8.10 and install the proprietary driver.

---

### Post by Mark Phelps on 2010-06-17
Follow the directions in the link below for removing the fglrx drivers:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

After rebooting, Ubuntu should see your card and automatically install the open source drivers.  Those are the only drivers that will work with your card and current versions of Ubuntu.

---

