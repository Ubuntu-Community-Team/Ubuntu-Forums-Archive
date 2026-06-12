---
title: "Wily has trouble with Intel GMA 950 graphics"
date: 2015-11-17
forum: Hardware
---

### Post by ecowan on 2015-11-17
I just installed Wily on my test bench. It's a Lenovo M52 tower with Intel GMA 950 Dynamic Video Memory Technology 3.0 graphics.
It will boot and run for a minute or two, and then the screen snaps and gets completely garbled. Sometimes using shift-tab to flip to another window will partially rectify the display, but it quickly looses it again.

I haven't been able to find reports of similar problems.

Thanks. - Erny

---

### Post by blm-ubunet on 2015-11-18
Try to disable "SNA" acceleration in the i915 driver..
You need to create/edit  /etc/X11/xorg.conf file..

if file **does not** exist (most likely) then create with:
```
sudo Xorg -configure
```
Insert this into device section.
Option      "AccelMethod"  "UXA"

Logout & log back in should be enough to reload X server.

---

### Post by ecowan on 2016-01-06
I couldn't figure out how to get Xorg -configure to run. If I remember correctly, it complained that lightdm was running. When I dropped out to command mode and stopped lightdm, it complained about something else.
But I did find a solution at [http://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1507255](http://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1507255)

---

