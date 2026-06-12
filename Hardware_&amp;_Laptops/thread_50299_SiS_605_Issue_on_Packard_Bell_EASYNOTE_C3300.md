---
title: "SiS 605 Issue on Packard Bell EASYNOTE C3300"
date: 2005-07-19
forum: Hardware &amp; Laptops
---

### Post by lprofil on 2005-07-19
Hi Folks,

first of all a big thank you to the overwhelming help i gain from kind people in the ubuntu-chat. Thank you very much!

I am currently setting up Ubuntu Hoary-Hedgehog 5.04 on a Packard Bell EASYNOTE C3300 for a friend of mine and have some graphic problems. 

The installation went quiet smoth. I am currently using the 2.6.11-1-686 kernel.
The screen resolution on the installation was set wrong first but lateron ok.
After i installed all necesary things like Opera, Firfox-Extension and so on, 
i tried to play a movie - but - nada. 

I couldn't get totem, mplayer or the realplayer to play a movie. Sound but no picture. That's why i would kindly ask you guys for some help.
Here is more specific info with my xorg.conf file:

```

<snip>
Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "vbe"
EndSection
<snap>

<snip>
Section "Device"
        Identifier      "Silicon Integrated Systems (SiS) 65x/M650/740 PCI/AGP VGA Display Adapter"
        Driver          "sis"
        BusID           "PCI:1:0:0"
        VideoRam        32768
EndSection
<snap>

<snip>
Section "Screen"
        Identifier      "Default Screen"
        Device          "Silicon Integrated Systems (SiS) 65x/M650/740 PCI/AGP VGA Display Adapter"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection
<snap>

```


I also tried Knoppix 3.9 which worked fine with the xine player there. 
But Knoppix is using XFree86 though.

And here is my questions:

The graphic card driver seems to have been choosen right as is says that it is using the:
Silicon integrated Systems (SiS)
SiS650 Chipset
 
[list]shall i reconfigure the xsever.xorg with another module for the
graphic card?[/list] 

[list]Is it possible to use the Knoppix xfree86 Configuration file for the xprg server?
[/list]

[list]Any other suggestions?[/list]

