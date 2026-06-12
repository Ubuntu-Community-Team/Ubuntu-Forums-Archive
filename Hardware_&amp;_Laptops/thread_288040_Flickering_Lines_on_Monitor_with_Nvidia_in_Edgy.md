---
title: "Flickering Lines on Monitor with Nvidia in Edgy"
date: 2006-10-29
forum: Hardware &amp; Laptops
---

### Post by bjc on 2006-10-29
The upgrade from Dapper to Edgy broke my nv driver. The message alluded to an ABI incompatibility between the driver and the server version. (xserver-xorg-driver-nv is installed).

Changing "nv" to "nvidia" allowed me to startx, but now I have flickering lines on my (TFT) monitor. They're causing serious eyestrain, and I can't figure out how to get rid of them.

I've played around with various settings in xorg.conf, followed all the steps to install and configure the Nvidia drivers (they were all installed), and drew a blank. 

My monitor recommends 1280x1024@60Hz. I'm currently running at 1280x1024@75Hz (that's supported, too), because I gathered that flickering was normally a sign of a refresh rate set too low. Here's the spec. sheet: [http://h10010.www1.hp.com/wwpc/ie/en/sm/WF25a/20491-156249-156249-156249-169267-6388519.html](http://h10010.www1.hp.com/wwpc/ie/en/sm/WF25a/20491-156249-156249-156249-169267-6388519.html) .

Any tips? I'd rather not go back to Dapper over this.

---

### Post by taurus on 2006-10-29
May want to have a look at the vertical and horizontal refreshing rates in /etc/X11/xorg.conf.  And if it doesn't have those two lines, add them in.  Consult the manual for your monitor for the values...

---

### Post by bjc on 2006-10-29
> **taurus said:**
> May want to have a look at the vertical and horizontal refreshing rates in /etc/X11/xorg.conf.  And if it doesn't have those two lines, add them in.  Consult the manual for your monitor for the values...

Thanks for the help. :-) I believe I've already added them. That's the "    HorizSync       30.0 - 81.0 VertRefresh     56.0 - 76.0" section, right? The spec. sheet says "Horizontal frequency: 30-81 kHz, Vertical frequency: 56-76 Hz", so they seem to match up...

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

        # path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "dbe"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "gb"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "hp L1902"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "hp L1902"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

---

### Post by bjc on 2006-10-30
How can I revert back to the nv driver then?

---

