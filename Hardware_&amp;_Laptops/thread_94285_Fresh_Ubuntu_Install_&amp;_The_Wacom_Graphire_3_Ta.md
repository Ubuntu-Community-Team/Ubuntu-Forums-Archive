---
title: "Fresh Ubuntu Install &amp; The Wacom Graphire 3 Tablet"
date: 2005-11-23
forum: Hardware &amp; Laptops
---

### Post by motionsiren on 2005-11-23
I'm running Ubuntu 5.10 on a x86 machine, using a PS/2 Keyboard and Mouse and my Wacom Graphire 3 is the only USB device plugged into my machine (USB ports *do* work and have been tested with other devices).

When I boot up for the first time (nice bootup display now!) everything works, including my Graphire 3 tablet (pen & mouse), which was plugged into my machine even before I powered up.

However, both the pen and mouse are stuck in "absolute" mode, amongst other little preferences that I can't seem to find switches for in the Gnome control panel

* Everything is stock 5.10 install. Haven't modified the kernel, xorg.conf, etc. I simply plugged my Wacom tablet into USB. This may be my problem right here - but since there seems to be multiple solutions to getting this up and running, I'm posting here to ask...

Here is what the kernel says about the Wacom when I plug it in

```

[4306999.003000] usb 1-1: new low speed USB device using ohci_hcd and address 4
[4306999.112000] usbhid: probe of 1-1:1.0 failed with error -5
[4306999.121000] input: Wacom Graphire3 on usb-0000:00:03.0-1

```

hrm, the failed probing looks suspecious but im not sure it's related(?)

My main complaints and goals to solve are:

* The mouse is in "absolute(?)" mode (top, left = top left of sreen, etc.). I'd like it to be "relative(?)" is thats the proper term to use.
* I'd like to switch the pen in and out of "relative" mode, as sometimes I like using it as a mouse. It's currently "absolute" only.
* the wheel on the mouse is inverted (simple xorg fix?)
* pressure sensitivity? not even sure how to test this.

Any help out there? I wouldn't mind gathering notes on this task and updating the wiki. 

This would also be a nice thing to clear up before our next release.

K

---

### Post by motionsiren on 2005-11-23
Also...

Im assuming xorg.conf will become involved in this... right?

Are there any solutions out there to get this device working and managable via user-land tools? I figure - if the device works right out of the box, why can't that same method of operation support the basic functions that im most likely going to have to put into xorg.conf?

I don't really care about this part personally, but I think it'd be a high(er) priority for future releases to hunt down a dev team and get this feature(s) integrated into whatever... maybe the "mouse" item in Gnome's control panel.

---

### Post by 23meg on 2005-11-23
[quote=motionsiren]
* The mouse is in "absolute(?)" mode (top, left = top left of sreen, etc.). I'd like it to be "relative(?)" is thats the proper term to use.[/quote]Assuming you have the wacom-tools package installed, you can do this with the xsetwacom command. Type ```
xsetwacom set param
``` to learn all the tricks you can perform with it.
[quote=motionsiren]* I'd like to switch the pen in and out of "relative" mode, as sometimes I like using it as a mouse. It's currently "absolute" only.[/quote]Again, xsetwacom is the userspace tool you'll need.
[quote=motionsiren]* the wheel on the mouse is inverted (simple xorg fix?)[/quote]Haven't tried this myself since i don't own a Graphire but ```
Option "ZAxisMapping" "5 4"
``` specified in all your tablet device sections in xorg.conf should fix it.
[quote=motionsiren]* pressure sensitivity? not even sure how to test this. [/quote]You can test the raw data your tablet is producing with the wacdump utility which also comes in wacom-tools.

Sorry for not writing a detailed how-to on getting it working; I'm a bit too tired for that right now but you can find basic instructions on [the linuxwacom website]("http://linuxwacom.sf.net") in the meantime. I have a detailed guide on getting tablets working in Breezy under construction, and it will also hopefully include an autodetect script that I'll also submit for possible inclusion in Dapper.

---

### Post by MetalMusicAddict on 2005-11-23
This should give you some useful info:
[HOWTO: Enable your Wacom Intous/Graphire Tablet with Pressure Sensitivity]("http://www.ubuntuforums.org/showthread.php?t=25151")

Pressure sensitivity works great with The GIMP but need to play with Inkscape also.

I intend on updating it soon.

---

### Post by jejones3141 on 2005-12-04
There is useful info there, but when I try to tell GIMP about the tablet, it claims that there are no extended input devices, despite my having made the appropriate changes to xorg.conf. Has anyone managed to get a Wacom Graphire 3 working under Breezy?

---

