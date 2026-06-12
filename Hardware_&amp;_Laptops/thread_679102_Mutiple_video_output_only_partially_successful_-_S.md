---
title: "Mutiple video output only partially successful - SO CLOSE!"
date: 2008-01-26
forum: Hardware &amp; Laptops
---

### Post by sindyr on 2008-01-26
I am running Ubuntu Gutsy on a Dell laptop 700m with I think an Intel i810 video chipset.  I have recently swapped from WinXP, and I would like to stay.  However, I used to be able to plug my Bedroom TV into my laptop via the S-Video port, and play DVD's and Web content into the TV.  My goal with Ubuntu is the same.

I found an xorg.conf file that seems to be getting me partway there.  I now have video on both my laptop screen and the TV screen.

Now for the bad.

I cannot seem to drag windows from one screen to the other.  The mouse moves between the screens, but won't go when I am dragging a window.

And even worse, the resolutions on *both* screens is wrong.

On the laptop, it should be 1280 x 800, but it doesn't seem to want to be anything other than 1024 x 768.

Worse yet, the Ubuntu screen on the TV is not filling the screen - it's instead a smaller square inset in the TV tube about 3 inches on all sides.  If I had to guess, I would say that it is displaying 640 x 480 when it should be displaying 800 x 600.

So now I turn to you.  Below is my entire xorg.conf file.

This is pretty close - can anyone help figure out what mods are needed to bridge the final gap?

I think this S-Video thing, apart from Office 2007, is the final hurdle to me being in Ubuntu for the long haul...

Thanks.

```
##############
# Xorg configuration created by system-config-display
# Modified for use with Dell Inspiron 700m and SuSE 9.2 by Juergen Lennefer 04-Apr-2005

Section "Files"
    Fontpath    "/usr/X11R6/lib/X11/fonts/misc:unscaled"
    Fontpath    "/usr/X11R6/lib/X11/fonts/local"
    Fontpath    "/usr/X11R6/lib/X11/fonts/75dpi:unscaled"
    Fontpath    "/usr/X11R6/lib/X11/fonts/100dpi:unscaled"
    Fontpath    "/usr/X11R6/lib/X11/fonts/Type1"
    Fontpath    "/usr/X11R6/lib/X11/fonts/URW"
    Fontpath    "/usr/X11R6/lib/X11/fonts/Speedo"
    Fontpath    "/usr/X11R6/lib/X11/fonts/PEX"
    Fontpath    "/usr/X11R6/lib/X11/fonts/cyrillic"
    Fontpath    "/usr/X11R6/lib/X11/fonts/latin2/misc:unscaled"
    Fontpath    "/usr/X11R6/lib/X11/fonts/latin2/75dpi:unscaled"
    Fontpath    "/usr/X11R6/lib/X11/fonts/latin2/100dpi:unscaled"
    Fontpath    "/usr/X11R6/lib/X11/fonts/latin2/Type1"
    Fontpath    "/usr/X11R6/lib/X11/fonts/latin7/75dpi:unscaled"
    Fontpath    "/usr/X11R6/lib/X11/fonts/baekmuk:unscaled"
    Fontpath    "/usr/X11R6/lib/X11/fonts/japanese:unscaled"
    Fontpath    "/usr/X11R6/lib/X11/fonts/kwintv"
    Fontpath    "/usr/X11R6/lib/X11/fonts/truetype"
    Fontpath    "/usr/X11R6/lib/X11/fonts/uni:unscaled"
    Fontpath    "/usr/X11R6/lib/X11/fonts/CID"
    Fontpath    "/usr/X11R6/lib/X11/fonts/ucs/misc:unscaled"
    Fontpath    "/usr/X11R6/lib/X11/fonts/ucs/75dpi:unscaled"
    Fontpath    "/usr/X11R6/lib/X11/fonts/ucs/100dpi:unscaled"
    Fontpath    "/usr/X11R6/lib/X11/fonts/hellas/misc:unscaled"
    Fontpath    "/usr/X11R6/lib/X11/fonts/hellas/75dpi:unscaled"
    Fontpath    "/usr/X11R6/lib/X11/fonts/hellas/100dpi:unscaled"
    Fontpath    "/usr/X11R6/lib/X11/fonts/hellas/Type1"
    Fontpath    "/usr/X11R6/lib/X11/fonts/misc/sgi:unscaled"
    Fontpath    "/usr/X11R6/lib/X11/fonts/xtest"
    Fontpath    "/opt/kde3/share/fonts"
    Inputdevices    "/dev/ttyS0"
    Inputdevices    "/dev/ttyS1"
    Inputdevices    "/dev/ttyS2"
    Inputdevices    "/dev/ttyS3"
    Inputdevices    "/dev/ttyS4"
    Inputdevices    "/dev/ttyS5"
    Inputdevices    "/dev/ttyS6"
    Inputdevices    "/dev/ttyS7"
    Inputdevices    "/dev/ttyS8"
    Inputdevices    "/dev/psaux"
    Inputdevices    "/dev/logibm"
    Inputdevices    "/dev/sunmouse"
    Inputdevices    "/dev/atibm"
    Inputdevices    "/dev/amigamouse"
    Inputdevices    "/dev/atarimouse"
    Inputdevices    "/dev/inportbm"
    Inputdevices    "/dev/gpmdata"
    Inputdevices    "/dev/mouse"
    Inputdevices    "/dev/usbmouse"
    Inputdevices    "/dev/adbmouse"
    Inputdevices    "/dev/input/mice"
    Inputdevices    "/dev/input/event0"
    Inputdevices    "/dev/pointer0"
    Inputdevices    "/dev/pointer1"
    Inputdevices    "/dev/pointer2"
    Inputdevices    "/dev/pointer3"
EndSection

Section "ServerFlags"
    #       Option          "DefaultServerLayout" "DefaultLayout"
    #       Option          "DefaultServerLayout" "MultiheadLayout"
    #       Option          "DefaultServerLayout" "BeamerLayout"
    Option        "DefaultServerLayout"    "TVLayout"
    Option        "AllowMouseOpenFail"
EndSection

Section "Module"
    Load        "extmod"
    Load        "fbdevhw"
    Load        "record"
    Load        "freetype"
    Load        "type1"
    Load        "glx"
    Load        "GLcore"
    Load        "v4l"
EndSection

#Section "Module"
#  Load         "freetype"
#  Load         "type1"
#  Load         "dbe"
#  Load         "glx"
#  Load         "extmod"
#  Load         "v4l"
#EndSection

###########

Section "InputDevice"
    Driver        "kbd"
    Identifier    "Keyboard0"
    Option        "Protocol"    "Standard"
    Option        "XkbLayout"    "us"
    Option        "XkbModel"    "pc104"
    Option        "XkbRules"    "xfree86"
EndSection

Section "InputDevice"
    Driver        "mouse"
    Identifier    "Mouse1"
    Option        "ButtonNumber"    "5"
    Option        "Device"    "/dev/mouse"
    Option        "Name"    "SynPS/2 Synaptics TouchPad"
    Option        "Protocol"    "imps/2"
    Option        "Vendor"    "Sysp"
    Option        "ZAxisMapping"    "4 5"
EndSection

Section "InputDevice"
    Driver        "mouse"
    Identifier    "Mouse3"
    Option        "Device"    "/dev/input/mice"
    Option        "InputFashion"    "Mouse"
    Option        "Name"    "USB-Mouse;IMPS/2"
    Option        "Protocol"    "imps/2"
    Option        "ZAxisMapping"    "4 5"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"    "/dev/psaux"
    Option        "Protocol"    "auto-dev"
    Option        "HorizEdgeScroll"    "0"
    Option        "SHMConfig"    "on"
EndSection

###########

Section "ServerLayout"
    Identifier    "DefaultLayout"
  screen 0 "Screen0" 0 0
    Inputdevice    "Keyboard0"    "CoreKeyboard"
    Inputdevice    "Mouse1"    "CorePointer"
    Inputdevice    "Mouse3"    "SendCoreEvents"
EndSection

Section "ServerLayout"
    Identifier    "MultiheadLayout"
  screen 0 "Screend0" rightof "Screend1"
  screen 1 "Screend1"
    Inputdevice    "Keyboard0"    "CoreKeyboard"
    Inputdevice    "Mouse1"    "CorePointer"
    Inputdevice    "Mouse3"    "SendCoreEvents"
    Option        "Xinerama"    "on"
    #       Option      "Clone" "on"
EndSection

Section "ServerLayout"
    Identifier    "BeamerLayout"
  screen 0 "Screend0" leftof "Beamer1"
  screen 1 "Beamer1"
    Inputdevice    "Keyboard0"    "CoreKeyboard"
    Inputdevice    "Mouse1"    "CorePointer"
    Inputdevice    "Mouse3"    "SendCoreEvents"
    Option        "Xinerama"    "on"
    #       Option         "Clone" "on"
EndSection

Section "ServerLayout"
    Identifier    "TVLayout"
  screen 0 "Screentvd0" leftof "TV1"
  screen 1 "TV1"
    Inputdevice    "Keyboard0"    "CoreKeyboard"
    Inputdevice    "Mouse1"    "CorePointer"
    Inputdevice    "Mouse3"    "SendCoreEvents"
    Inputdevice    "Synaptics Touchpad"
   
    #       Option      "Xinerama" "on"
    #       Option      "Clone" "on"
EndSection

###########

Section "Monitor"
    Identifier    "Monitor0"
    Vendorname    "Generic LCD Display"
    Modelname    "LCD Panel 1280x800"
    Horizsync    31.5-50.0
    Vertrefresh    56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
    Gamma    1.0
EndSection

Section "Monitor"
    Identifier    "Monitor1"
    Vendorname    "Plug 'n' Play"
    Modelname    "Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
    Gamma    1.0
EndSection

Section "Monitor"
    Identifier    "Monitor2"
    Vendorname    "--> Beamer"
    Modelname    "Beamer 1024x768"
    Horizsync    31.5    -    67.0
    Vertrefresh    50.0    -    65.0
    Option        "dpms"
EndSection

Section "Monitor"
    Identifier    "TVm1"
    Vendorname    "Monitor Vendor"
    Modelname    "TV"
    Option        "dpms"
EndSection

###########

Section "Device"
    Identifier    "Videocard0"
    Boardname    "i810"
    Busid        "PCI:0:2:0"
    Driver        "i810"
    Screen    0
EndSection

Section "Device"
    Identifier    "Videocardd0"
    Driver        "i810"
    Vendorname    "Intel"
    Boardname    "855 GM"
    Busid        "PCI:0:2:0"
    Screen    0
    Option        "MonitorLayout"    "CRT,LFP"
EndSection

Section "Device"
    Identifier    "Videocardd1"
    Boardname    "i810"
    Busid        "PCI:0:2:0"
    Driver        "i810"
    Screen    1
EndSection

Section "Device"
    Identifier    "Videocardtvd0"
    Driver        "i810"
    Vendorname    "Intel"
    Boardname    "855 GM"
    Busid        "PCI:0:2:0"
    Screen    0
    Option        "MonitorLayout"    "TV,LFP"
EndSection

Section "Device"
    Identifier    "Videocardtvd1"
    Driver        "i810"
    Vendorname    "Intel"
    Boardname    "855 GM"
    Busid        "PCI:0:2:0"
    Screen    1
    Option        "MonitorLayout"    "TV,LFP"
EndSection

###########

Section "Screen"
    Identifier    "Screen0"
    Device        "Videocard0"
    Monitor        "Monitor0"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Virtual    1280    800
        Modes        "1280x800@60"    "1280x720@60"    "1280x768@60"    "800x600@60"    "800x600@56"
    EndSubSection
EndSection

Section "Screen"
    Identifier    "Screend0"
    Device        "Videocardd0"
    Monitor        "Monitor0"
    Defaultdepth    24
    SubSection "Display"
        Viewport    0    0
        Depth    24
        Modes        "1280x800"    "1024x768"    "800x600"    "640x480"
        Virtual    1280    1024
    EndSubSection
EndSection

Section "Screen"
    Identifier    "Screend1"
    Device        "Videocardd1"
    Monitor        "Monitor1"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Virtual    640    480
        Modes        "640x480@60"
    EndSubSection
EndSection

Section "Screen"
    Identifier    "Beamer1"
    Device        "Videocardd1"
    Monitor        "Monitor1"
    Defaultdepth    24
    SubSection "Display"
        Viewport    0    0
        Depth    24
        Modes        "1024x768"    "800x600"    "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier    "Screentvd0"
    Device        "Videocardtvd0"
    Monitor        "Monitor0"
    Defaultdepth    24
    SubSection "Display"
        Viewport    0    0
        Depth    24
        Modes        "1280x800"    "1024x768"    "800x600"    "640x480"
        #        Virtual    1280    800
    EndSubSection
EndSection

Section "Screen"
    Identifier    "TV1"
    Device        "Videocardtvd1"
    Monitor        "TVm1"
    Defaultdepth    24
    SubSection "Display"
        Viewport    0    0
        Depth    24
    EndSubSection
EndSection

###########

Section "DRI"
    Group        "video"
    Mode    0660
EndSection

Section "Extensions"
EndSection
```

