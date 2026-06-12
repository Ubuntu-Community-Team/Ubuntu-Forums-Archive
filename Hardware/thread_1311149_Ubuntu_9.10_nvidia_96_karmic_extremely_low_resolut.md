---
title: "Ubuntu 9.10 nvidia 96 karmic extremely low resolutions"
date: 2009-11-02
forum: Hardware
---

### Post by Funzo22 on 2009-11-02
I was previously running the beta of karmic, on the beta I had this issue once after manually installing the nvidia 96 driver, my solution was to reinstall the beta and enable the driver using the ubuntu proprietary hardware manager (which was successful).

Note that my upgrade to the final version was a complete reinstall. After installing the final version, my terminal flickered non stop so I started in recovery mode and I switched the driver in /etc/X11/xorg.conf to "nv" from nvidia. I was able to start X and get to an 800x600 resolution, however after enabling the nvidia driver, I am unable to get a resolution higher than 640x480. It is detecting my display as a CRT (it is an LCD but through VGA) and it refuses to let me change anything.

I have tried reconfiguring xserver using dpkg, deleting my /etc/X11/xorg.conf and using the nvidia-xconfig to generate a new xorg.conf file (which causes X to start but the monitor just displays "out of range").



Let me know if anybody has had any experience with this issue.


Thanks in advance!


Dustin

---

