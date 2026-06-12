---
title: "Ubuntu 14.04 stuck at 640x480 dell s2009wb monitor"
date: 2015-02-07
forum: Hardware
---

### Post by Alduins_Khajiit on 2015-02-07
I plugged my Dell s2009wb monitor into a Linux Ubuntu 14.04 computer and it says it failed all resolution tests and told me it will be set at 640x480. the monitor is capable of 1600x900 and all the resolutions that failed, worked on all Windows versions that monitor has been hooked up to, everything from Windows 98, XP, & 7. XP even included it's native 1600x900 resolution but Ubuntu doesn't like my monitor for some reason
 
How can I remedy this?
 
from Google:
 
> 

Your search - *ubuntu stuck 640x480 dell s2009wb* - did not match any documents.
Suggestions:

[LIST]
[*]Make sure all words are spelled correctly.[/*] 
[*]Try different keywords.[/*] 
[*]Try more general keywords.[/*] 
[*]Try fewer keywords.[/*] 
[/LIST]


 
 
I searched the software center for both "dell monitor" and "s2009wb" and both got "no results" I go into software updates and additional drivers, it says "no proprietary drives are in use" and "No additional drivers are available"

setting/display only shows 640x480 or the other 480p 16:9 & 16:10 variants

Ubuntu worked fine with 1280x1024 on an older monitor that this replaced.

---

### Post by efflandt on 2015-02-08
What may matter is video card/chip, drivers, and most likely, type of cable connection to the display. VGA is analog and Linux often cannot tell what the display is capable of, so it may just offer common defaults. DVI or HDMI are digital and may better communicate the capabilities of your display to Linux. Even that may not be perfect, for my HDTV it is proper 1080p resolution, but I have "Just Scan" set on my LG HDTV to properly size/center the video signal it is receiving.

What results do you get for the following commands in a terminal window:```
lspci -nnk | grep -iA2 VGA
xrandr
```It may be possible with either an /etc/X11/xorg.conf file, an EDID, or xrandr commands to switch to the native resolution of the display.

---

