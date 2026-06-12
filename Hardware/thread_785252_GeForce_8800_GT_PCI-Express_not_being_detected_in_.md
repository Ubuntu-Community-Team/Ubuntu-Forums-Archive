---
title: "GeForce 8800 GT PCI-Express not being detected in Hardy Heron"
date: 2008-05-07
forum: Hardware
---

### Post by Gamehunter on 2008-05-07
**Processor:** Intel Core 2 Duo E8400 3Ghz
**Motherboard: **Intel DP35DP Original Motherboard [No onboard VGA available]
**RAM**: 2GB
**Graphics Card:** MSI nVIDIA GeFOrce 8800 GT 512MB PCI-Express 
**Sound:** On Board (SigmaTel Codec)
**OS:** Ubuntu 8.04 Hardy Heron & Windows XP SP2
**Monitor:** CRT 17" Samsung

Issues: Graphics card is not recognized by Ubuntu. Enabling the nvidia "new" driver causes the screen to revert to 640x480.

Xorg.conf detects it as generic Nvidia graphics card.:confused:
 

"PCI device failed to allocate mem"----This message is seen if I edit Xorg.conf to correct screen resolution values.:confused:
This is also seen if I try to run the Ubuntu 7.10 Live CD, though it is not seen with Ubuntu 8.04 Live CD. 

"sudo dpkg-reconfigure xserver-xorg" does not configure or detect card properly.
There are no options to set screen resolution and refresh rates or horizontal and vertical refresh frequencies of the monitor while running the above command in Hardy Heron. 



Manually editing xorg.conf crashes X on restart with the message "PCI device failed to allocate mem". "No screens found":confused:

Repairing Xorg.conf in the recovery console allows me to restart X but again it has the same low resolution of 640x480. :confused:

3D acceleration is not properly working.:confused:



I had no issues on a previous system: Pentium 4 1.7GHz, Intel 845G Motherboard with GeForce 5700 AGP card running Ubuntu 7.10.

It used to work magnificently. :confused:

---

