---
title: "Monitor not configured/recognized?"
date: 2008-11-01
forum: General Help
---

### Post by Westerberg on 2008-11-01
My screen resolution as I type this is 640 x 480.

I have a ViewSonic VG2230wm.  Its max screen resolution is supposed to be 1680 x 1050.

If I look under System > Preferences > Screen Resolution, in the box at the top where the screen icon should be is a pink box  with "Unknown" in it.  As I said the max screen resolution available is 640 x 480.

I've noticed a couple error messages stating,

> EE  NV(0): No valid initial configuration found
EE Screen(s) found but none have usable configuration

I am using the NVIDIA 177 driver for my geforce card.

Here is my xorg.conf file:

> Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Any help or insights would be appreciated.

---

### Post by knightcarl on 2008-11-01
I've got the same problem too. Problem is I'm not much an expert on tweaking.

---

### Post by Westerberg on 2008-11-02
bump

---

### Post by Westerberg on 2008-11-02
lol I figured out what the problem was.

There were a lot of cobwebs and dust on the inside of my case that were apparently interfering with my graphics card.  

I turned my leaf blower on the inside of my case and voíla . . . no more problems.

---

