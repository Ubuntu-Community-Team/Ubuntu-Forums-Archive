---
title: "Dual monitor, incorrect resolutions :("
date: 2008-10-25
forum: General Help
---

### Post by cmulax on 2008-10-25
so got myself a new laptop and i have it hooked up to an external monitor via VGA cable.  both my external and laptop screens should be at 1680x1050 = 3360x1050.  trying to set this up using nvidia-settings and twinview.

this is what it currently looks like: 

[IMG]http://i405.photobucket.com/albums/pp131/vicariouscheese/screenshot-1.jpg[/IMG]

the right angle is where the split in the monitors is, which is completely wrong as they should be equal in size... also the black area to right i can actually pan through if i move my mouse over there.

i have an nvidia 9600m GT using the newest drivers...

annnd heres my xorg.conf:

```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
	SubSection "Display"
		Virtual	3360 1050
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
	Disable	"dri2"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver		"nvidia"
	Option		"TwinView"
	Option		"TwinViewOrientation" "CRT-0 LeftOf DFP-0"
EndSection

```

from past experience with other computers this xorg.conf seems incredibly sparse... if that comes with the xorg update thats cool, it just makes me a little suspicious..

ill be posting if i solve this myself, but any input is greatly appreciated!

---

### Post by cmulax on 2008-10-25
bump... ive been trying every xorg.conf i can think of and they all give me similar issues.  i believe its the nvidia driver thinking that the external can only support a certain (smaller) resolution and just panning to the size i want it to be.

---

