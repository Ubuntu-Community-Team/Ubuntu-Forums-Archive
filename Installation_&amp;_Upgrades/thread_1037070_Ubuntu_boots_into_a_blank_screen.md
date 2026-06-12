---
title: "Ubuntu boots into a blank screen"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by vmusoyan on 2009-01-11
I just installed Ubuntu 8.10 on my AOpen 1558 laptop with an Intel 915GM graphic card. When I run "dpkg-reconfigure xserver-xorg", it detects the "vesa" driver, which does not allow me to set the resolution to anything higher than 800x600. When I change the driver from "vesa" to "intel" in "xorg.conf", I see only a blank screen when the computer boots.

Any idea about what I can do to get a 1024x768 resolution?

Thanks,
Vahe

---

### Post by MIKE SILVA on 2009-09-07
Hi,

This solution doesn't work with me, and I have less resolution: 640 x 320.

But the place where i get the solution, they have comment it works. Maybe for you.

Edit you xorg.conf and insert this text:


Section "Device"
Identifier "Configured Device"
Driver "vesa"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Device"
SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection
EndSection 


Best Regards

---

