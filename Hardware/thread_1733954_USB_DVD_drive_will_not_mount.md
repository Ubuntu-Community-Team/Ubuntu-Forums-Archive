---
title: "USB DVD drive will not mount"
date: 2011-04-19
forum: Hardware
---

### Post by Nomad Dome on 2011-04-19
I've had a problem with my external USB DVD writer which seems to have gotten progressively worse as I upgraded.  Drive used to work on Ubuntu 9.

Media will not mount.  A few weeks ago, I could play DVD movies using VLC, but could not access any other files on a cd.  This week, not even DVD movies will play on VLC.  Drive works fine on my wife's macbook.

Ubuntu 10.10
HP Invent DVD R/RW USB
I have no internal optical drive on this box.

lsusb shows:
Bus 002 Device 004: ID 093a:2620 Pixart Imaging, Inc. 
Bus 002 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 002: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 05e3:0701 Genesys Logic, Inc. USB 2.0 IDE Adapter
Bus 001 Device 006: ID 0846:6a00 NetGear, Inc. WG111v2 54 Mbps Wireless [RealTek RTL8187L]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Drive has power from computer (lights on, disks spin when inserted)

---

### Post by Nomad Dome on 2011-04-19
okay... odd.  After running the lsusb, VLC can now read DVD movies again.  Media inserted still does not show up under places/media.

---

