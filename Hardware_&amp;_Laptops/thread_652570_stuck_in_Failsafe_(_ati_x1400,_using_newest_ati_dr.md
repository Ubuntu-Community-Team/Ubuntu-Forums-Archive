---
title: "stuck in Failsafe ( ati x1400, using newest ati driver )"
date: 2007-12-28
forum: Hardware &amp; Laptops
---

### Post by Xar_Lock on 2007-12-28
fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.1.7170 Release

glxinfo | grep rendering
direct rendering: Yes

glxgears
12576 frames in 5.0 seconds = 2515.139 FPS
12604 frames in 5.0 seconds = 2520.776 FPS
12598 frames in 5.0 seconds = 2519.598 FPS
13290 frames in 5.0 seconds = 2657.968 FPS
16888 frames in 5.0 seconds = 3377.401 FPS


I still am not able to load up in normal interface. i have to select failsafe to get online. I am at a loss as to what i need to do to correct this issue. The driver never gave me any errors when i installed it via the distro specific package.

Any assistance is much appreciated. As well as any further info you may need i will gladly post. I just didn't want to post my entire xorg file as most of whats in it most likely has no bearing on this issue.

Also note i originally upgraded to this driver because of issues running a game. The game is World of warcraft, using wine, but i am not having any issues with Wine at all. The issues are graphics related, even after all the various tweaks. I'm not sure what i am missing here. prior to this new driver my  

glxinfo | grep rendering
direct rendering: No

And my Framerate was topping about 4600 to 4800. its now slower framerate, but the graphics issue in the game was fixed, save for not being able to load up in the normal session. i am stuck having to use failsafe.

---

### Post by Xar_Lock on 2007-12-30
i found i had to uninstall the xgl server, for me to get back into normal session, and the game i was doing all this work for, still acts a bit funny and now crashes. so prior to this driver it didn't crash but had graphical bugs. those bugs are now corrected from the new driver save for the character never shows on the screen at all, and the game now crashes, so 1 issue corrected, and i have gained a couple new ones. ( starting ot think highly of changing to an nvidia card in this laptop instead of wasting my time on ati.

---

