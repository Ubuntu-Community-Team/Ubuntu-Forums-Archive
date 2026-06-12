---
title: "Vid drivers for intel 945GM on gateway laptop"
date: 2009-01-30
forum: Hardware
---

### Post by johns-noobie on 2009-01-30
By no means am I an expert on anything. So that might give you an idea that I am new to Ubuntu. I am trying to jump ship off of the uss microsoft. I am almost there, with just a few more pieces of software to go.

I have been using Ubuntu 8.04 for a month or two now, fighting issues left and right trying to get dual booting going and getting my favorite software running.

I have dual boot up and running with Vista and Ubuntu 8.04 on a Gateway MX-8738 laptop that has the 17 in screen. It uses the Mobile Intel 945GM/GMS, 943/940GML Express chipset family for video with 224 MB of mem.
(according to Vista)

The one program I have left to get running is a CAD software with 3d rendering) for woodworking. With the troubleshooting I have done, it is pointing to a video issue.

The "lspci | grep VGA" command recognizes the hardware.

According to Synaptic the driver is installed on the computer.

According to Device manager, under VGA Controller, there is an intel corp Direct Rendering Manager Device (with a ? to the left).

Hardware Drivers does not show anything listed.

Display Config is showing the i945 hardware, but no driver. 


xorg.conf has this:

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

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection


So, what it seems like, it can see the hardware, but does not use the correct driver. My guess is that it is using a generic driver that seems to work for the most part.

I think (meaning I hope) that switching to the intel driver will correct my software issue.

I can find bits and pieces about this issue, but most of it does not make sense to a noobie (aka me).

I do have auto updates running so I sould be on the latest kernel.

I did notice someone say that libdrm1 is needed, which I have libdrm2.

I hope that I have provided enough info for a solution. I am at wits end on this one.

What am I missing?

Thanks ahead to anyone that can help the poor noob.

John.

---

### Post by Papo1988 on 2009-01-30
I too have the same problem. From what i gather you have to change "Vesa" to "intel" in the xorg.conf somewhere, i have not tried as of yet, and i could be completely wrong lol. If anyone with more experience could help it would be greatly appreciated.

---

### Post by restouffer on 2009-01-30
To make sure that your xorg uses the intel driver, it SHOULD be a matter of simply putting:
```
  Driver "intel"
```
in the Device section and restarting X.

P.S. - The intel driver may just, currently, not be working for your chipset.  I have a machine with a Mobile Intel 945GM/GMS, 943/940GML Express chipset and the intel driver currently results in a blank screen and a few error messages.  I have been using vesa while I wait for it to start working again.

---

### Post by johns-noobie on 2009-01-30
Papo1988, 
   Thanks for the info. As an fyi, I do not have an entry with Vesa in the .conf file. When I put  Driver "Intel" as suggested by restouffer, restart xserver, every time I run a high graphic program like Google Earth, the xserver restart in a low graphic mode and I end up with an altered xorg.conf file with some confusing stuff. I end up with one device set to i810 intel driver and one Vesa driver. If I reset the second setting from Vera to i810, things improve some, but they are still jumpy.

Restouffer,
   I wish it was that simple, but that is not the way my luck goes. I tried you suggestion, but it did not work for me. I did do some research and Intel has some directions to build the driver. Its over my head, but I do have a co-worker that might help out with this. Thanks for you help.

---

