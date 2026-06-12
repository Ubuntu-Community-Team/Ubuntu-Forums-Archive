---
title: "Configure HDMI on ASUS P5Q-EM"
date: 2009-06-27
forum: Hardware
---

### Post by alebreeze on 2009-06-27
I have an ASUS P5Q-EM mobo and EVERY THING works FINE wit  Jaunty 64 EXCEPT HDMI out I am planing on building an HTPC using this mobo. Sound and Eithernet are working perfectly no changes made DVI works fine two VGA for sure works fine. The only thing I can't use is HDMI it says in the TV "HDMI No Signal" I am using direct cable. Here is the /etc/X11/xorg.conf file content:

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"




Hope I can find an answer here.............. :confused:

---

### Post by alebreeze on 2009-06-27
I am able to configure the video BUT no sound through HDMI ?????

---

