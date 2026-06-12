---
title: "About to STAB my Raedon 9200 SE (dual screen problems)"
date: 2005-09-16
forum: Hardware &amp; Laptops
---

### Post by keene on 2005-09-16
Alright, I've got a raedon 9200 SE on a basic, freshly installed 5.04 Ubuntu system.

I've installed the fglrx drivers from Synaptic, and created a new Xorg.conf, and everything works wonderfully. I have my 16x12 resolution, the colors are good, and it clones onto my TV perfectly. Wonderful, right?

But I don't want it to CLONE onto my TV, I want it to be an extended desktop.

I was able to get that to work with the newest ATI drivers (8.16.20), but then, the monitor was incredibly washed out. No matter what I did to my xorg.conf, I couldn't fix the washing out of the screen.

So I've gone back to the original drivers, but now, for the life of me, I can't figure out how to get my TV to be an extended desktop.

My xorg.conf as it currently stands:

---------------------------------

Section "dri"
     Mode 0666
EndSection

Section "Module"
     Load "dbe"

SubSection "extmod"
     Option "omit xfree86-dga"
EndSubSection

     Load "type1"
     Load "freetype"
     Load "glx"
     Load "dri"
EndSection

Section "Files"
     FontPath "/usr/X11R6/lib/X11/fonts/local/"
     FontPath "/usr/X11R6/lib/X11/fonts/misc/"
     FontPath "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
     FontPath "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
     FontPath "/usr/X11R6/lib/X11/fonts/Type1/"
     FontPath "/usr/X11R6/lib/X11/fonts/75dpi/"
     FontPath "/usr/X11R6/lib/X11/fonts/100dpi/"
EndSection

Section "InputDevice"
     Identifier "Keyboard"
     Driver "kbd"
     Option "XkbRules" "xorg"
     Option "XkbModel" "pc104"
     Option "XkbLayout" "us"
EndSection

Section "InputDevice"
     Identifier "Mouse"
     Driver "mouse"
     Option "Protocol" "ImPS/2"
     #Option "Buttons" "7"
     Option "ZAxisMapping" "4 5"
     Option "Device" "/dev/input/mice"
EndSection

Section "Monitor"
     Identifier "Monitor"
     Option "DPMS"
EndSection

Section "Device"
     Identifier "Device"
     Driver "fglrx"
     Option "UseInternalAGPGART" "yes"
     Option "TVFormat" "NTSC-M"
     Option "TVStandard" "VIDEO"
     Option "DesktopSetup" "clone"
     Option "VideoOverlay" "on"
     Option "OpenGLOverlay" "off"
     Option "OverlayOnCRTC2"
EndSection

Section "Screen"
     Identifier "Screen"
     Device "Device"
     Monitor "Monitor"
     DefaultDepth 24

Subsection "Display"
     Depth 24
     Modes "1600x1200" "1280x1024" "1280x768" "1024x768" "800x600" "640x480"
EndSubsection

EndSection

Section "ServerLayout"
     Identifier "ServerLayout"
     Screen "Screen"
     InputDevice "Mouse" "CorePointer"
     InputDevice "Keyboard" "CoreKeyboard"
EndSection

-----------------------------------

I tried changing the "Option "DesktopSetup" "clone"" part to "horizontal" and "0x00000200", but those both break the X server. I've tried creating a new xorg.conf from the fglrxconfig, and that breaks the X server. I just can't seem to figure this out. Help?

I have the log file available from my last broken X server available if necessary. It's rather large, so I won't post it right now.

---

### Post by sumadartson on 2005-09-16
Assuming you're trying to build what ATI refers to as a BigDesktop (sp?), I've posted my xorg.conf and some explanation for this setup in another thread [here](http://www.ubuntuforums.org/showthread.php?t=61666). This is a rather limited setup though.

If this isn't what you're going for, than ignore this post and please forgive the shameless self-promotion.

---

