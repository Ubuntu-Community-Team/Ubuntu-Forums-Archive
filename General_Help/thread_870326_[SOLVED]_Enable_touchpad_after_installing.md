---
title: "[SOLVED] Enable touchpad after installing"
date: 2008-07-25
forum: General Help
---

### Post by palomar on 2008-07-25
Hi,
I installed Ubuntu at my desktop PC on a usb harddisk. Afterwards I plugged in the usb harddisk in my laptop. (Almost) everything works fine, but since Ubuntu didn't detect the touchpad at installation (beacause I installed on my desktop), it is not enabled on my laptop (when booting from a live cd it is enabled and I can use the touchpad as scrollwheel and there is a tab called 'touchpad' in mouse settings).

So I need to enable the touchpad. Searching this forums brought me to add this lines to xorg.conf:
```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"SHMConfig"	"on"
EndSection

```
But I still don't see an extra tab in mouse settings. Even when I install gsynaptics from repository, it warns me to set SHMConfig to 'true'. true or on both don't work.

So how to enable this the easy way?

---

### Post by palomar on 2008-07-26
already solved using this tutorial: [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

---

