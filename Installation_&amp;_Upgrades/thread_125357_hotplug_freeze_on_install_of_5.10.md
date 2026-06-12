---
title: "hotplug freeze on install of 5.10"
date: 2006-02-03
forum: Installation &amp; Upgrades
---

### Post by expat on 2006-02-03
Having a problem with a Fujitsu Amilo M laptop on install of 5.10. After reboot I get the GUI interface displaying the hotplug is starting and the system hangs. I've tried a variety of
```
acpi=off
noacpi
nolapic
nosmp
```
...and mixtures of the above without success. Everytime the system hangs at the hotplug section. There are two messages I'm getting before system halt, one regarding the sound card (intel-hda) and some kernel module hw_random.

Suggestions for possible resolution most welcome!

---

### Post by UK31337 on 2006-02-04
Hi,

Take it you've got the M3438G?  I've got that too, I couldn't get the Live CD to start.

It seems to be some kind of problem with the USB kit Fujitsu put in our laptops.  For some reason, 5.10 doesn't like it, and there seems to be no fix.

Hope they're working on it!  I'm going to try installing the proper version, see what I can figure out.

---

