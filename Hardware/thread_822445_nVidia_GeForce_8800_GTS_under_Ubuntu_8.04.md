---
title: "nVidia GeForce 8800 GTS under Ubuntu 8.04?"
date: 2008-06-08
forum: Hardware
---

### Post by FabianoLinux on 2008-06-08
Does anyone have a nVidia GeForce 8800GTS and have it working under Ubuntu or any other 8000 or 9000 series graphics cards?

If you got it working, state if you did it manually from the nVidia website, used Envy, or Ubuntu automatically detected it with the restricted drivers manager.

If you did not get it working, state what you tried.

---

### Post by 16777216 on 2008-06-08
I have a GeForce 8600 GT that Ubuntu detected in a usable state, it then installed the binary "nvidia" driver into a usable statewhen I told it to, I then moved my hand tuned xorg.conf into place and have not had a problem since. 

I have a dual head setup, ubuntu never uses this correctaly.
They will be set into clone mode by default, as my computer is a desktop this is not the best soultion.

I also don't think Ubuntu can set up the binary nVidia driver to use twinview on it's own.
So when the binary driver installs I get clone mode or just one monitor is used.

That is part of the reason I use a hand tuned xorg.conf which I will paste below. ( The other part is performance with a 3D desktop  and games. )

It seems that some thing has edted my xorg.conf but all of my changes are still there. 
I will probaly edit it back to how I like it and add comments for ease of edting by others since I post it alot.

```
Section "Screen"
    Identifier    "Screen0"
    Device        "Videocard0"
    Monitor        "Monitor0"
    Option        "metamodes"    "CRT-0: 1152x864_85 +0+0, CRT-1: 1152x864_75 +1152+0; CRT-0: 1024x768 +0+0, CRT-1: nvidia-auto-select +1024+0; CRT-0: 800x600 +0+0, CRT-1: nvidia-auto-select +800+0; CRT-0: 640x480 +0+0, CRT-1: nvidia-auto-select +640+0; CRT-0: 1024x768 +0+0, CRT-1: null"
    Option        "AddARGBGLXVisuals"    "True"
    SubSection "Display"
        Depth    24
        Modes        "640x480@60"    "640x480@72"    "640x480@75"    "640x480@85"    "800x600@56"    "800x600@72"    "800x600@75"    "800x600@85"    "800x600@60"    "832x624@75"    "1024x768@85"    "1024x768@75"    "1024x768@70"    "1024x768@60"    "1024x768@43"    "1152x864@75"    "1280x1024@75"    "1280x960@60"    "1280x960@85"    "1280x1024@85"    "1280x1024@60"    "1280x960@75"    "1400x1050@60"    "1400x1050@75"    "1600x1200@65"    "1600x1200@60"    "1600x1200@75"    "1600x1200@70"    "1792x1344@60"    "1856x1392@60"    "1920x1440@60"    "2048x1536@60"
    EndSubSection
    Defaultdepth    24
EndSection

Section "Device"
    Vendorname    "NVIDIA Corporation"
    Boardname    "GeForce 8600 GT"
    Identifier    "Videocard0"
    Driver        "nvidia"
    Option        "Coolbits"    "1"
    Option        "TwinView"    "1"
    Option        "TwinViewOrientation"    "RightOf"
    Option        "TwinViewXineramaInfoOrder"    "CRT-0"
    Option        "NoLogo"    "1"
    Option        "RenderAccel"    "1"
    Option        "HWCursor"    "1"
    Option        "AllowGLXWithComposite"    "1"
    Option        "RandRRotation"    "1"
    Option        "AllowDDCCI"    "1"
    Option        "AIGLX"    "1"
    Option        "DamageEvents"    "1"
    Option        "UseEvents"    "1"
    Option        "TripleBuffer"    "1"
EndSection

Section "InputDevice"
    Identifier    "Mouse0"
    Driver        "mouse"
    Option        "Protocol"    "auto"
    Option        "Device"    "/dev/psaux"
    Option        "Emulate3Buttons"    "no"
    Option        "ZAxisMapping"    "4 5"
EndSection

Section "InputDevice"
    Identifier    "Keyboard0"
    Driver        "kbd"
EndSection

Section "ServerLayout"
    Identifier    "Layout0"
  screen "Screen0"
    Inputdevice    "Keyboard0"    "CoreKeyboard"
    Inputdevice    "Mouse0"    "CorePointer"
EndSection

Section "Module"
    Load        "dbe"
    Load        "extmod"
    Load        "type1"
    Load        "freetype"
    Load        "glx"
    Load        "v4l"
EndSection

Section "Monitor"
    Vendorname    "Dell Computer Manufacturing Inc."
    Modelname    "DELL M991"
    Identifier    "Monitor0"
    Horizsync    30.0    -    96.0
    Vertrefresh    50.0    -    160.0
    Option        "DPMS"
EndSection

Section "ServerFlags"
    Option        "Xinerama"    "0"
EndSection

Section "Extensions"
    Option        "DAMAGE"    "Enable"
    Option        "RENDER"    "Enable"
    Option        "Composite"    "Enable"
EndSection

Section "Files"
    Rgbpath        "/usr/X11R6/lib/X11/rgb"
EndSection

```I will re post it when I have finished edting it.

