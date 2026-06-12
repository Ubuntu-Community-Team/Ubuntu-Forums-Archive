---
title: "Display Driver for Radeon 7000 on IBMT30?"
date: 2006-04-10
forum: Hardware &amp; Laptops
---

### Post by Clunsford on 2006-04-10
So what drivers am I supposed to be using for an ATI mobility 7000? the intergrated IBM T30 kind?

I tried following the ATI guied, it didn't work well, i had to run xorg config from consol to get x server working again.

Suggestions?

---

### Post by Clunsford on 2006-04-10
M7 LW [Radion Mobility 7500] To be exact...

---

### Post by adamkane on 2006-04-10
You need to use the radeon driver. Don't use the ati driver  or the fglrx driver.

Here is what my /etc/X11/xorg.conf file looks like for my ATI Radeon 7200 card. Change AGPSize to correspond to your card memory:

> 
Section "Device"
    Identifier    "ATI Technologies, Inc. Radeon 7200 (R100 QD)"
    Driver        "radeon"
    BusID        "PCI:1:0:0"
    Option        "AGPMode"    "2"  # 4 doesn't seem to work here
    Option        "AGPSize"    "64" # the default is 8
    Option        "RingSize"    "8"
    Option        "BufferSize"    "2"
    Option        "EnablePageFlip"    "true"
    Option        "EnableDepthMoves"    "true"
    Option        "RenderAccel"    "true"
        # Eyecandy Stuff
    Option        "AccelMethod"     "4"
    Option        "EnablePageFlip"     "true
    Option        "DDCMode"
    Option        "SubPixelOrder" "NONE"
    Option        "ColorTiling"     "false"


---

### Post by Clunsford on 2006-04-11
[QUOTE=adamkane]You need to use the radeon driver. Don't use the ati driver  or the fglrx driver.

Here is what my /etc/X11/xorg.conf file looks like for my ATI Radeon 7200 card. Change AGPSize to correspond to your card memory:[/QUOTE]


OK so i basically copy and pasted what you had there, sept i left my card name (the first line) and i set my AGPsize to 16 as necissary... BUT

when ido fglrx info i get this
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)


thats not riht is it??

---

### Post by adamkane on 2006-04-11
You probably need to uninstall fglrx. fglrx is for non-Radeon cards.

Make sure you've rebooted with your new radeon driver. Test the driver by installing and playing a 3D game, or previewing a 3D screensaver.

---

### Post by Clunsford on 2006-04-13
[QUOTE=adamkane]You probably need to uninstall fglrx. fglrx is for non-Radeon cards.

Make sure you've rebooted with your new radeon driver. Test the driver by installing and playing a 3D game, or previewing a 3D screensaver.[/QUOTE]




figured out what was wrong i think, i added a few 'otions' that wernt in yours, and set AGP mode to 4... seemed to do the trick

oh and i did uninstall the fglrx driver (the one that says ATI in the debs) don't know if that did it or not.    

oh and now that i got hardware accel working, my battery lats about 20 minuts playing falconseye (not even openGL?) 


so... yeah thats the next project, power efficienty

but thanks

---

