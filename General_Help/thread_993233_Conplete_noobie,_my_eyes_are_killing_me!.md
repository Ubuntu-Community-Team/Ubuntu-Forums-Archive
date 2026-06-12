---
title: "Conplete noobie, my eyes are killing me!"
date: 2008-11-25
forum: General Help
---

### Post by WOOHOOHOO on 2008-11-25
Hi there,

I'm new to Ubuntu and very grateful for the excellent package. But, it's killing my eyes, everything on my screen is too small and my eyes are hurting. I installed Ununtu 8.10 desktop edition.

I tried changing resolutions to find a good 1 in monitor resolution settings but the higher the res, the small it gets. When i ran XP, i got an ok one. I have a really old GVC laptop and a tiny screen.

I've tried various things in the terminal suggested on other forums but now of them worked. i have no idea what they mean in most.

Any ideas. I play Scrabble a lot and can't play as i cant see the screen. I tried zooming, but the letters distorted.

Any ideas please? I'm getting desperate.


I did a 'lspci' and got this:

[COLOR="Blue"]"00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS961 [MuTIOL Media IO]
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 46)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter"[/COLOR]

---

### Post by kanikilu on 2008-11-25
What resolution is Ubuntu using now, and what resolution did you find comfortable in Windows?

---

### Post by Trafferth on 2008-11-25
WOOHOOHOO,

You can go to "System > Preferences > Appearance" and change the default font sizes from there.  In addition, you can make the icons bigger or smaller in a open window by either right-clicking and selecting "zoom in / zoom out" or by holding down the left control key and using the scroll wheel on your mouse.

Hope this helps,

-T :)

---

### Post by philinux on 2008-11-25
Set the resolution for the monitors native resolution.

Then in system>prefs>appearance Fonts tab increase the font point size for the items to want to appear larger. Experiment.

Also under the fonts tab choose lcd subpixel smoothing and under details choose hinting slight.

---

### Post by WOOHOOHOO on 2008-11-25
It's on the highest, 1024 x 768 (4:3).Refresh rate 60. I don't know what i had on XP, it was default and i never had to do anything with it.

That's the highest resolution, it's the smallest on the monitor but the text doesnt distort too much.

Other options are:

1024x576 (16:9)
960x600 (16:10)
960x940 (16:9)
800x600 (4:3)
768x576 (4:3)
856:480 (16:9)
800x480 (16:10)
720x480
640x480
640x400
512:384
400x300
320:240
320:200

The 800:600 is a decent size, but on java games it doesnt resize correctly, it goes all bity, were as on XP it was smooth.

---

### Post by WOOHOOHOO on 2008-11-25
> **philinux said:**
> Set the resolution for the monitors native resolution.

Then in system>prefs>appearance Fonts tab increase the font point size for the items to want to appear larger. Experiment.

Also under the fonts tab choose lcd subpixel smoothing and under details choose hinting slight.

I'll try this. Which option would be for internet font. I wish i new XP's font, i was used to them.

I don't know what screen i have, the laptop i bought in Thailand 5 years ago. It's a GVC, that's all i know. Is SiS a monitor?

---

### Post by WOOHOOHOO on 2008-11-26
hi again, still no luck sadly.i played with the fonts,that didnt help. Any other ideas?  ireally dont want to revert back to XP (as i've also lost the disc!)

Thanks

---

### Post by Trafferth on 2008-11-26
Could you send us a screenshot?  Perhaps something is incorrectly configured - as far as I can tell in a Virtual Machine running a 1024x768 resolution, Ubuntu and Windows XP fonts and windows sizes, etc. are more or less the same.

If you change all of the fonts from size 10 to size 12, say, then the holders such as window title bars, etc. will grow with them.  Also, you can set the default zoom level for Nautilus by opening any location ("Places > Home Folder" will do), selecting "Edit > Preferences" and setting the default zoom levels to something other than the defaults.  Try 150% for the icon zoom and 75% for the list zoom view for starters (I am not sure whether you run Nautilus in icon or list mode, so increase both values).

This should sort out any size - related problems.

If it is still unpleasant to view the screen, then perhaps the refresh rate is set incorrectly.  I know that you can damage a monitor by incorrectly setting the refresh rate, but it should be safe to try changing it a bit.  Go to "System > Preferences > Screen Resolution" and try changing the refresh rate.  Also try using the "Detect Monitor" button to see if Ubuntu can recognize your monitor and set the correct resolution and refresh rate.

Let us know how you get on.

Good luck!

-T :)

---

