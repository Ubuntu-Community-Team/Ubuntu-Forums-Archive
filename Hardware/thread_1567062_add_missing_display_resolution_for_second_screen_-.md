---
title: "add missing display resolution for second screen - 10.4"
date: 2010-09-03
forum: Hardware
---

### Post by brightweasel on 2010-09-03
Hi, 

I've installed Ubuntu Lucid Lynx 10.4 on my laptop. 
Everything working fine until I plug the external screen (DELL 1907FP). 
Optimal resolution of this screen is 1280 x 1024_60Hz
But I only get 1024 x 768 (4x3). 

How can I add the missing display resolution?

I've been trying around a lot. But no progress. 

I copy below the results of 
&#8226; the lshw command (describing graphic card), 
&#8226; xrandr 
&#8226; xorg.conf file (created through instructions as shown below)
&#8226; "system->admin->hardware drivers" gives "No proprietary drivers are in use on the system."

EDIT:
&#8226; following [http://ubuntuforums.org/showthread.php?t=1544501](http://ubuntuforums.org/showthread.php?t=1544501)
I replaced xorg.conf with 
```
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       31-65
        VertRefresh     50-120
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
             SubSection      "Display"
                Viewport        0 0
                Depth           24
                Modes           "1280x1024"
             EndSubSection
EndSection
```Then after restart, I could find the correct display resolution in "System -> Preferences -> Monitor"

&#8226; SO NOW, can somebody explain me how to fine tune  xorg.conf to perfectly fit my screen DELL 1907FP ?
Specifications are described in 
[http://support.dell.com/support/systemsinfo/document.aspx?c=us&l=en&s=gen&~file=/systems/1907fp/en/about.htm](http://support.dell.com/support/systemsinfo/document.aspx?c=us&l=en&s=gen&~file=/systems/1907fp/en/about.htm)

> **Resolution**
Horizontal scan range        30 kHz to 81 kHz (automatic)
Vertical scan range            56 Hz to 76 Hz (automatic)
Optimal preset resolution    1280 x 1024 at 60 Hz
Highest preset resolution    1280 x 1024 at 75 Hz 

**Preset Display Modes**
Display Mode    Horizontal Frequency (kHz)    Vertical Frequency (Hz)    Pixel Clock (MHz)    Sync Polarity (Horizontal/Vertical)
VESA    ...
VESA, 1280 x 1024    64.0        60.0        135.0    +/+ 
VESA, 1280 x 1024    80.0        75.0        135.0    +/+



THANKS!!!

_**lshw**_
> [SIZE=1]user@home-ubuntu:~$ sudo lshw -C display

  *-display:0             [/SIZE] [SIZE=1]
       description: VGA compatible controller
       product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:eff00000-eff7ffff ioport:eff8(size=8) memory:d0000000-dfffffff(prefetchable) memory:efec0000-efefffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:eff80000-efffffff[/SIZE]_**xrandr**_> [SIZE=1]user01@home-ubuntu:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9     59.9  
LVDS1 connected (normal left inverted right x axis y axis)
   1280x800       60.0 +
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV1 disconnected (normal left inverted right x axis y axis)[/SIZE]_**xorg.conf**_> [SIZE=1]Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"[/SIZE] [SIZE=1]
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"[/SIZE] [SIZE=1]
    Load  "glx"
    Load  "extmod"
    Load  "dri2"
    Load  "dri"
    Load  "dbe"
    Load  "record"
EndSection

Section "InputDevice"[/SIZE] [SIZE=1]
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"[/SIZE] [SIZE=1]
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"[/SIZE] [SIZE=1]
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"[/SIZE] [SIZE=1]
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "CacheLines"             # <i>
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "NoDDC"                  # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "XvMCSurfaces"           # <i>
        #Option     "PageFlip"               # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    VendorName  "Intel Corporation"
    BoardName   "Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"[/SIZE] [SIZE=1]
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection[/SIZE]**_creation of xorg.conf_**> [SIZE=1]create xorg.conf file:
[http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html](http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html)[/SIZE] [SIZE=1]
In order to generate xorg.conf you need to switch to one virtual console using the key combination CTRL + ALT + F1.
Now execute the following commands:
user@ubuntu ~# sudo service gdm stop
This command will stop the X.
Now we need to generate the xorg.conf file:
user@ubuntu ~# sudo Xorg -configure
This has generated the file in ~/xorg.conf.new.
We need to make the X using it so we have to put this file inside /etc/X11/
user@ubuntu ~# sudo mv ~/xorg.conf.new /etc/X11/xorg.conf
After moving this file to the proper location you can start the X again and see what happens:
user@ubuntu ~# sudo service gdm start[/SIZE]

---