Ok here is the edited one. 
```

## START ##

Section "Files"
    Rgbpath        "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load        "dbe"
    Load        "extmod"
    Load        "type1"
    Load        "freetype"
    Load        "glx"
    Load        "v4l"
EndSection

Section "ServerLayout"
    Identifier    "Layout0"
    screen        "Screen0"
    Inputdevice    "Keyboard0"            "CoreKeyboard"
    Inputdevice    "Mouse0"            "CorePointer"
EndSection

Section "ServerFlags"
    Option        "Xinerama"            "0"
EndSection

Section "InputDevice"
    Identifier    "Keyboard0"
    Driver        "kbd"
EndSection

Section "InputDevice"
    Identifier    "Mouse0"
    Driver        "mouse"
    Option        "Protocol"            "auto"
    Option        "Device"            "/dev/psaux"
    Option        "Emulate3Buttons"        "no"
    Option        "ZAxisMapping"            "4 5"
EndSection

Section "Device"
    Vendorname    "NVIDIA Corporation"
    Boardname    "GeForce 8600 GT"
    Identifier    "Videocard0"
    Driver        "nvidia"
    Option        "Coolbits"            "1"  ## This is for over clocking ##
    Option        "TwinView"            "1"  ## This is for a multi monitor set up ##
    Option        "TwinViewOrientation"        "RightOf"  ## This is to tell twinview how your monitors are arranged ##
    Option        "TwinViewXineramaInfoOrder"    "CRT-0"  ## this is the main monitor to use when you have more than one ##
    Option        "NoLogo"            "1"  ## This removes the nVidia logo when X loads ##
    Option        "RenderAccel"            "1"  ## This turns on the 3D ##
    Option        "HWCursor"            "1"  ## This makes the videocard draw the mouse directly ##
    Option        "AllowGLXWithComposite"        "1"  ## This is for composite desktops ( Compiz and the like ) ##
    Option        "RandRRotation"            "1"  ## This is for rotating your screen to match what ever weird set up you have ;) ##
    Option        "AllowDDCCI"            "1"  ## This is for power management ##
    Option        "AIGLX"                "1"  ## Again for Compiz and such ##
    Option        "DamageEvents"            "1"  
    Option        "UseEvents"            "1"
    Option        "TripleBuffer"            "1"
    Option        "AddARGBGLXVisuals"        "1"  ## Again for Compiz and such ##
EndSection

Section "Extensions"
    Option        "DAMAGE"            "Enable"
    Option        "RENDER"            "Enable"
    Option        "Composite"            "Enable"
EndSection

Section "Monitor"
    Vendorname    "Dell Computer Manufacturing Inc."
    Modelname    "DELL M991"
    Identifier    "Monitor0"
    Horizsync    30.0 - 96.0
    Vertrefresh    50.0 - 160.0
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Screen0"
    Device        "Videocard0"
    Monitor        "Monitor0"
    Option        "metamodes"            "CRT-0: 1152x864_85 +0+0, CRT-1: 1152x864_75 +1152+0; CRT-0: 1024x768 +0+0, CRT-1: nvidia-auto-select +1024+0; CRT-0: 800x600 +0+0, CRT-1: nvidia-auto-select +800+0; CRT-0: 640x480 +0+0, CRT-1: nvidia-auto-select +640+0; CRT-0: 1024x768 +0+0, CRT-1: null"

    SubSection "Display"
        Depth 24
        Modes                    "640x480@60" "640x480@72" "640x480@75" "640x480@85" "800x600@56" "800x600@72" "800x600@75" "800x600@85" "800x600@60" "832x624@75" "1024x768@85" "1024x768@75" "1024x768@70" "1024x768@60" "1024x768@43" "1152x864@75" "1280x1024@75" "1280x960@60" "1280x960@85" "1280x1024@85" "1280x1024@60" "1280x960@75" "1400x1050@60" "1400x1050@75" "1600x1200@65" "1600x1200@60" "1600x1200@75" "1600x1200@70" "1792x1344@60" "1856x1392@60" "1920x1440@60" "2048x1536@60"
    EndSubSection
    Defaultdepth 24
EndSection

## END ##
```

