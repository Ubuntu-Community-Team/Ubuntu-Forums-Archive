---
title: "Radeon 9800 pro - Polygon corruption"
date: 2008-05-08
forum: Hardware
---

### Post by norrei on 2008-05-08
Hello,

I have installed Ubuntu Hardy Heron, and am pleased with it overall. The only issue I am experiencing is polygon corruption (many discolored, oddly sized triangles jutting out of where the real 3d object should be) in virtually all openGL driven software, ranging from the "Bubbles" screensaver to games run in cedega/wine.

I've got the latest ATI proprietary driver installed (8.4.76 or something like that), and glxinfo tells me direct rendering is being used (as well as fglrxinfo telling me my drivers aren't Mesa). Videos and whatnot play fine (even 720p), but OpenGL seems to be producing these odd decolored-polygon artifacts.

There's nothing listed in the "Device" section of my xorg.conf except what was there from aticonfig --initial setup. I have dual-monitors set up at a total screen size of 2560x1024, which exceeds my maximum texture size of 2048x2048. Would this be affecting anything? I know it prevents me from using beryl and XGL. If so, how would I retain "big-screen" style dual monitors, but still be able to use XGL and the like? Is there a way to trick my video card? (I've read something about virtual desktops or something...).

Thanks!

---

### Post by norrei on 2008-05-08
Alright, I compiled the 2.6.25.2 kernel and the corruption is gone, but now openGL performance just seems to be very slow. I'm sure there's something I have to put in the "device" section or xorg.conf, but not sure what. Are there any options I need to enable/disable to boost performance?

Thanks!

---

