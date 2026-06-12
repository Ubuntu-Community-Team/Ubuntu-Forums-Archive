---
title: "Xinerama not working with GX2"
date: 2008-07-11
forum: General Help
---

### Post by strattonbrazil on 2008-07-11
I have a nvidia 9800 GX2 in my system.  The package nvidia-glx didn't work with it, so I switched to envy, which didn't work, so I used a tutorial to make sure every driver remnant was off my system and installed the driver straight from nvidia's website.  

The problem now is I can't setup my two monitors to use xinerama.  I have two DELL 2407WFPs.  Only one screen is working, while the other screen is just black.  Going into nvidia-settings, I see both monitors but the second one is disabled (see attached screenshot).  When using my previous card, a 7800, xinerama was working fine, but that may just be a consequence of it being older and supported in the nvidia-glx package.  

How can I setup my xinerama on my second monitor?  

```

Section "ServerLayout"
    Identifier     "Layout[all]"
    Screen         "Screen[fbdev]" 0 0
    InputDevice    "Keyboard[0]" "CoreKeyboard"
    InputDevice    "Mouse[1]" "CorePointer"
    Option         "Xinerama" "off"
EndSection

Section "Files"
    ModulePath      "/usr/lib/xorg/modules"
    InputDevices      "/dev/ttyS0"
    InputDevices      "/dev/ttyS1"
    InputDevices      "/dev/ttyS2"
    InputDevices      "/dev/ttyS3"
    InputDevices      "/dev/ttyS4"
    InputDevices      "/dev/ttyS5"
    InputDevices      "/dev/ttyS6"
    InputDevices      "/dev/ttyS7"
    InputDevices      "/dev/ttyS8"
    InputDevices      "/dev/psaux"
    InputDevices      "/dev/logibm"
    InputDevices      "/dev/sunmouse"
    InputDevices      "/dev/atibm"
    InputDevices      "/dev/amigamouse"
    InputDevices      "/dev/atarimouse"
    InputDevices      "/dev/inportbm"
    InputDevices      "/dev/gpmdata"
    InputDevices      "/dev/usbmouse"
    InputDevices      "/dev/adbmouse"
    InputDevices      "/dev/input/mice"
    InputDevices      "/dev/input/event0"
    FontPath        "/usr/share/fonts/truetype/"
    FontPath        "/usr/share/fonts/uni/"
    FontPath        "/usr/share/fonts/misc/"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "AllowMouseOpenFail"
    Option         "BlankTime" "0"
EndSection

Section "InputDevice"
    Identifier     "Keyboard[0]"
    Driver         "kbd"
    Option         "Protocol" "Standard"
    Option         "XkbRules" "xfree86"
    Option         "XkbKeycodes" "xfree86"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Mouse[1]"
    Driver         "mouse"
    Option         "Protocol" "explorerps/2"
    Option         "Device" "/dev/input/mice"
EndSection

Section "Modes"
    Identifier         "Modes[0]"
    ModeLine     "800x600" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine     "640x480" 31.5 640 656 720 840 480 481 484 500 # 6. Try
    ModeLine     "640x480" 31.5 640 680 720 864 480 488 491 521 # 5. Try
    ModeLine     "640x480" 28 640 664 760 800 480 491 493 525 # 4. Try
    ModeLine     "640x480" 28.32 640 664 760 800 480 491 493 525 # 3. Try
    ModeLine     "640x480" 25.18 640 664 760 800 480 491 493 525 # 2. Try
    ModeLine     "640x480" 25.175 640 664 760 800 480 491 493 525 # 1. Try
EndSection

Section "Modes"
    Identifier         "Modes[vmware]"
    ModeLine     "800x600" 29.38 800 816 896 992 600 601 604 617
EndSection

Section "Monitor"
    Identifier     "Monitor[0]"
    VendorName     "Initial"
    ModelName      "Initial"
    UseModes       "Modes[0]"
    HorizSync       25.0 - 40.0
    VertRefresh     47.0 - 75.0
EndSection

Section "Monitor"
    Identifier     "Monitor[vmware]"
    VendorName     "Initial"
    ModelName      "Initial"
    UseModes       "Modes[vmware]"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Monitor"
    Identifier     "Monitor[vesa]"
    VendorName     "VESA"
    ModelName      "VESA"
    HorizSync       31.0 - 48.0
    VertRefresh     50.0 - 60.0
EndSection

Section "Device"

  #BusID        "1:0:0"
  # device_options
    Identifier     "Device[0]"
    Driver         "ChangeMe"
    Option         "sw_cursor" "on"
EndSection

Section "Device"

  # fbdev_options
    Identifier     "Device[fbdev]"
    Driver         "nvidia"
EndSection

Section "Device"

  #Option        "DefaultRefresh"
    Identifier     "Device[vesa]"
    Driver         "vesa"
    Option         "ModeSetClearScreen" "no"
    Option         "ShadowFB" "off"
EndSection

Section "Device"
    Identifier     "Device[vmware]"
    Driver         "vmware"
EndSection

Section "Screen"
    Identifier     "Screen[0]"
    Device         "Device[0]"
    Monitor        "Monitor[0]"
    DefaultDepth    16
    SubSection     "Display"
        Depth       16
        Modes      "800x600"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "800x600"
    EndSubSection
    SubSection     "Display"
        Depth       32
        Modes      "800x600"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "800x600"
    EndSubSection
EndSection

Section "Screen"

#@DefaultDepth@
    Identifier     "Screen[fbdev]"
    Device         "Device[fbdev]"
    Monitor        "Monitor[0]"
    Option         "ShadowFB" "off"
    SubSection     "Display"
        Modes      "default"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "default"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "default"
    EndSubSection
    SubSection     "Display"
        Depth       32
        Modes      "default"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "default"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen[vesa]"
    Device         "Device[vesa]"
    Monitor        "Monitor[vesa]"
    SubSection     "Display"
        Depth       16
        Modes      "default"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "default"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen[vmware]"
    Device         "Device[vmware]"
    Monitor        "Monitor[vmware]"
    SubSection     "Display"
        Depth       8
        Modes      "800x600"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "800x600"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "800x600"
    EndSubSection
EndSection


```

---

