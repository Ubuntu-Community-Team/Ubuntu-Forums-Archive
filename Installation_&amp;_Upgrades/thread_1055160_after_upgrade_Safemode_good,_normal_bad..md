---
title: "after upgrade Safemode good, normal bad."
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by demoric on 2009-01-30
I have recently upgraded from Hardy Heron to the 7.10 Intrepid Ibex.

I now have an issue with logging in.  If I login normally the GUI boots about halfway in. (I'm seeing my desktop, and icons, and hear the startup sound) and then I get returned to the login screen. If I login to failsafe GNOME everything works well.  So I assume some startup script now has an invalid command.

I would like to know where the log file is for errors (so I can troubleshoot errors like this in the future), and also how I might go about fixing it.

---

### Post by demoric on 2009-01-30
[UPDATE] (and bump)

I have tried using
sudo dpkg-reconfigure xserver-xorg
and have also tried removing 
~/.gnome2

I still can't log into ubuntu using the normal login settings.  The only way things work is by using GNOME safe mode.

Is there a way to copy over the config for gnome safe mode to my profile?

Sorry, I'm still new to Ubuntu.

---

