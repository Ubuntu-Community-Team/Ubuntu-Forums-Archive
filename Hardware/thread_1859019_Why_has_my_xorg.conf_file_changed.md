---
title: "Why has my xorg.conf file changed?"
date: 2011-10-13
forum: Hardware
---

### Post by Twelveone on 2011-10-13
Hi, 

This is a little bizzar, however, I use a cloned image to configure PC's for systems we manufacture. The PC's are all identical so use the same xorg.conf file every time. The xorg.conf is very basic and includes no specific video modes and this has worked perfectly for the last 50 or so PC's with the resolution being successfully configured at what was reasonable for the monitor connected.

Today however a system that had been working suddenly started booting up at 640x480 resolution and not allowing it to be changed. We tried different monitors and vga cables to eliminate them as the cause then started investigating the configuration.

The xorg.conf file had been changed to include 640x480 mode settings for the monitor and screen forcing the PC to use that and nothing else.

Does anyone have any idea how this may have happened, other than the obvious "someone changed it" since I don't think any of the scientists using it would know xorg.conf exists let alone how to change it?

We're using 8.04LTS Hardy Heron

Thanks

Stewart

---

