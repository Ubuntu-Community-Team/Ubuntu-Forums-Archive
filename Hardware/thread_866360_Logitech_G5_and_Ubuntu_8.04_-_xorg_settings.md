---
title: "Logitech G5 and Ubuntu 8.04 - xorg settings"
date: 2008-07-21
forum: Hardware
---

### Post by namaster on 2008-07-21
Well i recently downloaded ubunutu and installed it on dell inspiron 6400. Its 8.04 Hardy. In my xorg.cfg i am not able to see logitech mouse or anything. Do i need to edit it manually? Also, the mouse tracking is not good. Do i need to install separate drivers for it?  I installed btnx for all buttons detection and it works but problem is tracking and also updated my polling rate :)

Here is my xorg.cfg for input device:

```


Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizEdgeScroll" "0"
EndSection

```

Any suggestion on what to use in mouse acceleration and mouse sensitivity ?

thanks !

---

### Post by aleb on 2008-08-19
Try installing Wine and then download Mouse Rate Checker from [http://tscherwitschke.de/mouseratechecker.html](http://tscherwitschke.de/mouseratechecker.html) (the statically linked exe) and run it. I have the same "mouse" driver specified in xorg.conf and this application shows average report rates for my Logitech G9 of up to 1200Hz. Tell us what it reports for you.

The following command prints "0" on my system. 
```
cat /sys/module/usbhid/parameters/mousepoll 
```
I don't know what 0 means. That value should represent the number of milliseconds between the polls, for example "2" means an interval of 2ms which leads to a rate of 500Hz.

I managed to change that number by running the following command, and it does have the expected effect in Mouse Rate Checker, for example "4" leads to averages around 250Hz.
```
sudo rmmod usbhid && sudo modprobe usbhid mousepoll=2
```

So maybe you don't have to change anything..

See this thread for more info:
[http://ubuntuforums.org/showthread.php?t=392494](http://ubuntuforums.org/showthread.php?t=392494)

---

### Post by namaster on 2008-08-20
Well i do run on 2ms but thats not the problem. Problem is its movement. It has acceleration on and somehow mouse movements are not linear while playing game. So, i cant play any fps based game from ubuntu.

---

### Post by aleb on 2008-08-20
What mousepad are you using?

---

### Post by namaster on 2008-08-23
> **aleb said:**
> What mousepad are you using?

Everglide titan gaming mouse pad :P

---

