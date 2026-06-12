---
title: "Xorg.conf Mouse config"
date: 2008-10-29
forum: General Help
---

### Post by _Mike on 2008-10-29
Hi there.

In Ubuntu 7 my [Labtec Wireless Optical Mouse]("http://www.labtec.com/index.cfm/gear/details/AMR/EN,crid=29,contentid=627") worked perfectly. I tried upgrading to 8.04 a while ago, only to find the mouse no longer worked, so I stayed with 7. I've decided to get upto date with 8.10 and the problem still persists. I looked in the xorg.conf and found that there isn't any mouse configuration at all.

I've never had to fiddle with xorg, so I don't know a lot about using it to add hardware. I've tried several attempts at writing a Section but they've all failed, a couple have even made Ubuntu unbootable. (Only fix is to reset xorg from recovery).

This is what I have currently:

```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Name"		"Labtec Wireless Optical Mouse"
	Option		"Protocol"	"usb"
	Option		"ZAxisMapping"	"5 4"
EndSection

```

I've run out of ideas, so I'm having to post here. Any help would be really appreciated.

If it helps, when Unplugging and replugging the usb dmesg returns this:
```

PPdev0: registered pardevice
PPdev0: unregistered pardevice
PPdev0: registered pardevice
PPdev0: unregistered pardevice
PPdev0: registered pardevice
PPdev0: unregistered pardevice

```

---

