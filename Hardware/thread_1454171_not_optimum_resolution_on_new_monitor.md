---
title: "not optimum resolution on new monitor"
date: 2010-04-14
forum: Hardware
---

### Post by legrega on 2010-04-14
I had sony crt 17" and evertyhing worked fine in 1600X1200. That monitor is toast and now I have Samsung 226BW 22" and Pentium 2 350# MMX AGP PCI and I cannot get a higher resolution than 800X600.   Please help me. Here is my xorg.conf:

# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
EndSection

and more inlspci -s 01:00.0 -v
 01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro
 AGP 1X/2X (rev 5c)
        Subsystem: ATI Technologies Inc Device 0084
        Flags: bus master, VGA palette snoop, stepping, medium devsel,
 latency 64
        Memory at e4000000 (32-bit, non-prefetchable) [size=16M]
        I/O ports at d000 [size=256]
        Memory at e6000000 (32-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at 30000000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel modules: atyfbfo: 

Please help me, thanks ... Love, Grega the Smart duck

---

