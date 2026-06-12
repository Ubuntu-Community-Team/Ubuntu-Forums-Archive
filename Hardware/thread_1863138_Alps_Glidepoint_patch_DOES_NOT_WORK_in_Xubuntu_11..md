---
title: "Alps Glidepoint patch DOES NOT WORK in Xubuntu 11.10"
date: 2011-10-17
forum: Hardware
---

### Post by MarjaE on 2011-10-17
The computer insists on detecting the Alps Glidepoint as both a touchpad and a PS/2 Mouse and insists on treating brushes against the trouchpad as clicks.

I cannot see any options to disable certain devices, to disable them while typing, to turn off tap-to-click, etc.

P.S. Can someone please add the [Xubuntu] tag?

---

### Post by MarjaE on 2011-10-17
A couple reboots later, it detects the touchpad as a touchpad and a nonexistant sick. but not as a ps/2 mouse. But the mouse preference within Xubuntu don't allow me to disable tap-to-click or disable touchpads while typing. I installed Pointing Devices, but it doesn't show in the Settings Manager.

---

### Post by Copper Bezel on 2011-10-18
Damn. It looks like [_you're not the only one_]("http://ubuntuforums.org/showthread.php?t=1744967"), but all I'm finding when I search for ALPS configuration under Oneiric are your topics and thus-far-unanswered bug report. Irritating. 

I've had an ALPS trackpad before, and while it was terrible, the settings at least stuck in Gnome. Xubuntu's terrible management of these things is one of the reasons I don't suggest it (it's similarly unbearable with keyboard settings, display settings, etc.) but at least with a Synaptics touchpad, this can all be controlled by a shell script when the appropriate GUI tools are not available. The only bit I've found is that ALPS trackpads might be configurable [_from udev rules_]("http://www.bhagwad.com/blog/2010/technology/alps-synaptics-touchpad-configuration-in-lucid-lynx-ubuntu-10-04.html/"), but I'm hoping someone a little more used to all of this configuration hell will try it first (I would, but I don't have an ALPS trackpad.) It seems like, even still, the best we'd likely get is turning off tap-to-click entirely, since your mouse input in general is clearly being misread by the driver.

This whole business is making me appreciate, huggle, and cuddle my beautiful Elantech trackpad and say a little prayer of thanks to the driver Gods for smooth, functional multitouch and trackpad interruption while typing that I never had to configure anything to get.

---

