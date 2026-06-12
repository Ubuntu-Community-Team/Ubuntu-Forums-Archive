---
title: "No touch on Wacom Pen &amp; Touch in Oneiric"
date: 2011-11-12
forum: Hardware
---

### Post by marek_online on 2011-11-12
The one and only hitch with upgrade to Oneiric.

I've a Bamboo Pen & Touch (CTH-460-DE), and the touchpad seems to be doing nothing at all.

The pen works fine, and the buttons on the pad work, but touch does nothing at all. I had it working with the evdev driver before the upgrade, but the behaviour seems to have changed - it still works but isn't really satisfactory. Have tried installing the latest driver as per instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=1515562"), but no joy. 

Touch is listed in the output of xinput and xsetwacom --list, so I've just no idea where to go from here.

Any pointers much appreciated.

UPDATE:

It's a KDE problem. I've auto-login set, but if I logout I get a perfectly working touchpad at the login screen. Hadn't picked that up before. Gives me a lead at least...

---

### Post by marek_online on 2011-11-12
```
sudo apt-get purge kde-config-tablet
```

Did the trick nicely.

---

