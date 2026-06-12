---
title: "How do you change performance levels with nouveau?"
date: 2011-04-01
forum: Hardware
---

### Post by inso_741 on 2011-04-01
```
dmesg | grep -A4 "available performance level"
```
gives:
```
[    5.159142] [drm] nouveau 0000:01:00.0: 3 available performance level(s)
[    5.159146] [drm] nouveau 0000:01:00.0: 0: memory 100MHz core 169MHz shader 338MHz voltage 1150mV fanspeed 100%
[    5.159150] [drm] nouveau 0000:01:00.0: 1: memory 301MHz core 275MHz shader 550MHz voltage 1150mV fanspeed 100%
[    5.159153] [drm] nouveau 0000:01:00.0: 2: memory 702MHz core 475MHz shader 950MHz voltage 1200mV fanspeed 100%
[    5.159175] [drm] nouveau 0000:01:00.0: c: memory 302MHz core 275MHz shader 550MHz voltage 1150mV

```
now how do I know which ones active and how do I switch in between them?

---

### Post by inso_741 on 2011-04-02
If anyone wants to give it a try:

add nouveau.perflvl_wr=7777 to the kernel command line
and then use "echo 'level' > /sys/class/drm/card0/device/performance_level"

use appropriate level that you find via --- dmesg | -A4 "available performance level"
thats it 
warning is not stable yet, may crash you system or burn your card so try at your own risk!!

---

### Post by breakdevize on 2011-05-11
> **inso_741 said:**
> If anyone wants to give it a try:

add nouveau.perflvl_wr=7777 to the kernel command line
and then use "echo 'level' > /sys/class/drm/card0/device/performance_level"

use appropriate level that you find via --- dmesg | -A4 "available performance level"
thats it 
warning is not stable yet, may crash you system or burn your card so try at your own risk!!

Thanks, exactly what i was looking for! Sadly the temp didnt go down much so is there a way to change the voltage level?

---

### Post by breakdevize on 2011-05-11
And btw, when i restart the settings are not saved, how to make them permanent?

---

### Post by inso_741 on 2011-05-13
> **breakdevize said:**
> And btw, when i restart the settings are not saved, how to make them permanent?


you can specify the level on boot using 
perflvl=$LEVEL module option in addition of course to perflvl_wr=7777
but its not recommended so better do it manually after 
booting to be safe

as for the voltage, its read directly from the bios
so your best chance is to modify bios...

hope this hepls...:P

---

