---
title: "nvidia won't retain monitor resolution on login"
date: 2009-07-13
forum: Hardware
---

### Post by doublempi on 2009-07-13
On my wife's desktop with an Environ monitor, I can use the nvidia utilities to change the resolution to 1200 x 1024 with no problem. I then save the xorg.conf. But when I reboot, the login screen comes up in the 1200 x 1024 resolution, which is good, but then after I'm logged in the resolution is at 640 x 480. I can reset it using nvidia, but that's only good for the session. If I log out, the login screen is at 1200 x 1024, but after logging in I'm back to 640 x 480.

I've googled, searched forums, and so on, but no luck. Can anyone help, please?

I'm using 9.04

Thanks,
Mike

---

### Post by doas777 on 2009-07-13
I have a box that doesn't do overscan on my TV right unless I run 
```
gksu nvidia-settings -l
``` from my Startup applications.
give it a try.

---

### Post by doublempi on 2009-07-13
Solved: found this at:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/362704](https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/362704)

Jaunty uses the settings in "/etc/X11/xorg.conf" to configure the display resolution at Ubuntu startup. "xorg.conf" settings are written by "nvidia-settings".
 Jaunty uses the settings in "/home/username/.config/monitors.xml" to reset the display resolution (when you log into your user). The settings in  ".config/monitors.xml"  are written by "gnome-display-properties".
 1. The values in ".config/monitors.xml" are not automatically synchronized when "nvidia-settings" is used to change the display resolution, so it is necessary to update those values by running "gnome-display-properties" (System->Preferences->Display).
 2. In my case (I have a nvidia FX-5200) "gnome-display-properties" is not detecting correctly the "Refresh Rate" parameter, so I manually updated the ".config/monitors.xml" file ("rate" parameter) with the correct value.
 ----------------
"nvidia-settings" shows the Refresh Rate next to the "Resolution" in "X Server Display Configuration". If this value is set to "auto", you can see the value with "nvidia-settings -q RefreshRate".

---

### Post by stavebna_chemia on 2010-01-26
Man, you saved me. I spent couple evenings trying to figure out what is wrong with my xorg.conf (I learned a lot, I must say) but I overlooked such a simple solution--basically I was misguided by System | Preferences | Display tool, that said that my driver (Nvidia) does not supprt necessary extension and that I should use Nvidia config app instead.

It was quite suspicious why login screen is in high resolution (1920x1080@6o Hz) and after successful login the screen is reset to 800x600--apparently not a problem with xorg settings: right now it is obvious...

I found the culprit (.config/monitors.xml) and I am going to reboot to enjoy the full resolution from the moment of login :-)

Thanks

---

