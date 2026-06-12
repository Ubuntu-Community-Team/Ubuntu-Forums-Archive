---
title: "lucid 10.04 Toshiba A110: battery pb acpi"
date: 2010-06-16
forum: Hardware
---

### Post by mauricebis on 2010-06-16
Hi,

I've installed lucid on my toshiba satellite A110. I've got the Phoenix bios. When I unplug the AC power to run on batteries, system hibernates.

I tried to play a bit with the power management options in gnome (sudo gconf-editor) without success.

I've searched the forum but didn't find anything very clear: The existence of an acpi tailored to toshiba? The existence of fxfn program that requires toshiba support module?...

Would there be a way of configuring the acpi for instance and prevent that the event of switching on batteries trigger an hibernate action?

Help much appreciated. Thanks.

---

### Post by mauricebis on 2010-06-21
I'll reply to myself just for others who would experiment this difficulty. While my attempt at tweaking the key values by the gnome editor was not successful ; by clicking on the battery icon itself and choosing preferences:

On main Power> When lid is closed: change to blank screen
On battery Power> When lid is closed: change to blank screen

For some reason, the event switch to battery is converted in lid closed!

Make sure you restart gnome after this (sudo /etc/init.d/gdm restart).

When the power switch to battery, you then get a blank screen, by pressing any key you then get the screen.

This has been written elsewhere but my first attempt at it was unsuccessful as I didn't restart gnome.

---