Maby it's some framebuffer issue as diskused on:
[http://ubuntuforums.org/archive/index.php/t-35449.html](http://ubuntuforums.org/archive/index.php/t-35449.html)

Anyway, i'll keep you posted
Desperate lprofil

ps:
Modem worked fine with the SmartLink Modem-Drivers i found on:
[http://ubuntuguide.org/](http://ubuntuguide.org/)
even if i would suggest to use the method described on the german:
[http://www.ubuntu-de.org/wiki/](http://www.ubuntu-de.org/wiki/)
because it's not dependent on the kernel version.

---

### Post by lprofil on 2005-07-19
Just tried a 
```
dpkg-reconfigure xserver-xorg
``` 
with framebuffer enabled - restarted the x-server 
but it's still not working.

Besides this is the XFree86 config file of Knoppix 3.9:

```

Section "Files"
        RgbPath      "/usr/X11R6/lib/X11/rgb"
        FontPath     "/usr/X11R6/lib/X11/fonts/misc:unscaled"
        FontPath     "/usr/X11R6/lib/X11/fonts/misc"
        FontPath     "/usr/X11R6/lib/X11/fonts/75dpi:unscaled"
        FontPath     "/usr/X11R6/lib/X11/fonts/75dpi"
        FontPath     "/usr/X11R6/lib/X11/fonts/100dpi:unscaled"
        FontPath     "/usr/X11R6/lib/X11/fonts/100dpi"
        FontPath     "/usr/X11R6/lib/X11/fonts/Speedo"
        FontPath     "/usr/X11R6/lib/X11/fonts/PEX"
# Additional fonts: Locale, Gimp, TTF...
        FontPath     "/usr/X11R6/lib/X11/fonts/cyrillic"
#        FontPath     "/usr/X11R6/lib/X11/fonts/latin2/75dpi"
#        FontPath     "/usr/X11R6/lib/X11/fonts/latin2/100dpi"
# True type and type1 fonts are also handled via xftlib, see /etc/X11/XftConfig!
        FontPath     "/usr/X11R6/lib/X11/fonts/Type1"
        FontPath     "/usr/share/fonts/ttf/western"
        FontPath     "/usr/share/fonts/ttf/decoratives"
        FontPath     "/usr/share/fonts/truetype"
        FontPath     "/usr/share/fonts/truetype/openoffice"
        FontPath     "/usr/share/fonts/truetype/ttf-bitstream-vera"
        FontPath     "/usr/share/fonts/latex-ttf-fonts"
        FontPath     "/usr/X11R6/lib/X11/fonts/defoma/CID"
        FontPath     "/usr/X11R6/lib/X11/fonts/defoma/TrueType"
EndSection

Section "ServerFlags"
EndSection

Section "Keyboard"
   Protocol    "Standard"
   AutoRepeat  500 5
   LeftAlt        Meta
   RightAlt        Meta
   ScrollLock      Compose
   RightCtl        Control
# This is just the default keymap for X.
# May be changed with the KDE international keyboard tool.
   XkbModel    "pc105"
   XkbLayout "de"
   XkbVariant  "nodeadkeys"
#   XkbOptions  "ctrl:swapcaps"
#   XkbKeycodes     "xfree86"
#   XkbTypes        "default"
#   XkbCompat       "default"
#   XkbSymbols      "us(pc101)"
#   XkbGeometry     "pc"
#   XkbRules        "xfree86"
#   XkbModel        "pc101"
#   XkbLayout "de"
EndSection

Section "Pointer"
    Protocol    "PS/2"
    Device      "/dev/mouse"
    Emulate3Buttons
    Emulate3Timeout    70
EndSection

# Auto-generated by mkxf86config

Section "Monitor"
        Identifier   "Monitor0"
#       HorizSync    28.0 - 78.0 # Warning: This may fry very old Monitors
        HorizSync    28.0 - 96.0 # Warning: This may fry old Monitors
        VertRefresh  50.0 - 75.0 # Very conservative. May flicker.
#       VertRefresh  50.0 - 62.0 # Extreme conservative. Will flicker. TFT default.
        #  Default modes distilled from
        #      "VESA and Industry Standards and Guide for Computer Display Monitor
        #       Timing", version 1.0, revision 0.8, adopted September 17, 1998.
        #  $XFree86: xc/programs/Xserver/hw/xfree86/etc/vesamodes,v 1.4 1999/11/18 16:52:17 tsi Exp $
        # 640x350 @ 85Hz (VESA) hsync: 37.9kHz
        ModeLine "640x350"    31.5  640  672  736  832    350  382  385  445 +hsync -vsync
        # 640x400 @ 85Hz (VESA) hsync: 37.9kHz
        ModeLine "640x400"    31.5  640  672  736  832    400  401  404  445 -hsync 





snip/snap because this section would be way to long






Section "Device"
    Identifier    "My Video Card"
    VendorName    "Unknown"
    BoardName     "Unknown"
#     TextClockFreq  22.175
EndSection

Section "Device"
  Identifier    "fbdev"
  VendorName    "Unknown"
  BoardName     "Unknown"
EndSection


# Standard Server
Section "Screen"
    Driver      "svga"
    Device      "My Video Card"
    Monitor     "Monitor0"
    Subsection  "Display"
        Modes "1024x768" "800x600" "640x480"
        ViewPort 0 0
    EndSubsection
EndSection

# Accel. Server(s)
Section "Screen"
    Driver      "accel"
    Device      "My Video Card"
    Monitor     "Monitor0"
    Subsection  "Display"
        Modes "1024x768" "800x600" "640x480"
        ViewPort 0 0
    EndSubsection
EndSection

# Fallback
Section "Screen"


    Driver      "vga16"
    Device      "My Video Card"
    Monitor     "Monitor0"
    Subsection  "Display"
        Modes "1024x768" "800x600" "640x480"
    EndSubsection
EndSection

Section "Screen"
  Driver        "fbdev"
  Device        "fbdev"
  Monitor       "Monitor0"
  SubSection "Display"
    Depth       32
    Modes       "default"
  EndSubSection
  SubSection "Display"
    Depth       24
    Modes       "default"
  EndSubSection
  SubSection "Display"
    Depth       16
    Modes       "default"
  EndSubSection
  SubSection "Display"
    Depth       15
    Modes       "default"
  EndSubSection
  SubSection "Display"
    Depth       8
    Modes       "default"
  EndSubSection
EndSection

```

---

### Post by lprofil on 2005-07-19
I just found this helpfull site:

[http://www.x.org/X11R6.8.2/doc/sis.4.html](http://www.x.org/X11R6.8.2/doc/sis.4.html)

but what the heck does it tell me? 
Which are the essential information i need?

/lprofil

---

### Post by motionsiren on 2005-11-28
sounds to me like your xorg is calling up the wrong method to display the video.

I'va had the same problem you have. What it came down to, was telling the video playback application to use "x11" output, rather "xv" (or maybe it was vice-versa). 

Check mplayer's man for -vo= and look more into xorg. Im guessing you're answer is whithin there.

---

