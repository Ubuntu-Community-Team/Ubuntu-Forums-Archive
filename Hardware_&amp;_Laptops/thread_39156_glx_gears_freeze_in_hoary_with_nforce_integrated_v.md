---
title: "glx gears freeze in hoary with nforce integrated video and nvidia driver"
date: 2005-06-03
forum: Hardware &amp; Laptops
---

### Post by discord on 2005-06-03
Hello,

I was having similar issues with the mouse pointer being frozen but I had 2100 memory on my nforce2 motherboard with onboard G4mx dual head (hp d325) but switched memory and those issues went away. However when I start glxgears I see the gears at first and then they dissappear and either the Xserver crashes and restarts or computer freezes and get a bunch of crap on the monitors. 

Here is the section of my xorg.conf that I feel is relevant

Section "Device"
Identifier "NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]"
Driver "nvidia"
BusID "PCI:1:0:0"
# Option "NvAGP" "1"
Option "TwinView" "true"
Option "SecondMonitorHorizSync" "22.0-82.0"
Option "SecondMonitorVertRefresh" "50.0-76.0"
Option "MetaModes" "1280x1024,1024x768"
Option "TwinViewOrientation" "RightOf"
# Option "Xinerama" "on"
Option "HWCursor" "false"
Option "RenderAccel" "true"

EndSection

I have tried tweaking most of these options.

---

