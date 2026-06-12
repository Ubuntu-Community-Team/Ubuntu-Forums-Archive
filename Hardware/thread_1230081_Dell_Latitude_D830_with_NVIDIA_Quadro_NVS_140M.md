---
title: "Dell Latitude D830 with NVIDIA Quadro NVS 140M"
date: 2009-08-03
forum: Hardware
---

### Post by niklasro on 2009-08-03
2.6.28-14-generic #47 Ubuntu i686 GNOME 2.26.1 Enabled NVIDIA accelerated graphics driver version 180 a Dell Latitude D830 with 15.4"WSXGA+ (1680x1050) TFT display and 256MB NVIDIA® Quadro NVS 140M complains about "running in low-graphics mode Failed to initialize the NVIDIA kernel module Screen(s) found but non have a usable configuration

Run in low-graphics mode, display restarts, "there appears to be an X server running on display:0, should another be tried?"
Answered yes

server started on display:1

Log on gnome, low resolution, no 3D, check nvidia display settings
"You do not appear to be using NVIDIA X driver, edit X config nvidia-xconfig and restart X server"

None of which seem to enable full NVIDIA support.

Please reply any recommendations.

xorg.conf:
...
Load "glx"
...
Driver "nvidia"
...
Depth 24
...
Modes "nvidia-auto-select"

Thank you

---

### Post by xamox on 2010-07-20
Anything ever come of this for you?

---

