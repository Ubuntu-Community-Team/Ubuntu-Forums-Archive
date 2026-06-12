---
title: "Lenovo X1 Yoga OLED brightness controls do not function"
date: 2016-09-18
forum: Hardware
---

### Post by dansanders on 2016-09-18
This laptop is somewhat unique in that it doesn't technically have a backlight (because OLED). The brightness controls in Windows were broken recently by an Intel graphics driver update, so it seems both that the graphics driver is responsible *and* that the hardware is poorly tested.

What I have tried:
[LIST]
[*]/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-eDP-1/intel_backlight/brightness
[LIST]
[*]Has range 0 to 852, changes have no effect.
[/LIST]

[*]Standard GNOME controls, xrandr --set Brightness
[LIST]
[*]Same as /sys interface.
[/LIST]

[*]Blacklist acer_wmi
[LIST]
[*]I don't know why this loads, but it doesn't appear to affect brightness.
[/LIST]

[*]acpi_backlight=vendor
[LIST]
[*]Adds thinkpad_acpi brightness controls, also non-functional.
[/LIST]

[*]Legacy boot mode
[LIST]
[*]Doesn't change anything related to brightness.
[/LIST]
[/LIST]

What does work:
[LIST]
[*]Currently I am using xrandr --brightness. This is actually workable for an OLED screen, but it gets reset to max brightness randomly (the setting survives suspend/resume, but somehow clicking in gedit occasionally resets it, for example).
[/LIST]

This doesn't work on any Linux distro that I am aware of, so I guess what I am looking for is help debugging and/or figuring out where to file a bug.

---

