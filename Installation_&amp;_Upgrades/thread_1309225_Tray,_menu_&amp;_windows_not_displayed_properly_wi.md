---
title: "Tray, menu &amp; windows not displayed properly with 9.10"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by emma_peel on 2009-11-01
Hello.

I have installed the last version of Kubuntu. Everything went right, but I'm facing a strange problem when logged in : the tray, the K-menu & the frame of the windows are not displayed properly. They are gayed, or dashed, something with color lines ...

Any idea of what should trigger that ?

I did the installation on old PC, with limited graphic capabilities. The display option may be too ambitious for it. On the last version, I was not able to activate all graphical option.

Thank's in advance for the support !

---

### Post by emma_peel on 2009-11-06
Hello.

A little UP for issue ... with a screen shot this time. I found the way to launch the console and start a couple of programs up.

A tried to changed the theme, but it does not change anything.

Thanks again for your support.

---

### Post by mviitane on 2009-11-07
I have similar problems with an eldish Dell c610 Latitude with an Ati Radeon Mobility 750. Dicreasing color depth to 8 from xorg.conf clarifys the panel and everything but otherwise the graphical performance is apparently so poor:( that this is not a workaround.


Marko



marko@Pantoufle:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:01.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
marko@Pantoufle:~$

---

### Post by emma_peel on 2009-11-11
Thank you for your reply.

I finally found a way to correct the bug, by activating the desktop effects (yes, activating, not deactivating). Unfortunately, the option is supposed to enrich the environment, and cause the system to slow down and trigger additional display bugs. Anyway, that's better.

I have noticed a link with the composing option. Sometimes this option is down and the previous bug happens again. :icon_frown:

---

### Post by emma_peel on 2009-11-13
I finally found some interesting threats about this issue :

[http://art.ubuntuforums.org/showthread.php?t=1306215](http://art.ubuntuforums.org/showthread.php?t=1306215)
[http://ubuntuforums.org/archive/index.php/t-1306180.html](http://ubuntuforums.org/archive/index.php/t-1306180.html)

So I'm not alone.:)

---

