---
title: "logitech ultrax remote r-rc6"
date: 2008-04-30
forum: Hardware
---

### Post by harrydg on 2008-04-30
hey,

since my upgrade from 7.10 to 8.04, a lot of buttons on my remote don't work anymore. evtest does see everything, i add that device to my xorg.conf, but still, xev doesn't see a lot of the keys...

i tried a lot of things, but it just won't work.

the relevant part of my xorg.conf:
Section "InputDevice"
	Identifier	"remotekeyboard1"
	Driver		"evdev"
	Option		"Name" "Logitech USB Receiver"
	Option		"XkbRules" "xorg"
	Option		"Device" "/dev/input/by-path/pci-0000:00:1a.2-usb-0:1:1.0-event-kbd"
	#Option		"Device" "/dev/input/by-path/pci-0000:00:1a.2-usb-0:1:1.1-event-"
	#Option		"Phys" "usb-0000:00:1a.2-1/input1"
EndSection

i tried with all the device and phys options, even with /dev/input/by-id/...
with a lot of other options... the weird part is: it recognises SOME of the keys, but just not all, while in 7.10, it recognised allmost all keys (some were double, which i don't get either, because the kernel sees them as they are)

can anyone shed some light here?

tnx

---

