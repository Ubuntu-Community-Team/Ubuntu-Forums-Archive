---
title: "No keyboard or mouse after Upgrade to 8.10"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by hobo on 2009-09-12
After doing an inplace upgrade from 8.04 to 8.10 I have no keyboard or mouse at the login screen. I have found that reverting the xorg.conf to an older version fixes my problem until the next boot. Then the system reverts to a 33 line generic xorg.conf file. Can I stop this?
Also in reading other peoples problems I have found that Dbus is not running. If I start dbus then hal, from the command line, it will bootup correctly and allow me to login and the mouse and keyboard work. Although the session seems to be a default one and not my normal screen.

btw...this is on my Gnome system

---