---

### Post by FabianoLinux on 2008-06-09
16777216, thanks,

But did ubuntu not say "you are now using a restricted driver" and automatically install the nvidia driver? Im just going to use a single standard 19" monitor. I was just hoping to know if I can get it to work with no effort at all.

---

### Post by 16777216 on 2008-06-09
Well you have to turn on the desktop effects or tell it to install the restricted drivers to get the nVidia binary drivers to install but yes you *should* not have any problems doing so. 

I would recomend using envyng to do this as it makes it easy to get the right driver for your hardware.

I can't remember if it is installed by default so if not copy/paste this in to a command line terminal. ```
sudo apt-get install envyng
```This will install it if it is not already, or tell you that it is, if it is.

Envy is quite simple to use, about the only thing you need to know is if your graphics are ATI or nVidia.

---

### Post by jrharvey on 2008-06-09
8500, 8600 and 8800 gt work automatically. Im not sure how GOOD the ubuntu drivers are but it works. I am not sure about 8800 GTS, GTX, Ultra or GTS (G92).

---

### Post by Octagonal on 2008-06-09
I have an 8800GTS in my box and it was detected just fine... I just had to click on the popup and select use restricted drivers for the video card--rebooted and everything worked perfectly.

---

### Post by SteveNorman on 2008-06-09
mine worked ok,,and I had to do what I posted here for someone else to get mine to work properly

[http://ubuntuforums.org/showthread.php?t=809654](http://ubuntuforums.org/showthread.php?t=809654)

wasnt to painful

---

### Post by FabianoLinux on 2008-06-11
Thanks everyone, that was really helpful!

I'm going to start building my new computer soon, so I wanted to choose a compatible video card.

I will also be sure to put entries in the compatibility list for all the hardware I buy, so others can benefit from it. Everyone else do the same:

[https://wiki.ubuntu.com/HardwareSupport/](https://wiki.ubuntu.com/HardwareSupport/)

[http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)

I will also create a new thread stating all my hardware and all my compatibility issues(hopefully none). It would be awesome if everyone did that, it took me forever to get the rest of my hardware chosen.

So far, I'm going with:
mobo:m2n-sli deluxe
gfx: 8800gt(eVGA) or gts(PNY 512)
ram: kingston 2gb 800mhz
hdr: 500gb seagate sata2
case:antec 900 case
ps:corsair 620W or OCZ gamextreme 600W
whatever dvd drive
cup: amd dual-core athlon either (2.9gh2)5600+ or (3.2ghz)6400+

What do you guys think of my hardware choices, is it balanced?

---