---

### Post by sindyr on 2008-01-26
Btw, *is* this the right forum for the question?  I am all antsy to get this solved, and just realized that if this is not even the right forum, I probably won't get any help...

---

### Post by sindyr on 2008-01-26
(This was posted to another forum, and since its was getting no action, I am moving it to this forum which may be the more accurate place to put it.  Thanks)

I am running Ubuntu Gutsy on a Dell laptop 700m with I think an Intel i810 video chipset.  I have recently swapped from WinXP, and I would like to stay.  However, I used to be able to plug my Bedroom TV into my laptop via the S-Video port, and play DVD's and Web content into the TV.  My goal with Ubuntu is the same.

I found an xorg.conf file that seems to be getting me partway there.  I now have video on both my laptop screen and the TV screen.

Now for the bad.

I cannot seem to drag windows from one screen to the other.  The mouse moves between the screens, but won't go when I am dragging a window.

And even worse, the resolutions on *both* screens is wrong.

On the laptop, it should be 1280 x 800, but it doesn't seem to want to be anything other than 1024 x 768.

Worse yet, the Ubuntu screen on the TV is not filling the screen - it's instead a smaller square inset in the TV tube about 3 inches on all sides.  If I had to guess, I would say that it is displaying 640 x 480 when it should be displaying 800 x 600.

So now I turn to you.  Below is my entire xorg.conf file.

This is pretty close - can anyone help figure out what mods are needed to bridge the final gap?

I think this S-Video thing, apart from Office 2007, is the final hurdle to me being in Ubuntu for the long haul...

Thanks.

