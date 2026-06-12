---
title: "Synaptic touchpad VS USB"
date: 2006-10-09
forum: Hardware &amp; Laptops
---

### Post by kirys on 2006-10-09
I have a toshiba laptop with a synaptic touchpad, that often have a usb mouse connected to it. 
Somentimes I want to disable the touchpad, ksynaptic works well but only if i dont use /dev/input/mice as input dev for xorg.
This because after i disable the synaptic driver Xorg still receive the command via the driver that is used for the usbmouse.
To fix this i have to point directly the input devices to /dev/input/mouseX.
The problem is that at each boot the various synmink of /dev/input/mouseX point to a different device (the same happen to eventsX) so sometimes mouse0 is the touchpad sometime mouse0 is the usbmouse. ](*,) .
Is there a way  to have the synaptic tpad always inited as mouse0? :confused: 
Thank You

:)

---

