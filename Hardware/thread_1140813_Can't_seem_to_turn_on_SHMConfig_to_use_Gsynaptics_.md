---
title: "Can't seem to turn on SHMConfig to use Gsynaptics in Jaunty"
date: 2009-04-28
forum: Hardware
---

### Post by rainwalker on 2009-04-28
I'm trying to use Gsynaptics to edit my touchpad settings like I did in Hardy, but it's telling me I haven't set SHMConfig to "true" even though (I think) I have. Here is my current Xorg.conf:
> Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "InputDevice"
   Identifier "Synaptics Touchpad"
   Driver "synaptics"
   Option "SendCoreEvents" "true"
   Option "Device" "/dev/psaux"
   Option "Protocol" "auto-dev"
   Option "HorizScrollDelta" "0"
   Option "SHMConfig" "on"
EndSection

Section "ServerFlags"
	Option	"DontZap"	"False"
EndSection

Am I doing something wrong?
I have gnsynaptics version 0.9.14-8 and the 0.99.3-2ubuntu4 synaptics touchpad driver.

---

### Post by Barry Carroll on 2009-04-28
I enabled SHMConfig by using hal which I think is the newer way of doing things.  I don't think editing the X config is recommended any more.

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

I used the above as a guide for my own machine and SHMConfig is set although I don't use GSynaptics.  If ```
synclient -l
``` works then SHMConfig is working iirc.  Perhaps it's just a GSynaptics problem if that's the case.

---