```
##############
# Xorg configuration created by system-config-display
# Modified for use with Dell Inspiron 700m and SuSE 9.2 by Juergen Lennefer 04-Apr-2005

Section "Files"
    Fontpath    "/usr/X11R6/lib/X11/fonts/misc:unscaled"
    Fontpath    "/usr/X11R6/lib/X11/fonts/local"
    Fontpath    "/usr/X11R6/lib/X11/fonts/75dpi:unscaled"
    Fontpath    "/usr/X11R6/lib/X11/fonts/100dpi:unscaled"
    Fontpath    "/usr/X11R6/lib/X11/fonts/Type1"
    Fontpath    "/usr/X11R6/lib/X11/fonts/URW"
    Fontpath    "/usr/X11R6/lib/X11/fonts/Speedo"
    Fontpath    "/usr/X11R6/lib/X11/fonts/PEX"
    Fontpath    "/usr/X11R6/lib/X11/fonts/cyrillic"
    Fontpath    "/usr/X11R6/lib/X11/fonts/latin2/misc:unscaled"
    Fontpath    "/usr/X11R6/lib/X11/fonts/latin2/75dpi:unscaled"
    Fontpath    "/usr/X11R6/lib/X11/fonts/latin2/100dpi:unscaled"
    Fontpath    "/usr/X11R6/lib/X11/fonts/latin2/Type1"
    Fontpath    "/usr/X11R6/lib/X11/fonts/latin7/75dpi:unscaled"
    Fontpath    "/usr/X11R6/lib/X11/fonts/baekmuk:unscaled"
    Fontpath    "/usr/X11R6/lib/X11/fonts/japanese:unscaled"
    Fontpath    "/usr/X11R6/lib/X11/fonts/kwintv"
    Fontpath    "/usr/X11R6/lib/X11/fonts/truetype"
    Fontpath    "/usr/X11R6/lib/X11/fonts/uni:unscaled"
    Fontpath    "/usr/X11R6/lib/X11/fonts/CID"
    Fontpath    "/usr/X11R6/lib/X11/fonts/ucs/misc:unscaled"
    Fontpath    "/usr/X11R6/lib/X11/fonts/ucs/75dpi:unscaled"
    Fontpath    "/usr/X11R6/lib/X11/fonts/ucs/100dpi:unscaled"
    Fontpath    "/usr/X11R6/lib/X11/fonts/hellas/misc:unscaled"
    Fontpath    "/usr/X11R6/lib/X11/fonts/hellas/75dpi:unscaled"
    Fontpath    "/usr/X11R6/lib/X11/fonts/hellas/100dpi:unscaled"
    Fontpath    "/usr/X11R6/lib/X11/fonts/hellas/Type1"
    Fontpath    "/usr/X11R6/lib/X11/fonts/misc/sgi:unscaled"
    Fontpath    "/usr/X11R6/lib/X11/fonts/xtest"
    Fontpath    "/opt/kde3/share/fonts"
    Inputdevices    "/dev/ttyS0"
    Inputdevices    "/dev/ttyS1"
    Inputdevices    "/dev/ttyS2"
    Inputdevices    "/dev/ttyS3"
    Inputdevices    "/dev/ttyS4"
    Inputdevices    "/dev/ttyS5"
    Inputdevices    "/dev/ttyS6"
    Inputdevices    "/dev/ttyS7"
    Inputdevices    "/dev/ttyS8"
    Inputdevices    "/dev/psaux"
    Inputdevices    "/dev/logibm"
    Inputdevices    "/dev/sunmouse"
    Inputdevices    "/dev/atibm"
    Inputdevices    "/dev/amigamouse"
    Inputdevices    "/dev/atarimouse"
    Inputdevices    "/dev/inportbm"
    Inputdevices    "/dev/gpmdata"
    Inputdevices    "/dev/mouse"
    Inputdevices    "/dev/usbmouse"
    Inputdevices    "/dev/adbmouse"
    Inputdevices    "/dev/input/mice"
    Inputdevices    "/dev/input/event0"
    Inputdevices    "/dev/pointer0"
    Inputdevices    "/dev/pointer1"
    Inputdevices    "/dev/pointer2"
    Inputdevices    "/dev/pointer3"
EndSection

Section "ServerFlags"
    #       Option          "DefaultServerLayout" "DefaultLayout"
    #       Option          "DefaultServerLayout" "MultiheadLayout"
    #       Option          "DefaultServerLayout" "BeamerLayout"
    Option        "DefaultServerLayout"    "TVLayout"
    Option        "AllowMouseOpenFail"
EndSection

Section "Module"
    Load        "extmod"
    Load        "fbdevhw"
    Load        "record"
    Load        "freetype"
    Load        "type1"
    Load        "glx"
    Load        "GLcore"
    Load        "v4l"
EndSection

#Section "Module"
#  Load         "freetype"
#  Load         "type1"
#  Load         "dbe"
#  Load         "glx"
#  Load         "extmod"
#  Load         "v4l"
#EndSection

###########

Section "InputDevice"
    Driver        "kbd"
    Identifier    "Keyboard0"
    Option        "Protocol"    "Standard"
    Option        "XkbLayout"    "us"
    Option        "XkbModel"    "pc104"
    Option        "XkbRules"    "xfree86"
EndSection

Section "InputDevice"
    Driver        "mouse"
    Identifier    "Mouse1"
    Option        "ButtonNumber"    "5"
    Option        "Device"    "/dev/mouse"
    Option        "Name"    "SynPS/2 Synaptics TouchPad"
    Option        "Protocol"    "imps/2"
    Option        "Vendor"    "Sysp"
    Option        "ZAxisMapping"    "4 5"
EndSection

Section "InputDevice"
    Driver        "mouse"
    Identifier    "Mouse3"
    Option        "Device"    "/dev/input/mice"
    Option        "InputFashion"    "Mouse"
    Option        "Name"    "USB-Mouse;IMPS/2"
    Option        "Protocol"    "imps/2"
    Option        "ZAxisMapping"    "4 5"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"    "/dev/psaux"
    Option        "Protocol"    "auto-dev"
    Option        "HorizEdgeScroll"    "0"
    Option        "SHMConfig"    "on"
EndSection

###########

Section "ServerLayout"
    Identifier    "DefaultLayout"
  screen 0 "Screen0" 0 0
    Inputdevice    "Keyboard0"    "CoreKeyboard"
    Inputdevice    "Mouse1"    "CorePointer"
    Inputdevice    "Mouse3"    "SendCoreEvents"
EndSection

Section "ServerLayout"
    Identifier    "MultiheadLayout"
  screen 0 "Screend0" rightof "Screend1"
  screen 1 "Screend1"
    Inputdevice    "Keyboard0"    "CoreKeyboard"
    Inputdevice    "Mouse1"    "CorePointer"
    Inputdevice    "Mouse3"    "SendCoreEvents"
    Option        "Xinerama"    "on"
    #       Option      "Clone" "on"
EndSection

Section "ServerLayout"
    Identifier    "BeamerLayout"
  screen 0 "Screend0" leftof "Beamer1"
  screen 1 "Beamer1"
    Inputdevice    "Keyboard0"    "CoreKeyboard"
    Inputdevice    "Mouse1"    "CorePointer"
    Inputdevice    "Mouse3"    "SendCoreEvents"
    Option        "Xinerama"    "on"
    #       Option         "Clone" "on"
EndSection

Section "ServerLayout"
    Identifier    "TVLayout"
  screen 0 "Screentvd0" leftof "TV1"
  screen 1 "TV1"
    Inputdevice    "Keyboard0"    "CoreKeyboard"
    Inputdevice    "Mouse1"    "CorePointer"
    Inputdevice    "Mouse3"    "SendCoreEvents"
    Inputdevice    "Synaptics Touchpad"
   
    #       Option      "Xinerama" "on"
    #       Option      "Clone" "on"
EndSection

###########

Section "Monitor"
    Identifier    "Monitor0"
    Vendorname    "Generic LCD Display"
    Modelname    "LCD Panel 1280x800"
    Horizsync    31.5-50.0
    Vertrefresh    56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
    Gamma    1.0
EndSection

Section "Monitor"
    Identifier    "Monitor1"
    Vendorname    "Plug 'n' Play"
    Modelname    "Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
    Gamma    1.0
EndSection

Section "Monitor"
    Identifier    "Monitor2"
    Vendorname    "--> Beamer"
    Modelname    "Beamer 1024x768"
    Horizsync    31.5    -    67.0
    Vertrefresh    50.0    -    65.0
    Option        "dpms"
EndSection

Section "Monitor"
    Identifier    "TVm1"
    Vendorname    "Monitor Vendor"
    Modelname    "TV"
    Option        "dpms"
EndSection

###########

Section "Device"
    Identifier    "Videocard0"
    Boardname    "i810"
    Busid        "PCI:0:2:0"
    Driver        "i810"
    Screen    0
EndSection

Section "Device"
    Identifier    "Videocardd0"
    Driver        "i810"
    Vendorname    "Intel"
    Boardname    "855 GM"
    Busid        "PCI:0:2:0"
    Screen    0
    Option        "MonitorLayout"    "CRT,LFP"
EndSection

Section "Device"
    Identifier    "Videocardd1"
    Boardname    "i810"
    Busid        "PCI:0:2:0"
    Driver        "i810"
    Screen    1
EndSection

Section "Device"
    Identifier    "Videocardtvd0"
    Driver        "i810"
    Vendorname    "Intel"
    Boardname    "855 GM"
    Busid        "PCI:0:2:0"
    Screen    0
    Option        "MonitorLayout"    "TV,LFP"
EndSection

Section "Device"
    Identifier    "Videocardtvd1"
    Driver        "i810"
    Vendorname    "Intel"
    Boardname    "855 GM"
    Busid        "PCI:0:2:0"
    Screen    1
    Option        "MonitorLayout"    "TV,LFP"
EndSection

###########

Section "Screen"
    Identifier    "Screen0"
    Device        "Videocard0"
    Monitor        "Monitor0"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Virtual    1280    800
        Modes        "1280x800@60"    "1280x720@60"    "1280x768@60"    "800x600@60"    "800x600@56"
    EndSubSection
EndSection

Section "Screen"
    Identifier    "Screend0"
    Device        "Videocardd0"
    Monitor        "Monitor0"
    Defaultdepth    24
    SubSection "Display"
        Viewport    0    0
        Depth    24
        Modes        "1280x800"    "1024x768"    "800x600"    "640x480"
        Virtual    1280    1024
    EndSubSection
EndSection

Section "Screen"
    Identifier    "Screend1"
    Device        "Videocardd1"
    Monitor        "Monitor1"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Virtual    640    480
        Modes        "640x480@60"
    EndSubSection
EndSection

Section "Screen"
    Identifier    "Beamer1"
    Device        "Videocardd1"
    Monitor        "Monitor1"
    Defaultdepth    24
    SubSection "Display"
        Viewport    0    0
        Depth    24
        Modes        "1024x768"    "800x600"    "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier    "Screentvd0"
    Device        "Videocardtvd0"
    Monitor        "Monitor0"
    Defaultdepth    24
    SubSection "Display"
        Viewport    0    0
        Depth    24
        Modes        "1280x800"    "1024x768"    "800x600"    "640x480"
        #        Virtual    1280    800
    EndSubSection
EndSection

Section "Screen"
    Identifier    "TV1"
    Device        "Videocardtvd1"
    Monitor        "TVm1"
    Defaultdepth    24
    SubSection "Display"
        Viewport    0    0
        Depth    24
    EndSubSection
EndSection

###########

Section "DRI"
    Group        "video"
    Mode    0660
EndSection

Section "Extensions"
EndSection
```

