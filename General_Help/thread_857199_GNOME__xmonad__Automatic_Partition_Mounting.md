---
title: "GNOME / xmonad / Automatic Partition Mounting"
date: 2008-07-12
forum: General Help
---

### Post by sjmorgan on 2008-07-12
Dear Ubuntu friends,

I'd like to start using xmonad but there is one thing that's holding me back. As I'm sure you're aware, when you start GNOME it automatically detects all the partitions on your system and automatically mounts them for you.

Is there any way to achieve this kind of behaviour without running GNOME?

Thanks.

---

### Post by graabein on 2010-01-06
A big healthy 1 1/2 year bump!

What should I start for my external drive to be mounted automatically? The same goes for any USB-devices I hotplug. DeviceKit? dbus?




**Edit:** Never mind. I use gnome-volume-manager in .xsessionrc:
```
#!/bin/sh
numlockx on
gnome-settings-deamon &
gnome-volume-manager &
```

Update: Not sure if this actually works. Looks like gnome-volume-manager (for disks) has been removed from Ubuntu 9.04...

---

