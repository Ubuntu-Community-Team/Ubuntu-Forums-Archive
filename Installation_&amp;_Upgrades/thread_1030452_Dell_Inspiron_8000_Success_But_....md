---
title: "Dell Inspiron 8000 Success But ..."
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by chaotos on 2009-01-04
Hi. I am new to the forums. I have an old Dell Inspiron 8000 and decided to try installing Ubuntu 8.10 on it. I now have a nice 1200 x 1600 Ubuntu desktop in front of me (Dell only made this high resolution screen briefly; idiots complained that the icons were too small).

This is the video card reported by lspci:

01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M4 AGP

At first I was stuck with a tiny screen but I found this post:

[http://liltux.wordpress.com/2007/12/28/installing-ubuntu-on-dell-inspiron-8000-laptop/](http://liltux.wordpress.com/2007/12/28/installing-ubuntu-on-dell-inspiron-8000-laptop/)

Following these instructions I added these lines to the monitor section of /etc/X11/xorg.conf:

HorizSync 31-82
VertRefresh 40-110

Bingo! On the second reboot (???) I get a nice full screen and can select 1200 x 1600 for screen resolution.

This post also suggests:

"I also changed the color depth from 24bits to 16 bits and inserted the following lines under the device section.

Option “AGPMode” “4&#8243;
Option “AGPSize” “32&#8243;
Option “EnablePageFlip” “true”
Option “Display” “BIOS”
Option “SWCursor” “true”
Option “CCEusecTimeout” “20000&#8243; "

So I went ahead and added them.

I am unclear about the color depth thing. Where is this set or do the above lines do this somehow?

Wayne
Boulder, Colorado

---

