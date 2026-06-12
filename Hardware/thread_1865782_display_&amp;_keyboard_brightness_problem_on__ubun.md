---
title: "display &amp; keyboard brightness problem on  ubuntu 11.10"
date: 2011-10-20
forum: Hardware
---

### Post by alieblice on 2011-10-20
hi 
fn key not working for display brightness it was fine on 11.04
it just show at the up right corner of display that the light is changing but light is not changing  
i tried these ways but none of them helped 
[http://ubuntuforums.org/archive/index.php/t-1596438.html](http://ubuntuforums.org/archive/index.php/t-1596438.html)

keyboard lights not working in 11.10 but it was fine on 11.04 

sony/vaio f13u  Ubuntu 11.10 

any help is really  appreciated

---

### Post by alieblice on 2011-10-21
**all the problems so lved**


** fore screen back-light**
[http://ubuntuforums.org/showthread.php?t=1561966](http://ubuntuforums.org/showthread.php?t=1561966)

do this :

*********************************************************************

Ok so, new solutions for sony vaio f series notebook...

If you have Display Back light issue, follow this instruction for solution. It is easy to apply...

[http://code.google.com/p/vaio-f11-li...splayBacklight](http://code.google.com/p/vaio-f11-li...splayBacklight)

If you have display resolution problem and not to get 1600x900 or 1920x1080 resolution according to your sony vaio lcd display. Your xorg.conf file need some modifications for this.

Just add this following line to the device section on /etc/X11/xorg.conf file

Option "ConnectedMonitor" "DFP-0"
Option "CustomEDID" "DFP-0: /proc/acpi/video/NGFX/LCD/EDID"


The Device section should look like this

Section "Device"
Identifier "InternalCard"
Driver "nvidia"
Option "ConnectedMonitor" "DFP-0"
Option "CustomEDID" "DFP-0: /proc/acpi/video/NGFX/LCD/EDID"
Option "RegistryDwords" "EnableBrightnessControl=1"
EndSection

*************************************************************************





** fore keyboard back-light**
[https://bbs.archlinux.org/viewtopic.php?id=121566](https://bbs.archlinux.org/viewtopic.php?id=121566)

do this : 

*************************************************************************

To enable the keyboard backlight  `/sys/devices/platform/sony-laptop/kbd_backlight` has to be set to "1".  Also there is /sys/devices/platform/sony-laptop/kbd_backlight_timeout`,  where you may set: 0(default)=10secs, 1=30secs, 2=60secs and  3=unlimited.

*************************************************************************

---

### Post by KYSL on 2011-10-31
> **alieblice said:**
> **all the problems so lved**


** fore screen back-light**
[http://ubuntuforums.org/showthread.php?t=1561966](http://ubuntuforums.org/showthread.php?t=1561966)

do this :

*********************************************************************

Ok so, new solutions for sony vaio f series notebook...

If you have Display Back light issue, follow this instruction for solution. It is easy to apply...

[http://code.google.com/p/vaio-f11-li...splayBacklight](http://code.google.com/p/vaio-f11-li...splayBacklight)

If you have display resolution problem and not to get 1600x900 or 1920x1080 resolution according to your sony vaio lcd display. Your xorg.conf file need some modifications for this.

Just add this following line to the device section on /etc/X11/xorg.conf file

Option "ConnectedMonitor" "DFP-0"
Option "CustomEDID" "DFP-0: /proc/acpi/video/NGFX/LCD/EDID"


The Device section should look like this

Section "Device"
Identifier "InternalCard"
Driver "nvidia"
Option "ConnectedMonitor" "DFP-0"
Option "CustomEDID" "DFP-0: /proc/acpi/video/NGFX/LCD/EDID"
Option "RegistryDwords" "EnableBrightnessControl=1"
EndSection

*************************************************************************





** fore keyboard back-light**
[https://bbs.archlinux.org/viewtopic.php?id=121566](https://bbs.archlinux.org/viewtopic.php?id=121566)

do this : 

*************************************************************************

To enable the keyboard backlight  `/sys/devices/platform/sony-laptop/kbd_backlight` has to be set to "1".  Also there is /sys/devices/platform/sony-laptop/kbd_backlight_timeout`,  where you may set: 0(default)=10secs, 1=30secs, 2=60secs and  3=unlimited.

*************************************************************************

I tried it and it does not work permanently, assuming you can modify the file (with su privileges).

The solution was to:
1. edit (or create) /etc/modprobe.d/options.conf
2. add *options sony-laptop kbd_backlight=1*
3. reboot

---

