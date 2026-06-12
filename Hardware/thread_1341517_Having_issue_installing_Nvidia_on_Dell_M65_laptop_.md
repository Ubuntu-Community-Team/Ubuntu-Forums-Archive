---
title: "Having issue installing Nvidia on Dell M65 laptop with Ubuntu 9.10"
date: 2009-11-29
forum: Hardware
---

### Post by sincityharley on 2009-11-29
What I am looking to do is hook my laptop up to my flat panel tv. My TV has a vga input and of course my laptop has a VGA output. I am able to hook my windows laptop up this way but not my ubuntu dell laptop. When I try and go to System > Administration > Hardware Drivers. It will show me three possible Nvidia drivers to install. I tired all of them at different points. They all get stuck at installing drivers. The status bar gets 1/2 way and then never moves after that. I have let it wait at one point for an hour+. Any ideas would be greatly appreciated. Thanks

---

### Post by phiro on 2009-12-05
HI Harley.
I own a M65 too and have a dual setting system too. However, I do not use the VGA connection on the laptop but the DVI connection on a docking station. The OS drivers do recognize the dock-DVI out of the box, the Nvidia drivers need to be configured first by the nvidia-settings applet.
A few things I remembered was : 
- Do not connect any other screens to the laptop while installing the nvidia drivers.
- Desinstall and PURGE the nvidia drivers first then RESTART the laptop. Do not reboot since I found the drivers appears to stay resident for some reason
- Resinstall the drivers
- Connect the VGA screen
- Start nvidia-settings applet
- Detect screens, and do the settings you require. 

Hope this does the trick for you.

---

