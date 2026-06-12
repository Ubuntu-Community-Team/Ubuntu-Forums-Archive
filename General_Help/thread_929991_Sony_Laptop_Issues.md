---
title: "Sony Laptop Issues"
date: 2008-09-25
forum: General Help
---

### Post by Killtodie on 2008-09-25
I got a Sony VGN-NR180E.
Few issues it has running Ubuntu.

1. Wireless switch works but the light doesn't. Id be nice to have a light
2. When I plug in headphones it doesn't mute the speakers.
3. Cant control LCD brightness. Keyboard shortcuts don't work and the slider in the OS doesn't work either.

If anyone has solutions for these, Id like to have these issues fixed. Specialy the headphone thing.

---

### Post by Nepherte on 2008-09-25
[LIST=1]
[*]Install the package linux-backports-modules-hardy:
```
sudo apt-get install linux-backports-modules-hardy
```
[*]Follow the section named 'Manually specify module parameters' in [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
[*]You can control them with xbacklight, but unfortunately there's a bug with it. You can find information about it here: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/173652](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/173652)

It basically comes down to this:
Install xbacklight:
```
sudo apt-get install xbacklicht
```

Add the following to /etc/rc.local:
```
xrandr --output LVDS --set BACKLIGHT_CONTROL native
/etc/init.d/acpid restart
```

And edit /etc/acpi/sonybright.sh (it's a good idea to back up this file first) so that is contains only this:
```
#!/bin/bash
if [ "x$1" = "xdown" ]; then
   xbacklight -time 100 -steps 10 -dec 10 2>/tmp/sonybright.log
elif [ "x$1" = "xup" ]; then
   xbacklight -time 100 -steps 10 -inc 10 2>/tmp/sonybright.log
else
   echo >&2 Unknown argument $1
fi
```
[/LIST]

---

