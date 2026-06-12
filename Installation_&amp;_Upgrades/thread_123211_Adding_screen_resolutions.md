---
title: "Adding screen resolutions?"
date: 2006-01-29
forum: Installation &amp; Upgrades
---

### Post by shultzjr on 2006-01-29
Just finished a standard Ubuntu 5.10 on an older Dell Dimension XPS T500 with 768M of ram and an ATI Rage Pro Turbo AGP video card and a Dell D1728 17 inch monitor.  The screen resolutions that are available include 640x480 and 800x600.  There is no 1024x768 which I know the monitor/card will do.  How do I add the xga resolution to the list?

thanks,
charles.....

---

### Post by christhemonkey on 2006-01-29
if you really want to..
edit the xorg.conf file in /etc/X11/xorg.conf
sudo gedit xorg.conf
look for the section about resolutions and add the one that you require.
Quit and then type into a terminal:

sudo /etc/init.d/gdm restart

Let me know!

---

### Post by shultzjr on 2006-01-29
After the restart, it kicked me into command mode where I had to re-logon.  When I went to the place to change screen resolutions, it had the same list - no 1024x768.

anything else?

---

