---
title: "Left and Right Click = Middle Click (Mouse)"
date: 2008-11-23
forum: General Help
---

### Post by Jimmerz28 on 2008-11-23
Currently I'm attempting to play World of Warcraft, its working fine except when I press Left + Right mouse buttons at the same time they are registering as a Middle Mouse click.

I did some searching but all the articles discussing modifying xorg.config were outdated.

Is there anyway to fix this so that my left and right buttons will not register as a middle click?

Thanks in advance.

---

### Post by ibuclaw on 2008-11-23
Seems more like something that is happening on behalf of WINE, rather Linux.

Check out your default WINE configuration or have a look round on their forums.

Regards
Iain

---

### Post by RHTopics on 2008-11-23
In file /etc/X11/xorg.conf change the option "Emulate3Buttons"  from "true" to "false".  If the option does not exist, you may need to add it in.

Below is a partial listing of my /etc/X11/xorg.conf to assist you in finding it in your /etc/X11/xorg.conf file:

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "false"
EndSection

```

Without knowing more about your setup, I believe this should turn it off.

---

### Post by Jimmerz28 on 2008-11-24
I have to say its doesn't seem to be a WINE specific problem; in Ubuntu pressing the LEFT + RIGHT mouse buttons perform the same actions as MIDDLE CLICK.

Here is my current xorg.conf:

```
Section "Monitor"
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
	Disable	"dri2"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
EndSection


```

I added in the "Input" section, restarted and still had the problem. I'll check on the WINE forum and see if I can find anything to update.

I've got Ubuntu Ibex and a Microsoft Wireless Intellimouse Explorer 2.0 (if that helps with anything).

Thanks!

---

### Post by CatKiller on 2008-11-24
> **RHTopics said:**
> In file /etc/X11/xorg.conf change the option "Emulate3Buttons"  from "true" to "false".  If the option does not exist, you may need to add it in.

Actually, with Intrepid, this option gets completely ignored in favour of some obscure new HAL configuration somewhere. I've not managed to find a simple way to stop the > extended input device "Macintosh mouse button emulation" pretend device from being loaded.

---

### Post by Jimmerz28 on 2008-11-24
> **CatKiller said:**
> Actually, with Intrepid, this option gets completely ignored in favour of some obscure new HAL configuration somewhere. I've not managed to find a simple way to stop the  pretend device from being loaded.

Yea I found the same HAL config. info but it really didn't answer anything. Does anyone have a more friendly solution?

---

