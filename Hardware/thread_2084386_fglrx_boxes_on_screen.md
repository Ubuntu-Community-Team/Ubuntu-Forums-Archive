---
title: "fglrx boxes on screen"
date: 2012-11-15
forum: Hardware
---

### Post by Freek07 on 2012-11-15
I switched from nvidia (worked superb on closed source drivers) to ati (craptacular- couldn't even scroll normally in firefox on AMD website drivers) and after using **ubuntu provided** fglrx drivers, scrolling is smooth(er) but I'm noticing rectangulars in windows- they dissapear as soon as window is redrawn but it's really annoying.

That's what I'm talking about, for example (grey box inside window until window is redrawn).
[IMG]http://www.apollonus.net/misc/boxes.jpeg[/IMG]

There are no driver specific options in xorg.conf other than "driver" "fglrx".

sysinfo:
Linux xxxxxx 3.2.0-32-generic #51-Ubuntu SMP Wed Sep 26 21:33:09 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

$ dpkg -l | grep fglrx
ii  fglrx                         2:8.960-0ubuntu1.1             Video driver for the AMD graphics accelerators
ii  fglrx-amdcccle                2:8.960-0ubuntu1.1             Catalyst Control Center for the AMD graphics accelerators
ii  xvba-va-driver                0.7.8-1ubuntu3                 XvBA-based backend for VA API (AMD fglrx implementation)

$ glxinfo | grep rendering
direct rendering: Yes

$ glxinfo | grep OpenGL
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 7700 Series
OpenGL version string: 4.2.11627 Compatibility Profile Context
OpenGL shading language version string: 4.20

$ lspci | grep AMD
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 683d
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Device aab0

Any ideas?

---

### Post by QIII on 2012-11-15
Actually, the "Ubuntu provided" closed source driver is one Canonical got from AMD/ATI as they usually do for inclusion at release time in April and October.  There's nothing special about it other than that a MOTU packaged it.

What version of Ubuntu?

Did you uninstall the nVidia driver before removing the card and replacing it?

When you decided to use the driver from the repo, did you first uninstall the driver you had installed directly from AMD's website?

If you installed using their scripts, you have to use the amdconfig utility to uninstall it.

Did you install from AMD by building a .deb?

If you built a .deb, you have to use dpkg to uninstall it.

---

