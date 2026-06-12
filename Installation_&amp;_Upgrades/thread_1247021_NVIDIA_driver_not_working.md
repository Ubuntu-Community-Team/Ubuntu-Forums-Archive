---
title: "NVIDIA driver not working"
date: 2009-08-22
forum: Installation &amp; Upgrades
---

### Post by kulkarniniraj on 2009-08-22
Hi
    I am having ubuntu 8.04 64 bit edition. I am having integrated nvidia 6100 Geforce card.
    I have installed some nvidia packages ( may be installed automatically). But when I see restricted drivers section, it shows that my nvidia driver is ENABLED but 'not in use'. 
    Recently I found out that i could directly install driver from nvidia.com. I tried their latest driver but when I restarted X-server, it shows PC running on low-graphics mode then even if I select NVIDIA driver, restricted driver section shows it is still not in use, and my screen resolution is fixed to 800x600. 
   So I finally my renamed my old xorg.config.backup to xorg.config. 
    Now I can change my screen resolution. But restricted driver manager still shows I have nvidia driver which is not in use.
    And also now I have  problems running opengl programs. It gives an error as :
     Xlib:* extension "GLX" missing on display ":0.0".
 Can anyone please help me?

---

### Post by mikewhatever on 2009-08-23
It's not advisable to install several drivers for the same hardware. If you prefer using a manually installed driver from Nvidia website, first disable the restricted driver provided by Ubuntu, and vice versa.

---

