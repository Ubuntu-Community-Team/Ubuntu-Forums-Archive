---
title: "Ubuntu 8.10 hangs with Radeon 3650"
date: 2009-03-18
forum: Installation &amp; Upgrades
---

### Post by laxdad8992 on 2009-03-18
I am having a problem with booting (install seems to work) to Ubuntu 8.10 on a new laptop with a Radeon HD 3650 graphics card. Things look really nice in Vista (yes, in Vista), but I cannot find anything that will really help me get the drivers set up correctly. 

When I start it up, I see the splash screen, but then, just when it should be showing me the login screen, it goes black, and stays that way. I can  restart (only by powering off, rather unceremoniously), and boot into "recovery" but even then, the only thing I can do is log in as root, and I seem to have no network (I cannot ping my router).

So, what I need is a way to get the right set up - from the command line - to get at least *some* X going. BTW, at least for now I am not worried about 3D acceleration, I just want it to let me login and play around a little...

Oh yeah, also, this is the 64-bit version. I tried installing the 32-bit version, but it seems to try to boot and start X before really installing, so it also goes through the splash screen, and gets to the point where the orange bar makes it all the way across the screen, then goes to a black screen, never to return again.

---

### Post by laxdad8992 on 2009-03-23
Through digging and other searches I found a solution...boot the "recovery" version and go to "root". Edit /etc/X11/xorg.conf file and change the "Device" listing to "vesa", then reboot. The vesa driver is NOT ideal, but it does work. I am still looking to get either "ati" or "radeonhd" going, and getting the screen size right (vesa will only give me 1024x768, but the screen should go to 1366x768 ).

---

