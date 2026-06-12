---
title: "Dual Monitor Issues on Tecra M4"
date: 2008-04-13
forum: Hardware &amp; Laptops
---

### Post by jerew on 2008-04-13
Hey, I have been going crazy trying to get my dual-monitors to work on my Toshiba Tecra M4 laptop. I got the Nvidia drivers installed using ENVY, and the video card detects that I have a second monitor plugged in (it even knows the right resolution), but when I have it try two screens, my main laptop screen crashes, and the second monitor never turns off standby. The monitor worked great in Windows (I just tried it).

I've tried other monitors, and they don't seem to work either. I've also tried this on 7.10 and 8.04 beta. 

Here's my X11 from my new install of Hardy Heron:

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Synaptics Touchpad"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "vmmouse"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "TOSHIBA Internal Panel"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6600 TE/6200 TE"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"

# Removed Option "metamodes" "CRT: nvidia-auto-select +1400+0, DFP: nvidia-auto-select +0+0"
# Removed Option "TwinView" "1"
# Removed Option "metamodes" "CRT: 640x400 +1400+0, DFP: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection



I've consulted some good Linux guys I know, and they can't come up with anything. I am at a loss...

---

### Post by overdrank on 2008-04-13
HI and have you tried the nvidia-settings? If you are using Hardy then go to synaptic manager located under system, administration. Search for nvidia and install nvidia-settings. Then using the alt, F2 key use the command ```
gksudo nvidia-settings
``` there you can adjust your dual screens and resolution. Hope this helps and good luck!

---

### Post by jerew on 2008-04-13
Yeah, sorry I forgot to mention that I've been adjusting the settings *through* sudo nvidia-settings, and still nothing. I've tried applying changes, or writing it to the xorg.conf file and restarting XServer. Neither have worked.

Also, under the secondary monitor section of nvidia-settings, the only thing listed is "refresh rate unknown" I used an EDID reader on a windows machine to get the information from the EDID file, but I'm not sure if that is relevant.

---

### Post by jerew on 2008-04-15
Update:

I tried doing this manually without nvidia or twinview. I have it so that the screen will occasionally turn on, completetley white, and then slowly turn a splotchy purple. Then nothing. I took out the Configured Monitor section, because it didn't seem to do anything when I deleted it... Here's the xorg.conf for that setup:

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Screen0" 
    Screen         "Screen1" RightOf "Screen0"
    InputDevice    "Synaptics Touchpad"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    Option         "xinerama" "on"
    Option         "clone"    "off"
EndSection

Section "ServerFlags"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "vmouse"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "TOSHIBA Internal Panel"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "ViewSonic Q19wb-2"
    HorizSync       31.0 - 80.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6600 TE/6200 TE"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6600 TE/6200 TE"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24

SubSection "Display"
        Depth       1
        Modes       "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"

EndSubSection
    SubSection "Display"
        Depth       4
        Modes       "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
EndSubSection

    SubSection "Display"
        Depth       8
        Modes       "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
EndSubSection

    SubSection "Display"
        Depth       15
        Modes       "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
EndSubSection

    SubSection "Display"
        Depth       16
        Modes       "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
    
    SubSection "Display"
        Depth       24
        Modes       "1400x1050" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection

EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
SubSection "Display"
        Depth       1
        Modes       "1440x900" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"

EndSubSection
    SubSection "Display"
        Depth       4
        Modes       "1440x900" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
EndSubSection

    SubSection "Display"
        Depth       8
        Modes       "1440x900" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
EndSubSection

    SubSection "Display"
        Depth       15
        Modes       "1440x900" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
EndSubSection

    SubSection "Display"
        Depth       16
        Modes       "1440x900" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
    
    SubSection "Display"
        Depth       24
        Modes       "1440x900" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---

