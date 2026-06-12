---
title: "New ATI Drivers + Xv = New ATI Drivers"
date: 2007-12-16
forum: Hardware &amp; Laptops
---

### Post by Onimae on 2007-12-16
I just got the new ATI driver (Catalyst 7.11) and have been trying to get Xv to work again. I've done

```

sudo aticonfig --overlay-type=Xv

```

And it doesn't seem to make a difference. The output of fglrxinfo is

```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon X1200 Series
OpenGL version string: 2.1.7059 Release

```

and the output of xvinfo is:

```

X-Video Extension version 2.2
screen #0
 no adaptors present

```

Lastly, here is my Xorg.conf:

```

Section "ServerLayout"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
        Load  "glx"
        Load  "dri"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc101"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ImPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "HorizScrollDelta" "0"
        Option      "SHMConfig" "1"
EndSection

Section "InputDevice"
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "stylus"
        Option      "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier  "eraser"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "eraser"
        Option      "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier  "cursor"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "cursor"
        Option      "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "Extensions"
        Option      "XVideo" "enable"
EndSection

```

Anyone know what the problem is?

**Peter**

---

### Post by Onimae on 2007-12-18
Anyone know anything about this problem?

**Peter**

---

### Post by Onimae on 2007-12-18
Anybody...please? This is really bothersome.

**Peter**

---

### Post by moron on 2007-12-25
I have exactly the same issue.  It appears that the embedded X1200 series chipsets just do not support Xv at this time.  Not sure whether this will be a case of waiting or having to ditch ATI for Nvidia. . .

---

### Post by Onimae on 2007-12-25
Well, the problem was fixed with Catalyst 7.12. Unfortunately, there is very little widescreen support (namely, it won't work with the 1200 card and quite a few others, but does work with some). Plus if you try to use Compiz while using Xv, the Xv video will be all choppy and probably just do a whole lot of flickering. *shakes fist at ATI*.

**Peter**

---

### Post by moron on 2007-12-26
Do you have a link to anywhere that documents this?  I finally managed to ressurect my Xorg.conf to something that would work after installing the latest drivers but would like to have a better idea of what is and isn't supported by this card.  

For example, with the x1200 adding this:

Option            "VideoOverlay" "on"

causes the screen resolution to get messed up  - shifts the desktop partially out of the currently viewable screen area (no monitor adjusment seemed to be able to bring it back).  The screen was also a bit blurry and xvinfo was unable to find the adaptor but I didn't see any obvious errors reported.

Gotta say that if I wasn't quite so keen on reducing heat and saving space (love the quiet) I would be shopping for an Nvidia product right now.  

Cheers

---

### Post by Yellow Pasque on 2007-12-26
Just a quick aside: ATI/AMD is releasing the specs of the RS690/X12x0 this week, so the open-source community can have a go at writing some decent drivers for it. Rejoice!

---

### Post by moron on 2007-12-26
Ok, I realized what was going on with the odd off screen behaviour.  For whatever reason, the fglrx driver seems to periodically forget what mode to be in when it starts up and although xorg.conf is saying to show a widescreen resolution, the actual screen resolution being set to the monitor is 4x3 which causes scaling distortion (i.e. blurriness).  Looking at the status menu on the LCD monitor itself confirmed this.  Starting up amdccle showed the resolution as being correct (1680x1050) although this was *not* what the LCD monitor was actually reporting as receiving (it was getting 1280x1040).

BY changing the resolution in amdccle to something lower, applying it and then changing it back to the widescreen resolution the driver was reset and now my widescreen resolution is no longer messed up.

Hopefully I do not need to do this everytime I restart the machine.

And still no Xv support.

Cheers

---

### Post by novakyu on 2008-03-11
I just wanted to note, for those monitoring this thread, that the Xv support in X1200 series has been fixed in the March 5th release of the proprietary FGLRX driver. More information and download links are available at [https://groups.google.com/group/x1250/web/drivers4linux]("https://groups.google.com/group/x1250/web/drivers4linux").

So,  this bandage solution should work, at least until the open source driver (radeon or radeonhd) supports widescreen (maybe the latest version does, but what's included in Debian testing doesn't seem to).

---

