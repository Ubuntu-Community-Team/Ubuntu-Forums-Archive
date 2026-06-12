---
title: "Dell 700m Multihead"
date: 2006-06-09
forum: Hardware &amp; Laptops
---

### Post by TheSoko on 2006-06-09
Soo Dapper has come and I still cannot figure out how to get multihead going. I still get the vm86 crash. I thought I had read somewhere that this was fixed in Dapper. Has anybody else had much luck?

Here's the showstopping xorg.conf that used to work in Gentoo on the same laptop...

```

Section "ServerFlags"
        Option          "DefaultServerLayout" "DefaultLayout"
#       Option          "DefaultServerLayout" "MultiheadLayout"
#       Option          "DefaultServerLayout" "TVLayout"
EndSection

Section "ServerLayout"
        Identifier "DefaultLayout"
        Screen "DL - Notebook" 0 0
        InputDevice    "Mouse1" "CorePointer"
        InputDevice    "Keyboard1" "CoreKeyboard"
EndSection

Section "ServerLayout"
        Identifier     "MultiheadLayout"
        Screen      0  "ML - Notebook" LeftOf "ML - Monitor"
        Screen      1  "ML - Monitor"
        InputDevice    "Mouse1" "CorePointer"
        InputDevice    "Keyboard1" "CoreKeyboard"
#       Option      "Xinerama" "on"
#       Option      "Clone" "on"
EndSection

Section "ServerLayout"
        Identifier     "TVLayout"
        Screen      0  "TL - Notebook" LeftOf "TL - TV"
        Screen      1  "TL - TV"
        InputDevice    "Mouse1" "CorePointer"
        InputDevice    "Keyboard1" "CoreKeyboard"
#       Option      "Xinerama" "on"
#       Option      "Clone" "on"
EndSection


Section "Files"
        RgbPath      "/usr/lib/X11/rgb"
        FontPath     "/usr/share/fonts/misc/"
        FontPath     "/usr/share/fonts/TTF/"
        FontPath     "/usr/share/fonts/Type1/"
        FontPath     "/usr/share/fonts/75dpi/"
        FontPath     "/usr/share/fonts/100dpi/"
        FontPath     "/usr/share/fonts/local/"
EndSection

Section "Module"
        Load  "dbe"     # Double buffer extension
        SubSection "extmod"
                Option      "omit xfree86-dga"   # don't initialise the DGA extension
        EndSubSection
        Load  "fbdevhw"
        Load  "glx"
        Load  "record"
        Load  "freetype"
        Load  "type1"
        Load  "dri"
EndSection

Section "InputDevice"
        Identifier  "Keyboard1"
        Driver      "keyboard"

        Option      "CoreKeyboard"
        Option      "XkbRules"   "xorg"
        Option      "XkbModel"   "pc105"
        Option      "XkbLayout"  "us"
EndSection

Section "InputDevice"
        Identifier  "Mouse1"
        Driver      "mouse"
        Option      "Protocol" "Auto"
        Option      "Device" "/dev/psaux"
        Option      "Emulate3Timeout" "50"
        Option      "ZAxisMapping" "4 5"
EndSection

########################
# Default Layout Stuff #
########################

Section "Device"
        Identifier "DL - Notebook Device"
        Driver "i810"
        VideoRam 65536
        Option "AGPFastWrite" "true"
        Option "MonitorLayout" "LFP"
        Option "ActiveDevice" "LCD"
        Option "AlowGLXWithComposite" "true"
EndSection

Section "Screen"
        Identifier "DL - Notebook"
        Device     "DL - Notebook Device"
        Monitor    "DL - Notebook Monitor"

        DefaultDepth 24
        Subsection "Display"
                Depth 24
                Modes "1280x800" "1024x768" "800x600"
                Viewport 0 0
        EndSubSection
EndSection

Section "Monitor"
        Identifier "DL - Notebook Monitor"
        Option "DPMS"
        Modeline "1280x800" 101.92 1280 1312 1696 1728 800 816 825 841
EndSection

##########################
# Multihead Layout Stuff #
##########################

Section "Screen"
        Identifier "ML - Notebook"
        Device     "ML - Notebook Device"
        Monitor    "DL - Notebook Monitor"

        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes    "1280x800" "1024x768" "800x600"
        EndSubSection
EndSection

Section "Screen"
        Identifier "ML - Monitor"
        Device     "ML - Monitor Device"
        Monitor    "ML - Monitor Monitor"

        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "Device"
        Identifier "ML - Notebook Device"
        Driver "i810"
        Option "AGPFastWrite" "true"
        Option "AlowGLXWithComposite" "true"

        BusID "PCI:0:2:0"
        Screen 0
        Option "MonitorLayout" "CRT,LFP"
EndSection

Section "Device"
        Identifier "ML - Monitor Device"
        Driver "i810"
        Option "AGPFastWrite" "true"
        Option "AlowGLXWithComposite" "true"

        BusID "PCI:0:2:0"
        Screen 1
        Option "MonitorLayout" "CRT,LFP"
EndSection

Section "Monitor"
        Identifier   "ML - Monitor Monitor"
        Option      "dpms"
EndSection


###################
# TV Layout Stuff #
###################

Section "Screen"
        Identifier      "TL - Notebook"
        Device          "TL - Notebook Device"
        Monitor         "DL - Notebook Monitor"

        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes    "1280x800" "1024x768" "800x600"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "TL - TV"
        Device          "TL - TV Device"
        Monitor         "TL - TV Monitor"

        DefaultDepth 24
        SubSection "Display"
                Viewport 0 0
                Depth 24
                Modes "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "Device"
        Identifier "TL - Notebook Device"
        Driver "i810"

        BusID "PCI:0:2:0"
        Screen 0
        Option "MonitorLayout" "TV,LFP"
EndSection

Section "Device"
        Identifier "TL - TV Device"
        Driver "i810"

        BusID "PCI:0:2:0"
        Screen 1
        Option "MonitorLayout" "TV,LFP"
EndSection

Section "Monitor"
        Identifier   "TL - TV Monitor"

        HorizSync 30 - 50
        VertRefresh 60

        Option      "dpms"
EndSection


Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

```

Xorg.0.log
```

(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(EE) I810(0): vm86() syscall generated signal 11.
(II) I810(0): EAX=0x0000ff01, EBX=0x000ff530, ECX=0x00003780, EDX=0x00200000
(II) I810(0): ESP=0x00005f49, EBP=0x00005f8d, ESI=0x00005f75, EDI=0x00000636
(II) I810(0): CS=0xf000, SS=0x0100, DS=0x0000, ES=0xffff, FS=0x0000, GS=0x0000
(II) I810(0): EIP=0x0000f517, EFLAGS=0x00033046
(II) I810(0): code at 0x000ff517:
 26 8a 26 10 00 38 e0 75 0d f6 16 00 00 26 8a 26
 10 00 86 06 00 00 2a e0 8e c0 58 50 a9 00 02 74
(II) I810(0): VESA BIOS not detected

Fatal server error:
AddScreen/ScreenInit failed for driver 0


```

If someone could help me figure this out that'd be great. Thanks.

---

