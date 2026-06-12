---
title: "Double-finger scrolling and right click in *any* synaptics touchpad laptop/notebook"
date: 2007-11-24
forum: Hardware &amp; Laptops
---

### Post by zeh on 2007-11-24
[B]Hi everyone,

I recently bought an Apple Macbook and i'm trying with no sucess to install Ubuntu Gutsy in my new toy. While trying to get things working, i took my old Compaq Presario 2700T notebook to test some improvements. I always admired that old Compaq. Its a Intel PIII 1.2Ghz, 1Gb 133Mhz  RAM, awesome 1600x1200 pixels display, 32Mb ATI Mobility Radeon M6 discrete video card and a really nice sounding JBL speakers.

So, i was searching for some info in the net to find if is possible to get double finger tapping and scrolling like the Macs touchpad. As Macs also use Synaptic, i start to wonder that this could be done, as linux synaptic driver recognizes two and even three fingers resting on touchpad.

Googling for xorg.conf configs for Macbooks, i found some information and changed some synaptics parameters. I got double finger right click working!! I don' t know if this is news, but i was pretty surprised!
I'm assuming that this will work on any laptop with synaptics touchpad...

Now i' m trying to get double scrolling working, which i think is one of the great features of OSX.
Any hints?

This is how i managed to get double finger right click working:

Open the xorg.conf file: (backup the actual xorg.conf file)[/B]
> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_save
sudo gedit /etc/X11/xorg.conf

**Add in the synaptics section:**
	Option 		"TapButton2" 		"3"
	Option 		"TapButton3" 		"2"

** Also added the SHMConfig. Follow this great wiki to see how manage synaptics options in Ubuntu and Kubuntu:
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

**So, this is my final Synaptics section in xorg config:**
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option 		"CorePointer"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option 		"TapButton2" 		"3"
	Option 		"TapButton3" 		"2"
	Option		"SHMConfig" 		"true"
EndSection


tip: If your xorg file doesn't have the synaptics section and your laptop features this touchpad brand, probably is because some bug that not recognizes it during install.
Do a xorg reconfigure:

> sudo dpkg-reconfigure -phigh xserver-xorg

With this simple option i can right click on the touchpad just as in OSX. :)
Now there must be a way to get double finger scrooling. I will search for more info.

Regards!

Zeh

---

### Post by zeh on 2007-11-25
[B][COLOR="Blue"]Amazing!

Got two finger scrolling working on my Presario laptop!!
So simple and so great! I really didn't know that this was possible on non Apple hardware!
Now i have an old laptop with Compiz with all exposé-like features and two finger right click and scrolling! Great!

This is how i did!

Just add these simple lines to the synaptic section on xorg.conf that i showed above:

Option "VertTwoFingerScroll"     "true"
Option "HorizTwoFingerScroll"   "true"[/COLOR][/B]

---

### Post by zeh on 2007-11-25
> **zeh said:**
> [B][COLOR="Blue"]Amazing!

Got two finger scrolling working on my Presario laptop!!
So simple and so great! I really didn't know that this was possible on non Apple hardware!
Now i have an old laptop with Compiz with all exposé-like features and two finger right click and scrolling! Great!

This is how i did!

Just add these simple lines to the synaptic section on xorg.conf that i showed above:

Option "VertTwoFingerScroll"     "true"
Option "HorizTwoFingerScroll"   "true"[/COLOR][/B]
[COLOR="Red"][B][SIZE="4"]
PLASE REPORT IF YOU GET THIS WORKING ON YOUR NOTEBOOK.

Best regards,

Zeh[/SIZE][/B][/COLOR]

---

### Post by bettlebrox on 2008-01-02
On a Dell 700m this works for me (the lines that are **bold** are the ones I added):

[INDENT]Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
**	Option 		"CorePointer"**
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
[B]	Option		"HorizScrollDelta"	"0"
	Option 		"VertTwoFingerScroll"	"true"
	Option 		"HorizTwoFingerScroll"	"true"
	Option 		"TapButton2" 		"3"
	Option 		"TapButton3" 		"2"[/B]
EndSection
[/INDENT]

However, the scroll speed seems a little fast for my tastes.

---

### Post by gree on 2008-01-03
On my Fujitsu-S. V3205 it works too, but the scroll speed is a tad fast, and 50% of the times when I use it, firefox jumps back a page in history.

---

### Post by lewt539 on 2008-07-08
So, is it confirmed that the double-finger scrolling and right click works on Linux Ubuntu on an synaptics touchpad for notebooks? 
I just received my new laptop Asus F8SN. I have been thinking of learning to use ubuntu, but gave up because of lack of time. So does this method work? If so, how? I know almost nothing about how to operate Linux.

What is the "xorg.conf" file, and where would I find it and edit it's source content, if I were to install Ubuntu and try this out for myself?

---

