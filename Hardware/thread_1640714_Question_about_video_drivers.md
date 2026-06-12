---
title: "Question about video drivers"
date: 2010-12-08
forum: Hardware
---

### Post by horseatingweeds on 2010-12-08
I have a few questions about video drivers.

I installed the NVIDIA driver (NVIDIA accelerated graphics driver (version current) [Recommended]) Afterward, things looked the same, good. I checked the resolution it was set at, which was AUTO at 1440x900. I tried other resolutions, but they all made the screen look horrible, even the ones with the same ratio. So I gave up.

Later I restarted. On startup, the login screen looked fine. But after logging in, the screen came up with a fuzzy looking resolution, 1152x864 or something close to that. I can go to the NVIDIA X Serer Settings screen and change it back to 1440x900, but upon restarts, the resolution switches back. This happens regardless of if I set an explicit resolution or us AUTO. 

Playing around, (image attached) I pushed the "Save to X Configuration File". That gave me this error: Failed to parse existing X config file '/etc/X11/xorg.conf' I read in the NVIDIA Ubuntu HowTo, to run* **sudo nvidia-xconfig*** to fix the error. This stopped the error and has the driver writing to the file now, but the resolution still changes after startup. I've tried changing the resolution with root privileges: gksudo nvidia-settings

What should I be doing here? If I disable the NVIDIA driver and restart will this start me fresh with the Ubuntu driver, or allow me to reinstall the NVIDIA driver fresh? What should I do? 

If I make another user, can I experiment with drivers for that user without it effecting other users?

---

