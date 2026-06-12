---
title: "NVidia DVI bug, fixed"
date: 2009-11-02
forum: Hardware
---

### Post by Outworlder on 2009-11-02
Since my Karmic upgrade, I've had a problem with not being able to use my DVI monitor - the display always went blank. Downloading the newest driver from nvidia didn't help.

Turns out the new driver, for some reason, tries to display the image using VGA instead of DVI. It says that the connected monitor is on CRT-0.

I've fixed it by adding

Section "Device"
    Option         "ConnectedMonitor" "DFP"
EndSection

---

