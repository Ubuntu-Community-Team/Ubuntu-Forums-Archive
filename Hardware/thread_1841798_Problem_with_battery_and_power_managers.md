---
title: "Problem with battery and power managers"
date: 2011-09-10
forum: Hardware
---

### Post by jagster on 2011-09-10
I'm having this problem since I installed Xubuntu 11.04, this didn't seem to happen with kubuntu 10.04 or with other distros that used HAL.

When I have the laptop (Compaq 515) connected to AC and running xfce-power-manager the "Your battery is fully charged" or how much charge the battery has appears every few seconds and after a while it crashes using 100% of my CPU. This doesn't happen with gnome-power-manager, but when using it indicator-plugin starts hogging all of my memory after a while. When the laptop isn't plugged in it seems to work fine.

Also everytime xfce-power manager flashes the message upowerd uses 100% of my cpu for a second or two.

When I run *$upower -m* I get this:

```
[04:49:59.421]	device added:     /org/freedesktop/UPower/devices/battery_BAT0
[04:49:59.421]	device changed:     /org/freedesktop/UPower/devices/battery_BAT0
[04:49:59.421]	device changed:     /org/freedesktop/UPower/devices/battery_BAT0
[04:50:01.041]	device changed:     /org/freedesktop/UPower/devices/battery_BAT0
[04:50:02.040]	device changed:     /org/freedesktop/UPower/devices/battery_BAT0
[04:50:03.040]	device changed:     /org/freedesktop/UPower/devices/battery_BAT0
[04:50:04.041]	device changed:     /org/freedesktop/UPower/devices/battery_BAT0
[04:50:17.368]	device removed:   /org/freedesktop/UPower/devices/battery_BAT0
[04:50:18.473]	device added:     /org/freedesktop/UPower/devices/battery_BAT0
[04:50:18.474]	device changed:     /org/freedesktop/UPower/devices/battery_BAT0
[04:50:19.040]	device changed:     /org/freedesktop/UPower/devices/battery_BAT0
[04:50:20.040]	device changed:     /org/freedesktop/UPower/devices/battery_BAT0
[04:50:21.041]	device changed:     /org/freedesktop/UPower/devices/battery_BAT0
[04:50:22.040]	device changed:     /org/freedesktop/UPower/devices/battery_BAT0
[04:50:23.040]	device changed:     /org/freedesktop/UPower/devices/battery_BAT0
[04:50:36.443]	device removed:   /org/freedesktop/UPower/devices/battery_BAT0
[04:50:37.564]	device added:     /org/freedesktop/UPower/devices/battery_BAT0
```

This goes on and on all the time, everytime the battery seems to be removed and added is when xfce-power-manager flashes the message.

When I run *$ acpi_listen* I get this:

```
battery BAT0 00000081 00000001
battery BAT0 00000081 00000001
battery BAT0 00000081 00000001

```

Each of those messages coincide with the battery removed and added of upower.

I have been dealing with this without running any power manager, and running xfce-power-manager just to change the brightness or check the battery charge, which obviously gets annoying.

Is there any way to fix this? 
Thanks

---

