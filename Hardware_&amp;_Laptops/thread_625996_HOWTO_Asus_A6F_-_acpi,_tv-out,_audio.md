---
title: "HOWTO: Asus A6F - acpi, tv-out, audio"
date: 2007-11-28
forum: Hardware &amp; Laptops
---

### Post by suoko on 2007-11-28
This is an howto to fix some problems with my Asus A6F with HDA audio card and intel 945GM:

AUDIO:
if missing, add to the end of file /etc/modprobe.d/alsa-base the following string:
options snd-hda-intel model=asus

TV-OUT:
to get TV-OUT with PAL use this script:
xrandr --output LVDS --mode 1024x768; xrandr --output TV --set TV_FORMAT PAL; xr
andr --output TV --mode 1024x768

ACPI (suspend and hibernate not working yet: see [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/172675):](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/172675):)
if missing add to file  /etc/modules the following string:
asus_laptop

PLEASE SEE HERE for an upgrade on audio fixing on hardy:
[http://ubuntuforums.org/showthread.php?t=771429](http://ubuntuforums.org/showthread.php?t=771429)

---

