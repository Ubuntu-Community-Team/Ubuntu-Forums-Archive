---
title: "Touchpad settings disappear after upgrade or switching between desktops (GNOME)"
date: 2016-12-16
forum: Hardware
---

### Post by Antoon Stessels on 2016-12-16
In Ubuntu 16.10, Ubuntu GNOME 16.10 and Ubuntu MATE 16.10, **touchpad functionalities might literally disappear** from System Settings > Mouse and Touchpad.

This apparently happens after upgrading to Ubuntu MATE 16.10 (as is being discussed [here]("https://ubuntu-mate.community/t/touchpad-settings-seem-to-have-disappeared-following-update-to-16-10/9871")),

And also when switching back and forth between Unity and the GNOME desktop in Ubuntu 16.10.

The solution is given in the aforementioned forum, and reads like this:

[INDENT][FONT=Ubuntu]I suggest removing [/FONT]xserver-xorg-input-libinput[FONT=Ubuntu] package then. That is, if nothing depends on it. If you'll see that some other package(s) would be removed with it, then cancel the removal and post the output here.[/FONT][/INDENT]

Removing this package in Synaptic happens without dragging any dependencies with it;

after reboot, the functionalities, like **tap-to-click**, are back.

**Thanks to Vlad Orlov (monsta) for providing us with the answer.**

---

