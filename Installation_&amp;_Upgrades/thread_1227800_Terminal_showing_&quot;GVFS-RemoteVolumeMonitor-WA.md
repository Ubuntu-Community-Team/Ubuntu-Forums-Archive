---
title: "Terminal showing: &quot;GVFS-RemoteVolumeMonitor-WARNING&quot;"
date: 2009-07-31
forum: Installation &amp; Upgrades
---

### Post by vickoxy on 2009-07-31
So, after i type gedit in terminal i have this error. I mean, i done fresh installation of ubuntu-only added cairo-dock. Does anyone knows what is this?

> (gedit:3753): GVFS-RemoteVolumeMonitor-WARNING **: invoking IsSupported() failed for remote volume monitor with dbus name org.gtk.Private.GPhoto2VolumeMonitor: org.freedesktop.DBus.Error.Spawn.ExecFailed: Failed to execute program /usr/lib/gvfs/gvfs-gphoto2-volume-monitor: Success

---

### Post by vickoxy on 2009-07-31
If i type > sudo-gedit there is no error message...

---

### Post by vickoxy on 2009-07-31
Anyone knows how danger this could be, or i can ignore it? I didn´t notice that something is really wrong with the system.

---

### Post by vickoxy on 2009-07-31
Maybe it has something with SDHC Card to do. I did little tweaking to make it work:
[http://ubuntuforums.org/showthread.php?t=1224292](http://ubuntuforums.org/showthread.php?t=1224292)

---

### Post by vickoxy on 2009-07-31
No one has any idea-or should it be fatal error/should i do reinstall/?

---

### Post by vickoxy on 2009-07-31
So i fix it on unusual way-uninstalled gvfs-removed also ubuntu-desktop, nautilus, and lot of other things-then i reinstall them back. 

BUT, i noticed-it installed again gnome-games, gnome-games-data and gnome-cards-data. This packages i deleted after installation because i did not need them. But, obviously, they lack of "games" data:confused: caused this errors to show up.

So, what is with this games (or gnome-cards-data)?

---

