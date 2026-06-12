---
title: "Using a switchbox causes resolution to be lost on logout"
date: 2008-11-27
forum: Hardware
---

### Post by White Barry on 2008-11-27
Ok so here's my setup, I use my monitor for both Ubuntu and Xbox 360. I switch between them with a simple A/B VGA switch. When I boot (or logout to main login screen) with the switchbox plugged in, Xorg can no longer see my monitor so it defaults to some crazy low resolution (my best guess is 400x320 lol). But if I pull the plugs and run my monitor direct from the video card and Ctrl+Alt+Bkspace it fixes itself then I can log in like normal and switch between them with no issues. 

The problem is, I share the computer with my girlfriend and she needs to have her environment in German while I must keep mine in English. So every time we want to switch users, we have to unplug the switchbox and head back to the login screen. Quite a pain really. Been doing some reading and I can't find anything so far. Basically what I'm looking for is a way to make Xorg not try and detect my monitor and just assume everything is good to go (which it is). Here's my xorg.conf file:

```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

```

Halp??

---

### Post by White Barry on 2008-12-22
Bump ^^

---

### Post by White Barry on 2009-01-11
Any ideas :confused:

---

### Post by White Barry on 2009-01-27
I really hate doing this but still no reply sooooo bump :p

---

### Post by Yashiro on 2009-01-28
It's related to the *Nvidia* driver and the *EDID* information from the monitor I think. There's a setting, method of fixing this. Just search the forum for those terms.

Or perhaps it's simpy a case of forcing the right resolution. 
I can't do any more, don't have an Nvidia to test it with.

In xorg.conf
> Option "UseEDIDFreqs" "FALSE"
Option "ModeValidation" "NoEdidModes, NoEdidMaxPClkCheck" 
Might work. Just backup your .conf in case they don't

---

### Post by White Barry on 2009-01-28
> **Yashiro said:**
> It's related to the *Nvidia* driver and the *EDID* information from the monitor I think. There's a setting, method of fixing this. Just search the forum for those terms.

Or perhaps it's simpy a case of forcing the right resolution. 
I can't do any more, don't have an Nvidia to test it with.

In xorg.conf

Option "UseEDIDFreqs" "FALSE"
Option "ModeValidation" "NoEdidModes, NoEdidMaxPClkCheck" 

Might work. Just backup your .conf in case they don't


Which section would the options go into would it be device, screen, or monitor? Thanks in advance.

---

### Post by Yashiro on 2009-01-28
Do some googling on it? Probably the "Device" tree.

---

### Post by White Barry on 2009-01-28
> **Yashiro said:**
> Do some googling on it? Probably the "Device" tree.

Ok thanks for pointing me in the right direction, however, when I added the 2 lines above into the device section, it forces the monitor into the low-res mode (as if the switchbox were plugged it even though it isnt). 

Extensive googling has still turned up nothing... Any other ideas?

Thanks for the help so far by the way.

---

### Post by Yashiro on 2009-01-29
Well, we know the lines do something.

So I guess all that's left is for you to manually set the right resolution in your .conf. Just fishing here though, I have an ati.

There's loads of references for setting resolutions though. I did read that for Nvidia cards you can tell it to read the monitor data from a file instead. Saw it on these forums this week.

---

### Post by White Barry on 2009-01-29
> **Yashiro said:**
> Well, we know the lines do something.

So I guess all that's left is for you to manually set the right resolution in your .conf. Just fishing here though, I have an ati.

There's loads of references for setting resolutions though. I did read that for Nvidia cards you can tell it to read the monitor data from a file instead. Saw it on these forums this week.

Awesome thanks for the tip, I won't be able to mess with it today unfortunately but I will let you know sometime tomorrow how it goes. Thanks again, you're being a huge help.

---

