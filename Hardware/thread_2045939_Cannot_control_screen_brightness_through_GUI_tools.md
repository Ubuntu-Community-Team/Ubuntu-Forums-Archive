---
title: "Cannot control screen brightness through GUI tools"
date: 2012-08-22
forum: Hardware
---

### Post by tk83 on 2012-08-22
I have a Samsung Series 5 NP530U3C laptop with an Intel HD 4000 graphics card. I've found that I can't control the screen brightness with either the GUI tools (e.g. KDE's Power Management or the equivalent in Unity) or the function keys on the keyboard. 

However I can control the brightness by writing directly to the files in /sys/class/backlight/acpi_video0. For example ```
echo 50 > /sys/class/backlight/acpi_video0/brightness
``` sets the screen to approx 50% brightness.

Is there anything I can tweak to get the KDE and Unity power management software to be able to control the brightness?

---

### Post by matt1x on 2012-10-17
Hi,

You should try out the Linux on my Samsung -repo. It has package called samsung-tools, which fixed the same problem in Gnome.

Here's how to get it: [http://www.voria.org/forum/viewtopic.php?f=3&t=1091](http://www.voria.org/forum/viewtopic.php?f=3&t=1091)

-Matti

---

### Post by tk83 on 2012-10-17
Thanks but the one of the recent kernel updates that came through the normal update program fixed it.

---

