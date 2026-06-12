---
title: "Graphic driver problem for dual monitor"
date: 2012-11-12
forum: Hardware
---

### Post by ehsanesl on 2012-11-12
I have FireGL V7600 with propriety driver (AMD catalyst), and I am not able to setup dual monitor. The AMD catalyst does not let me to change anything for dual monitor setup. I tried to change > /.config/monitors.xml file but I get the error > requierd virtual size does not fit.

Is it possible to install open source driver for FireGL V7600? (I am not sure this will solve the problem).

I also should mention that the /etc/x11/xorg.conf looks like this:

> 
    Section "Screen"
            Identifier  "Default Screen"
            DefaultDepth    24
    EndSection

    Section "Module"
            Load    "glx"
    EndSection

    Section "Device"
      Identifier  "Default Device"
            Driver  "fglrx"
    EndSection


---

### Post by MNNorthStars on 2012-11-12
Don't know if this will work for you, but I have ClassicMenu installed. Then, went to System Tools --> Preferences --> AMD Catalyst Control Center (Administrative) and set up dual monitors there. Worked like a charm for my ATI Radeon HD 5870.

---