---

### Post by CarpKing on 2008-01-27
It looks like you're using separate Xservers for the monitor and TV.  I think you need a way to tell your programs to start in the other Xserver.  From the command line, this means placing "DISPLAY=:<# of the display> before the command to start the program.  It looks like your TV is display 1 (I could be wrong; I'm not that experienced with xorg.conf) so for MPlayer it would be something like:

```
DISPLAY=:1 mplayer <path of video file>
```

However, it would be more convenient to run both screens on the same Xserver.  For that, you should restore your original xorg.conf and then look into Xrandr.  There are many threads on the subject here, but [this]("http://http://lilserenity.wordpress.com/2007/10/15/ecstatic-xrandr-12-means-decent-linux-screen-management-at-last/") should get you started.  You'll also want to install xvattr so you can set the video overlay to appear on the other screen.

---

### Post by sindyr on 2008-01-27
After at least ten plus hours of working on my Dell 700m laptop with fresh Ubuntu Gutsy and trying different edits of xorg.conf over and over and over again (at least 30 times making minor alterations)  I have discovered some things:

First, the xorg.conf that I swiped from the net (which allows dual monitor with the TV, but won't permit 1280x800 on the latop and the TV image is not filling screen) has:

    Section "Device"
        Identifier    "Videocardtvd0"
        Driver        "i810"
        Vendorname    "Intel"
        Boardname    "855 GM"
        Busid        "PCI:0:2:0"
        Screen    0
        Option        "MonitorLayout"    "TV,LFP"
    EndSection

whereas the original xorg.conf built by my install of Ubuntu that does allow me to have my full 1280x800 laptop screen (but no TV out yet) has:

    Section "device" #   
        Identifier    "device1"
        Boardname    "intel"
        Busid        "PCI:0:2:0"
        Driver        "intel"
        Screen    0
    EndSection

After running many different tweaks of both, I have discovered that the key difference is that the web-swiped dual monitor conf file is using a device driver "i810" whereas the Ubuntu installed device driver is "intel".  Did a little research and it turns out that "i810" is an old driver that is no longer used in linux, and is replaced by the "intel" one.  So that seems to solve the mystery of why the web-swiped dual monitor conf file never gave me the full resolution of my laptop screen - apparently because it can't - whereas the newer "intel" driver can and does.

This makes me think that I need to use the "intel" driver, because if I don't I won't get my full 1280x800.  However, when I took the web-swiped dual monitor conf file and replaced the instances of "i810" with "intel", X wouldn't even boot.  I had to go into recovery mode and use pico to revert the changes.

So at this juncture it would seem that I do need to use the "intel" driver, or I won't be able to get my full desktop resolution.  The web-swiped dual monitor conf file is apparently incompatible with that driver, so I will have to start from scratch trying to figure out how to enable the S-video port while still using the "intel" device driver.

I am including my working single monitor xorg.conf - although I have also read confusing things about randr, xinerama, and other non xorg.conf methods for attacking this issue.  Not sure what is the right approach, I just want to have 1280x800 resolution on my laptop screen, 800x600 resolution (or whatever full screen is) on my TV via my S-Video out, and the ability to move windows back and forth between the two in order to enjoy both web content and media files on my TV.

So, now what? 

-Benn Grant

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc104"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"    "/dev/input/mice"
    Option        "Protocol"    "ImPS/2"
    Option        "ZAxisMapping"    "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"    "/dev/psaux"
    Option        "Protocol"    "auto-dev"
    Option        "HorizEdgeScroll"    "0"
    Option        "SHMConfig"    "on"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "stylus"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "eraser"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "cursor"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
  screen 0 "screen1" 0 0
    Inputdevice    "Generic Keyboard"
    Inputdevice    "Configured Mouse"
   
    # Uncomment if you have a wacom tablet
    #    InputDevice     "stylus"    "SendCoreEvents"
    #    InputDevice     "cursor"    "SendCoreEvents"
    #    InputDevice     "eraser"    "SendCoreEvents"
    Inputdevice    "Synaptics Touchpad"
EndSection

Section "Module"
    Load        "glx"
    Load        "GLcore"
    Load        "v4l"
EndSection

Section "device" #   
    Identifier    "device1"
    Boardname    "intel"
    Busid        "PCI:0:2:0"
    Driver        "intel"
    Screen    0
EndSection

Section "screen" #   
    Identifier    "screen1"
    Device        "device1"
    Defaultdepth    24
    Monitor        "monitor1"
    SubSection "Display"
        Depth    24
        Virtual    1280    1024
        Modes        "1280x1024@60"    "1280x960@60"    "1024x768@60"    "800x600@60"    "800x600@56"    "640x480@60"
    EndSubSection
EndSection

Section "monitor" #   
    Identifier    "monitor1"
    Vendorname    "Generic LCD Display"
    Modelname    "LCD Panel 1280x1024"
    Horizsync    31.5-64.0
    Vertrefresh    56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    Gamma    1.0
EndSection

Section "ServerFlags"
EndSection
```

---

### Post by sindyr on 2008-01-27
After at least ten plus hours of working on my Dell 700m laptop with fresh Ubuntu Gutsy and trying different edits of xorg.conf over and over and over again (at least 30 times making minor alterations)  I have discovered some things:

First, the xorg.conf that I swiped from the net (which allows dual monitor with the TV, but won't permit 1280x800 on the latop and the TV image is not filling screen) has:

    Section "Device"
        Identifier    "Videocardtvd0"
        Driver        "i810"
        Vendorname    "Intel"
        Boardname    "855 GM"
        Busid        "PCI:0:2:0"
        Screen    0
        Option        "MonitorLayout"    "TV,LFP"
    EndSection

whereas the original xorg.conf built by my install of Ubuntu that does allow me to have my full 1280x800 laptop screen (but no TV out yet) has:

    Section "device" #   
        Identifier    "device1"
        Boardname    "intel"
        Busid        "PCI:0:2:0"
        Driver        "intel"
        Screen    0
    EndSection

After running many different tweaks of both, I have discovered that the key difference is that the web-swiped dual monitor conf file is using a device driver "i810" whereas the Ubuntu installed device driver is "intel".  Did a little research and it turns out that "i810" is an old driver that is no longer used in linux, and is replaced by the "intel" one.  So that seems to solve the mystery of why the web-swiped dual monitor conf file never gave me the full resolution of my laptop screen - apparently because it can't - whereas the newer "intel" driver can and does.

This makes me think that I need to use the "intel" driver, because if I don't I won't get my full 1280x800.  However, when I took the web-swiped dual monitor conf file and replaced the instances of "i810" with "intel", X wouldn't even boot.  I had to go into recovery mode and use pico to revert the changes.

So at this juncture it would seem that I do need to use the "intel" driver, or I won't be able to get my full desktop resolution.  The web-swiped dual monitor conf file is apparently incompatible with that driver, so I will have to start from scratch trying to figure out how to enable the S-video port while still using the "intel" device driver.

I am including my working single monitor xorg.conf - although I have also read confusing things about randr, xinerama, and other non xorg.conf methods for attacking this issue.  Not sure what is the right approach, I just want to have 1280x800 resolution on my laptop screen, 800x600 resolution (or whatever full screen is) on my TV via my S-Video out, and the ability to move windows back and forth between the two in order to enjoy both web content and media files on my TV.

So, now what? 

-Benn Grant

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc104"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"    "/dev/input/mice"
    Option        "Protocol"    "ImPS/2"
    Option        "ZAxisMapping"    "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"    "/dev/psaux"
    Option        "Protocol"    "auto-dev"
    Option        "HorizEdgeScroll"    "0"
    Option        "SHMConfig"    "on"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "stylus"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "eraser"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "cursor"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
  screen 0 "screen1" 0 0
    Inputdevice    "Generic Keyboard"
    Inputdevice    "Configured Mouse"
   
    # Uncomment if you have a wacom tablet
    #    InputDevice     "stylus"    "SendCoreEvents"
    #    InputDevice     "cursor"    "SendCoreEvents"
    #    InputDevice     "eraser"    "SendCoreEvents"
    Inputdevice    "Synaptics Touchpad"
EndSection

Section "Module"
    Load        "glx"
    Load        "GLcore"
    Load        "v4l"
EndSection

Section "device" #   
    Identifier    "device1"
    Boardname    "intel"
    Busid        "PCI:0:2:0"
    Driver        "intel"
    Screen    0
EndSection

Section "screen" #   
    Identifier    "screen1"
    Device        "device1"
    Defaultdepth    24
    Monitor        "monitor1"
    SubSection "Display"
        Depth    24
        Virtual    1280    1024
        Modes        "1280x1024@60"    "1280x960@60"    "1024x768@60"    "800x600@60"    "800x600@56"    "640x480@60"
    EndSubSection
EndSection

Section "monitor" #   
    Identifier    "monitor1"
    Vendorname    "Generic LCD Display"
    Modelname    "LCD Panel 1280x1024"
    Horizsync    31.5-64.0
    Vertrefresh    56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    Gamma    1.0
EndSection

Section "ServerFlags"
EndSection
```

---

### Post by sindyr on 2008-01-27
OK, after 20 plus hours working on this issue, I am going to vastly simplify my goals.  You see, I figure that all I really need is to watch video from my laptop on my TV.  Whenever I am not doing that, I can swap back to my functional single head xorg.conf that works fine for that.  Now here is the new goal, hopefully simplified enough that someone can help me out.  Don't make me go back to Windows people! ;p

New Goal:  Have S-Video Out/TV show a Duplicate/Clone of what is on the laptop screen.

I don't care what resolution (though 800x600 as a low limit would be nice), I just want the LCD screen and the TV screen to be showing the same thing.  Obviously, since my 700m LCD is widescreen (1280x800) and the TV is an old 27# 3:4, one of the two will be distorted - the laptop screen being distorted is fine.

Since I no longer care about the specific resolutions, this means I can go back to using the "i810" driver instead of the "intel" driver that I never got S-Video working at ALL under.

However, the BIG thing is I need the image on the TV screen to fill the screen and not just the center of it.  Also, when I go into the System/Administration/Screens and Graphics control panel, the 2nd is listed at Plug 'n' Play at 640x480, and it will not let me choose a different resolution.

Right now, I have a NON cloned image that does NOT fill the screen, using the following xorg.conf.

HELP! I have read scores of threads on these forums and others, and have tried countless xorg.conf files that were written for other people.  What I need is suggestions of specifically what to try, or specific edits I should make to my configuration, tailored to the hardware, OS, and needs I have.

Please help save me from Windows - the OS that I will be forced to fully return to if I can't get the S-Video to work in linux..  Help me stay in this new wonderful OS experience.

```
##############
# Xorg configuration created by system-config-display
# Modified for use with Dell Inspiron 700m and SuSE 9.2 by Juergen Lennefer 04-Apr-2005

Section "Files"
EndSection

Section "ServerFlags"
	Option		"AllowMouseOpenFail"
#	Option		"Xinerama"	"true"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection

###########

Section "InputDevice"
	Driver		"kbd"
	Identifier	"Keyboard0"
	Option		"Protocol"	"Standard"
	Option		"XkbLayout"	"us"
	Option		"XkbModel"	"pc104"
	Option		"XkbRules"	"xfree86"
EndSection

Section "InputDevice"
	Driver		"mouse"
	Identifier	"Mouse1"
	Option		"ButtonNumber"	"5"
	Option		"Device"	"/dev/mouse"
	Option		"Name"	"SynPS/2 Synaptics TouchPad"
	Option		"Protocol"	"imps/2"
	Option		"Vendor"	"Sysp"
	Option		"ZAxisMapping"	"4 5"
EndSection

Section "InputDevice"
	Driver		"mouse"
	Identifier	"Mouse3"
	Option		"Device"	"/dev/input/mice"
	Option		"InputFashion"	"Mouse"
	Option		"Name"	"USB-Mouse;IMPS/2"
	Option		"Protocol"	"imps/2"
	Option		"ZAxisMapping"	"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option		"SHMConfig"	"on"
EndSection

###########

Section "ServerLayout"
	Identifier	"DefaultLayout"
   screen 0 "Screentvd0" leftof "TV1"
   screen 1 "TV1"
	Inputdevice	"Keyboard0"	"CoreKeyboard"
	Inputdevice	"Mouse1"	"CorePointer"
	Inputdevice	"Mouse3"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
	
#	Option		"Xinerama"	"on"
#       Option      "Clone" "on"
EndSection

###########

Section "Monitor"
	Identifier	"Monitor0"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x1024"
	Horizsync	31.5-64.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	Gamma	1.0
EndSection

#Section "Monitor"
#	Identifier	"TVm1"
#	Vendorname	"Monitor Vendor"
#	Modelname	"TV"
	#	HorizSync	30-50
	#	VertRefresh	60
	#	Option		"dpms"
#EndSection

Section "Monitor"
    Identifier     "TVm1" #TV
    VendorName     "Plug 'n' Play"
    ModelName      "Plug 'n' Play"
    HorizSync       30 - 50
    VertRefresh     50 - 60
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
EndSection


###########

Section "Device"
	Identifier	"Videocardtvd0"
#	Driver		"intel"
	Driver		"i810"
	Vendorname	"Intel"
	Boardname	"855 GM"
	Busid		"PCI:0:2:0"
	Screen	0
	Option		"MonitorLayout"	"TV,LFP"
EndSection

Section "Device"
	Identifier	"Videocardtvd1"
	Driver		"i810"
	Vendorname	"Intel"
	Boardname	"855 GM"
	Busid		"PCI:0:2:0"
	Screen	1
	Option		"MonitorLayout"	"TV,LFP"
EndSection

###########

Section "Screen"
	Identifier	"Screentvd0"
	Device		"Videocardtvd0"
	Monitor		"Monitor0"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	1024
		Modes		"1280x1024@60"	"1280x960@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

#Section "Screen"
#	Identifier	"TV1"
#	Device		"Videocardtvd1"
#	Monitor		"TVm1"
#	Defaultdepth	24
#	SubSection "Display"
#		Viewport	0	0
#		Depth	24
#	EndSubSection
#EndSection

Section "Screen" 
   Identifier      "TV1"
   Device          "Videocardtvd1"  
   Monitor         "TVm1" 
   DefaultDepth     24 
   SubSection      "Display" 
         Depth      24 
         Modes     "640x480@60" 
   EndSubSection    
EndSection

###########

Section "DRI"
	Group		"video"
	Mode	0660
EndSection

Section "Extensions"
EndSection
```

---

### Post by sindyr on 2008-01-27
Update: I still have not found any success.  Apparently I am stumping everyone from Newbies like myself to all the Pros on these boards.

How do you get the TV out on an intel based Dell 700m to clone what's on the laptop screen?

---

### Post by CarpKing on 2008-01-27
This sort of thing can be frustrating.  I apologize if this is a stupid question, but did your laptop work fine with a single display before you made any changes to xorg.conf?  Whatever driver it used then is probably the best one to try with, though I admit I don't know much about Intel drivers.  What I would recommend is that you restore your xorg.conf to how you had it before you tried any of this, and then try messing with Xrandr.  Using it you should be able to set the screens side by side or cloned.  You could also make a script that would switch between two screens and one.  That way you wouldn't have to worry about rebooting and having X not work.  Also, I wouldn't trust the "Screens and Graphics" control panel if I were you.  If it works, fine, but it has never worked for me and it sounds like you're having trouble too.

---

### Post by sindyr on 2008-01-27
> **CarpKing said:**
> This sort of thing can be frustrating.  I apologize if this is a stupid question, but did your laptop work fine with a single display before you made any changes to xorg.conf? 

Both the "i810" and the "intel" driver worked for my main LCD screen, however only the "intel" driver seems to get my full screen resolution of 1280x800.

 > Whatever driver it used then is probably the best one to try with, though I admit I don't know much about Intel drivers.  What I would recommend is that you restore your xorg.conf to how you had it before you tried any of this, and then try messing with Xrandr.

I did this.  I tried following your directions at:
[http://ubuntuforums.org/showthread.php?p=4214467](http://ubuntuforums.org/showthread.php?p=4214467)
but errorred out when I used the command "xrandr --addmode S-video 800x600" it replied "Cannot find output "S-Video"".  I got that error even when I switched "S-Video" to "TV" which the Intel drivers seem to prefer.

I also tried to follow the directions here:
[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)
but upon getting to step 4.1 "xrandr -q", there were NO TV or S-Video, where it should have at least said "TV Disconnected" like in the example.

So what do I do now on that front?

>  Also, I wouldn't trust the "Screens and Graphics" control panel if I were you.  If it works, fine, but it has never worked for me and it sounds like you're having trouble too.

Agreed.

The interesting thing is that almost every thing I have tried to get this to work has produced zero result - that it, crashes X-WIndows and forces me to go to the terminal at Alt-F1 to use pico to reset or fix the xorg.conf.

However, one single xorg.conf gives me very limited success.  With this one xorg.cong, I *do* get a screen both on my laptop and my TV.  However, the TV image is much smaller than the TV screen (although the image is a good and accurate one) - if I could somehow expand the image maybe we would be partway to a solution.

Here is the partway solution xorg.conf below.  However, starting fresh may be better.

I am willing to follow any course of action, so long as it accomplishes the base need, which is to watch stuff on my TV from my laptop.  Otherwise it's gonna have to be bye-bye Ubuntu and linux, hello again to Windows XP, because this is a major use of my laptop.

And I was really digging linux.

So, what specifically do I try next?

---

### Post by sindyr on 2008-01-28
Monday morning, checking in, but alas, no new suggestions.  Will check back in again shortly.

---

### Post by sindyr on 2008-01-28
Still no ideas?  I am pretty much stymied until I get some new ideas and suggestions.  Be back later.

Save me from Windows!  (grin)

---

### Post by motin on 2008-01-29
Use my set of X configuration files on [http://ubuntuforums.org/showthread.php?p=4211618#post4211618](http://ubuntuforums.org/showthread.php?p=4211618#post4211618) optionally along with the GUI switch tool and/or the All purpose RandR based configuration. 

This should solve all your problems. 

Cheers!

---

### Post by sindyr on 2008-01-30
> HOWTO: Make use of RandR 1.2 - or the ability to stick with one X configuration and dynamically add or remove screens and change display setups dynamically

Basically if Gutsy is your first installation or you have run "dpkg-reconfigure xserver-xorg" using Gutsy - you will have a RandR 1.2 setup. Verify this by running "xrandr" in a terminal. If you get something like:

Code:

$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 2048 x 2048
VGA disconnected (normal left inverted right)
LVDS connected 1280x800+0+0 (normal left inverted right) 331mm x 207mm
   1280x800_60.00   60.0*+
   1280x800       60.0 +   60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV disconnected (normal left inverted right)

... then RandR 1.2 is active (it detects your output ports and whether or not there are screens attached).

This part of your link doesn't track - when I run xrandr is does NOT list TV disconnected at all.

In fact, I ran the series of steps here:
[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)

And at the step where it *SHOULD* have shown a TV output, it did not.

So what now?

Here is my current hypothesis:  The "i810" driver is a better match for the graphics chipset in my older 700m laptop in that it seems to partially allow video on the TV (see above xorg.con) - however, the video on the TV fills only half the screen.  The "intel" driver is newer and replaces the "i810" driver, but the "intel" driver does not seem to enable access on the TV out at all.

Long story short, I believe that the new driver won't work for S-Video out on my 3.5 year old machine, and the older driver never seemed to work well.

Long story even shorter, I am starting to believe that the S-Video out on the Intel 855GME/ICH4-M Chipset  (Dell 700m laptop) has never worked for anyone under Ubuntu/linux, and will never work.

Anyone disagree?

---

### Post by sindyr on 2008-01-30
Anyone?

---

### Post by motin on 2008-01-30
After 3 min of googling:

[http://www.thinkwiki.org/wiki/Intel_Extreme_Graphics_2](http://www.thinkwiki.org/wiki/Intel_Extreme_Graphics_2):
>   SVideo port

SVideo works with for example:

 Option    "MonitorLayout"  "NONE,TV"

in your Device section. However, no settings for clone mode has been found to work yet. 

So stick with your way of getting at least a second desktop on the TV - looks like your best option atm. 

Other choices include using a VGA cable instead (if possible), replace the TV with a monitor, change laptop / computer that connects with the TV etc.

---

### Post by sindyr on 2008-01-31
> **motin said:**
> After 3 min of googling:

[http://www.thinkwiki.org/wiki/Intel_Extreme_Graphics_2](http://www.thinkwiki.org/wiki/Intel_Extreme_Graphics_2):


So stick with your way of getting at least a second desktop on the TV - looks like your best option atm. 

Other choices include using a VGA cable instead (if possible), replace the TV with a monitor, change laptop / computer that connects with the TV etc.

I too had done the same googling, and I would be HAPPY to stick with the "i810" driver.  However, currently when I display on the TV, the desktop fills only half the screen in an inset square in the middle of the TV.  This is obviously unnacceptable, so since you recommended I continue using this driver, do you have specific suggestions that I haven't tried to fix this issue?

Replacing the TV with a monitor is avoiding the problem, not solving it - and I don't think my wife would take kindly to the disappearance of our bedroom TV and being unable to watch our tivo.

Your advice that I "change the laptop/computer" that connects to the TV sounds great - if you can provide the $1000+ for a new laptop.  Otherwise, the "fix your problem by buying entirely new hardware" approach will have to wait until someday I have the money.  Especially since my laptop is fully functional right now, so long as I stay in Windows.

So ultimately, it sounds like your advice is to forget about Ubuntu getting my S-video out to work on this laptop, and just stick with using Windows as my primary OS.

The ironic thing is that I came here because I figured of all places, this would be the one turning over *every* stone to find *some* way to save a fellow techie from Windows.

So I guess I am forced to come back to this:

So what now?

Here is my current hypothesis: The "i810" driver is a better match for the graphics chipset in my older 700m laptop in that it seems to partially allow video on the TV (see above xorg.con) - however, the video on the TV fills only half the screen. The "intel" driver is newer and replaces the "i810" driver, but the "intel" driver does not seem to enable access on the TV out at all.

Long story short, I believe that the new driver won't work for S-Video out on my 3.5 year old machine, and the older driver never seemed to work well.

Long story even shorter, I am starting to believe that the S-Video out on the Intel 855GME/ICH4-M Chipset (Dell 700m laptop) has never worked for anyone under Ubuntu/linux, and will never work.

Anyone disagree?

---

### Post by motin on 2008-01-31
> **sindyr said:**
> I too had done the same googling, and I would be HAPPY to stick with the "i810" driver.  However, currently when I display on the TV, the desktop fills only half the screen in an inset square in the middle of the TV.  This is obviously unnacceptable, so since you recommended I continue using this driver, do you have specific suggestions that I haven't tried to fix this issue?

I didn't mean to indicate that you hadn't done your research (you seem to have done a lot and thoroughly) - just that my reply was only based on a brief google-check. I'll rephrase myself next time. 

As for further suggestions - you ought to seek up other users using your specific laptop model to start with. Check [https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron700m](https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron700m) (and please do update if you find the time) for starters. 

Also, if you haven't already (and noone else had), you ought to report this missing possibility as a bug.  

My backbone tells me that since you have gotten a picture on the TV, there ought to be a way of setting the resolution correctly.

> **sindyr said:**
> Replacing the TV with a monitor is avoiding the problem, not solving it - and I don't think my wife would take kindly to the disappearance of our bedroom TV and being unable to watch our tivo.

True, but you can use for instance [LinuxMCE]("http://www.linuxmce.com"), mythtv or freevo and not even need the tivo. 

> **sindyr said:**
> 

Your advice that I "change the laptop/computer" that connects to the TV sounds great - if you can provide the $1000+ for a new laptop.  

A mere suggestion. Just like this one: If you find a cheap new or unused older 1ghz+ desktop computer that connects to the TV you can use it as a thin client in a LinuxMCE environment, using the laptop as the media Core. 

> **sindyr said:**
> Otherwise, the "fix your problem by buying entirely new hardware" approach will have to wait until someday I have the money.  Especially since my laptop is fully functional right now, so long as I stay in Windows.

So ultimately, it sounds like your advice is to forget about Ubuntu getting my S-video out to work on this laptop, and just stick with using Windows as my primary OS.

Unless you reckon that it is ok to hibernate and start Windows just for the times when you want to connect it to the TV. Then restart and resume from hibernation when you're done.

> **sindyr said:**
> The ironic thing is that I came here because I figured of all places, this would be the one turning over *every* stone to find *some* way to save a fellow techie from Windows.


At least I don't have anything against Windows. (I do have some strong reactions against Microsoft's marketing however - since they mostly base it on false information about other system as well as FUD). If {insert OS name here} suits you (it's strengths vs weaknesses ratio is better than others') then go with it for the time being. Just check the facts and try to make a long-term decision since it usually pays off.

> **sindyr said:**
> 
So I guess I am forced to come back to this:

So what now?

Here is my current hypothesis: The "i810" driver is a better match for the graphics chipset in my older 700m laptop in that it seems to partially allow video on the TV (see above xorg.con) - however, the video on the TV fills only half the screen. The "intel" driver is newer and replaces the "i810" driver, but the "intel" driver does not seem to enable access on the TV out at all.

Seems correct. "intel" is newer and does in nature support newer chipsets better than the older ones.

> **sindyr said:**
> Long story short, I believe that the new driver won't work for S-Video out on my 3.5 year old machine, and the older driver never seemed to work well.

The "i810" driver won't change - so if it doesn't work well then that's it. 
It is possible that the "intel" driver will support this chipset (or already does) - but not without a relevant feature request for starters.

> **sindyr said:**
> Long story even shorter, I am starting to believe that the S-Video out on the Intel 855GME/ICH4-M Chipset (Dell 700m laptop) has never worked for anyone under Ubuntu/linux, and will never work.

If you mean "work well" (you already stated that it works somewhat) - you could be right. Keep on searching and make sure to file those bug reports/feature requests - it is not so unusual that one ends up finding a solution on the way.

Good luck!

---

### Post by sindyr on 2008-02-01
First of all, I apologize if this seems disjointed - I hit "quote" but it's only quoting you, not my original stuff you were replying to.  Because of this apparent limitation of the forums, you may have to check the post above to make full sense of this one.

> **motin said:**
> I didn't mean to indicate that you hadn't done your research (you seem to have done a lot and thoroughly) - just that my reply was only based on a brief google-check. I'll rephrase myself next time. 
No worries.  I readily admit to getting a frustrated because with my short but deep exposure to Ubuntu, I kinda fell in love with it - and now it appears I may not be able to consumate that love.  (horrible imagery, yes? grin)
> As for further suggestions - you ought to seek up other users using your specific laptop model to start with. Check [https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron700m](https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron700m) (and please do update if you find the time) for starters. 
I went to that page, was confused as to what I should do next.  I went ahead and email one of the page's contact people with the info about this situation.  The other contact person left no way to reach him that I could figure out, just a blog link.
> Also, if you haven't already (and noone else had), you ought to report this missing possibility as a bug.
OK, Glad to.  How do I do that?
> My backbone tells me that since you have gotten a picture on the TV, there ought to be a way of setting the resolution correctly.
Of course, that was with the old deprecated "i810" driver, but my gut is saying the same thing.  Which is why I find it hard to completely give up.
> True, but you can use for instance [LinuxMCE]("http://www.linuxmce.com"), mythtv or freevo and not even need the tivo. 
Tivo is one of those products that I am committed to and invested in.  It's why I switched from Dish Network to DirecTV in the first place.  Now if they go down the tubes, or my DirecTivo breaks and is not replacable, I may have to consider it.  But that would be a HUGE project, what with figuring out how the device would control the satellite box and still get 2 channels simultaneously.
> A mere suggestion. Just like this one: If you find a cheap new or unused older 1ghz+ desktop computer that connects to the TV you can use it as a thin client in a LinuxMCE environment, using the laptop as the media Core. 
I am keeping my eyes open, but my requirements for the possible new device is pretty steep: I can't afford to buy a new laptop right now, or else I would solve my problem that way.  Since my finances are limited, I could perhaps put $300 into such a device.  Still, if I could find such a device, I would be very interested.  S-Video (and audio) out would be a must, of course.  Plus it would have to be super-quiet and not sound like a traditional PC.  I have been looking, but haven't yet found such a device yet.  Do you have any recommendations?
> Unless you reckon that it is ok to hibernate and start Windows just for the times when you want to connect it to the TV. Then restart and resume from hibernation when you're done.
I am an all-or-nothing kind of person.  Either I replace Windows with Ubuntu, or I stay with Windows.  Your idea would work, but would be a big hassle, because I connect my laptop to the TV every day, sometimes multiple times.
> At least I don't have anything against Windows. (I do have some strong reactions against Microsoft's marketing however - since they mostly base it on false information about other system as well as FUD). If {insert OS name here} suits you (it's strengths vs weaknesses ratio is better than others') then go with it for the time being. Just check the facts and try to make a long-term decision since it usually pays off.
Long term, when I have the money to replace this laptop which needs to be replaced anyways, I see myself getting a laptop that will be chosen for, among other things, full compatibility.  Actually, the more I think about it, the more the S-video requirement for ANY system, Windows, Ubuntu, or otherwise, is an annoyance.  A quiet fanless device attached to my TV would be perfect if I could find one that wasn't as much as a laptop to begin with.
> Seems correct. "intel" is newer and does in nature support newer chipsets better than the older ones.

The "i810" driver won't change - so if it doesn't work well then that's it. 
It is possible that the "intel" driver will support this chipset (or already does) - but not without a relevant feature request for starters.
I keep wondering that since I can *get* a good picture under "i810" that there must be some way to configure that picture to be *bigger* and fill the screen.  But in over 25 hours of trying xranrd, xinerama, and countless xorg.conf's, I haven't found any.
> If you mean "work well" (you already stated that it works somewhat) - you could be right. Keep on searching and make sure to file those bug reports/feature requests - it is not so unusual that one ends up finding a solution on the way.

Good luck!
Not sure how much luck I have left - I keep feeling it the end of the line.  If I can get some more information on how to file bug reports I would be happy to do so.

Thanks for the in-depth reply, and trying to help.

---

### Post by CarpKing on 2008-02-01
Have you tried commenting out all but the 800 x 600 modelines for your TV in xorg.conf?  maybe that would force it to use that resolution.  Another thing you might try is "sudo dpkg-reconfigure xserver-xorg," though I don't know if that can handle multiple monitors.  I actually don't think I've seen that command suggested in a long time, but it will probably still work (you'll go through a textmode process that in the end basically generates an xorg.conf).  

You might also want to check out the Xorg bugtracker ([https://bugs.freedesktop.org/buglist.cgi?quicksearch=intel+xorg](https://bugs.freedesktop.org/buglist.cgi?quicksearch=intel+xorg)).  This is where you would go to file a bug.  You could also contact their mailing list- [email]xorg@freedesktop.org[/email].  

I wish you luck.

EDIT: [https://bugs.freedesktop.org/buglist.cgi?quicksearch=s-video+intel](https://bugs.freedesktop.org/buglist.cgi?quicksearch=s-video+intel) has a few interesting ones, but I don't know if they apply to you.

EDIT #2: Stumbled across this: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/178505](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/178505).  Doesn't provide any new information, but might still be of interest.

---

### Post by motin on 2008-02-03
I guess you have tried this, but it seems that you have only a 640x468 modeline in the TV1 Screen Display section:

```
Section "Screen" 
   Identifier      "TV1"
   Device          "Videocardtvd1"  
   Monitor         "TVm1" 
   DefaultDepth     24 
   SubSection      "Display" 
         Depth      24 
         Modes     "640x480@60" 
   EndSubSection    
EndSection
```

Try to replace the 640x480 with 800x600@56 or 800x600@60 maybe?

Also, when X just doesn't start you vill be able to see the reason (prefixed with a (EE) for error) in /var/log/Xorg.[a number, usually 0].log). Attach the errors from that log here in order for us to be able to help you understand the problem.

Btw, check out the Linux MCE demonstrational video - Linux MCE supports connecting that cable box and watching multiple channels simultaneously. It will probably be some sort of project though - midsized at least.

I have a HP Vectra desktop model at 866mhz at home which should be very cheap (the model) and it happens to be surprisingly quiet. I will in time try it out as a Linux MCE client and report back how well it works - although it could take some time until I get to it... Maybe you could look into it yourself meanwhile if you happen to stumble over one. 

Good luck with the further investigation of your problem!

---

### Post by 655 on 2008-02-05
[SIZE=2]I am having essentially the same problem as the OP:
Intel 82852/855GM integrated graphics chipset, using the "intel" driver, trying to get S-video to RCA cable to pump a signal to a TV, but no luck.

Xrandr displays no info for TV or S-video output, and all commands just cause the screen to flicker momentarily.

I'd like to get some step-by-step help in fixing my xorg.conf and hopefully getting this working, but I don't want to hijack **sindyr's** thread.
So perhaps someone (**motin**?) could PM me or, if it's O.K., help me troubleshoot in this thread.

Needless to say, I have tried the general advice provided for the OP's problem, as it is my problem too, but it is not working; hence the desire for individualized help.

P.S. TV signal was working fine when I used [featherking's tutorial]("http://ubuntuforums.org/showthread.php?t=361124&highlight=switchmon"), but I upgraded to Gutsy to take advantage of xrandr 1.2 and not have to start a new X session.[/SIZE]

---

