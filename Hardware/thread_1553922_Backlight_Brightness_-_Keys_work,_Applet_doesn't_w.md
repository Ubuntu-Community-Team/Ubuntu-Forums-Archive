---
title: "Backlight Brightness - Keys work, Applet doesn't when using FGLRX"
date: 2010-08-15
forum: Hardware
---

### Post by kandarz on 2010-08-15
Hardware: Dell Studio 15 (1558) 
[LIST]
[*]1920x1080 screen
[*]ATI Mobility Radeon HD 5470
[/LIST]

Running Ubuntu Lucid 10.04

**Driver: default Ubuntu driver (Radeon?)**
[LIST]
[*] Function Keys: works
[*] Brightness Applet: semi-works, can scroll to adjust brightness, icon says "Cannot get laptop panel brightness", buttons don't work, can't click to change brightness
[*] Gnome-power-manager brightness on boot: works
[/LIST]

```
for file in $(ls /proc/acpi/video/*/LCD/brightness) ; \
do { echo $file && cat $file && echo ; } ; done
```
Shows:
```
/proc/acpi/video/M86/LCD/brightness
levels:  6 12 18 24 30 36 42 48 54 60 66 72 78 84 90 100
current: 6
```

**Driver: FGLRX**

[LIST]
[*] Function Keys: works
[*] Brightness Applet: doesn't work
[*] Gnome-power-manager brightness on boot: doesn't work
[/LIST]

```
for file in $(ls /proc/acpi/video/*/LCD/brightness) ; \
do { echo $file && cat $file && echo ; } ; done
```
Shows:
```
/proc/acpi/video/M86/LCD/brightness
levels:  6 12 18 24 30 36 42 48 54 60 66 72 78 84 90 100
current: 6
```

Really end-goal here is to get FGLRX driver working so it remembers screen brightness. I don't care so much about the applet.

---

