---
title: "multi monitor problems"
date: 2011-07-11
forum: Hardware
---

### Post by henry9419 on 2011-07-11
i have an nvidia gpu and dual monitors on my computer and im running ubuntu 11.04 just upgraded 10.04>10.10>11.04 yesterday and i had no problems with dual monitors until i installed nvidias drivers and now i can configure them but they dont stay configured on reboot and im not able to get them exactly the way i want anyway...i want the botom edges of the screens to be aligned graphically like they are pyshically and not the tops and i want the top taskbar to extend all the way across the top of the left monitor and i want to set up a panel on the bottom edge of both screens like in 10.04 and 10.10 and have it across both monitors but have it act as one....any suggestions??? i really need help! THANKS!!!!!!!!!!!!!!!!!

---

### Post by wolfen69 on 2011-07-12
Are you using nvidia-settings as super user? Open it with:
```
gksu nvidia-settings
```
Make your changes, apply, save to xorg, and reboot.

---

### Post by fenrasa on 2011-07-15
I have a working multimonitor setup with nouveau drivers.
But I dont use that fancy 3D compiz magic anymore. Didnt perform at all, also black screens and general annoyance.

First of all, purge the nvidia closed source drivers.
Then install xserver-xorg-video-nouveau or xserver-xorg-video-all, dunno :P

Afterwards, I edited my xorg.conf manually, here it is, maybe it helps a bit.
```
# three screens, two cards, nvidia nouveau, ubuntu 11.06, 
# working 3d on ONE screen (0, tested with minecraft) 
# enable 3d via ubuntu experimental drivers nouveau

Section "ServerLayout"
		Identifier "XorgConfigured"
		Screen 0	"Screen0" 0 0
		Screen 1	"Screen1" RightOf "Screen0"
		Screen 2 	"Screen2" LeftOf "Screen0"
		Option "Xinerama" "1"
EndSection

Section "Device"
	Identifier	"8400gs0"
      	Driver	"nouveau"
		Screen	0
		BusID	"PCI:1:0:0"
EndSection

Section "Device"
	Identifier	"8400gs1"
      	Driver	"nouveau"
		Screen	1
		BusID	"PCI:1:0:0"
EndSection

Section "Device"
	Identifier "Quadro280"
	Driver		"nouveau"
	BusID		"PCI:4:1:0"
EndSection

Section "Monitor"
	Identifier "right"
EndSection

Section "Monitor"
	Identifier "middle"
EndSection

Section "Monitor"
	Identifier "left"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device		"8400gs0"
	Monitor		"middle"
EndSection

Section "Screen"
	Identifier "Screen1"
	Device		"8400gs1"
	Monitor		"right"
EndSection

Section "Screen"
	Identifier "Screen2"
	Device		"Quadro280"
	Monitor		"left"
EndSection
```

funfact of the config is following part:
the screen in the device section is the video cards output, not the above defined screen in the layout. whatsha say to that?
```
Section "Device"
	Identifier	"8400gs1"
      	Driver	"nouveau"
		Screen	1
		BusID	"PCI:1:0:0"
EndSection
```

---

