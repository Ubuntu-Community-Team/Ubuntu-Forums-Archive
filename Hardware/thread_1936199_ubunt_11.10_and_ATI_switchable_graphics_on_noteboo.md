---
title: "ubunt 11.10 and ATI switchable graphics on notebook with dim display issue"
date: 2012-03-05
forum: Hardware
---

### Post by Imagery on 2012-03-05
Hi everyone,

I have a HP notebook with ATI switchable graphics, and I installed the latest ATI driver off their site, which works fine.

But I do have the brightness issue where at login, my display is dark and I have to manually set the brightness at each restart.

I did try and edit the Rc.local file, as noted by others, where you set the brightness to 5 or 10: 

"echo 10 > /sys/class/backlight/acpi_video0/brightness"

When I try and save it, I get this message in Terminal:

(gedit:3801): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory


So far nothing is working to set the brightness to max at startup. Even used a Python script I found with no luck.

Here's my lspci | grep VGA listing:


00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 07)
01:00.0 VGA compatible controller: ATI Technologies Inc NI Seymour [AMD Radeon HD 6470M]


Sorry for the long post, anyone have any ideas? I assume this is realted to switchable graphics.

Thank you

---

