---
title: "Dell Studio 1537 laptop &amp;&amp; X Window Issue (with Dual Monitor)"
date: 2009-06-12
forum: Hardware
---

### Post by mikeshn on 2009-06-12
I've installed Ubuntu 9.04 through WUBI ([http://wubi-installer.org/](http://wubi-installer.org/)).
1st monitor is LG Electronics 19" Wide Screen && 2nd is Dell Studio 15" screen

Resolution is 1024X768(4:3) on both monitors.
However, on Dell Studo 1537 laptop on both side there are 2 black lines.
Therefore, there is space on laptop screen that are not used.
xorg.conf file is below.
Note: It's working fine when second monitor is not connected

########################## X Window (xorg.conf) ###################
Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
SubSection "Display"
Virtual 2048 768
EndSubSection
EndSection

Section "Device"
Identifier "Configured Video Device"
EndSection

---

