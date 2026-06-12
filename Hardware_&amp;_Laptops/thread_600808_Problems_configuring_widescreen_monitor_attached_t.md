---
title: "Problems configuring widescreen monitor attached to laptop"
date: 2007-11-02
forum: Hardware &amp; Laptops
---

### Post by utnapistim on 2007-11-02
Hi all,

Yesterday I got myself a LG widescreen monitor (**LG L194WS, 1440x900**) to attach it to my laptop (**Acer Aspire 1604LM**, running **Kubuntu 7.10**).

Running with the default settings (generated xorg.conf), the image showed on both screens (laptop and external), but on both monitors, the resolution was 1024x768 (max supported by the laptop screen).
The widescreen monitor displayed a background stretched to 1440x900, but the taskbar and all displayed windows were somewhere put in the upper-left corner of the screen (1024x768 rectangle).

Then, I tried setting up the external monitor through the kubuntu settings (K menu -> System Settings), but that didn't work: I coundn't find the exact monitor model, and with other ones I either got the same result by changing the settings, or broke the X server configuration completely (no longer starting).

Then, I tried manually editing the xorg.conf file (I read the man page, then recreated all entries from scratch, and generated the modeline for the monitor using **gtf 1440 900 60**.

With the new xorg.conf file (currently in use) the widescreen monitor appears to have a 1440x900 resolution(*), but only displays the left-upper corner of it, in 800x600 mode.

(*) -- Or, it could be 1024x768 - since I only see the left-upper corner, I can't really tell.

Anyone can help with getting the correct configuration?

This is my current xorg.conf:
> #define the input devices
Section "InputDevice"
    Identifier      "Generic Keyboard"

    Driver          "kbd"

    Option          "CoreKeyboard"
    Option          "XkbRules"          "xorg"
    Option          "XkbModel"          "pc105"
    Option          "XkbLayout"         "us"
EndSection

Section "InputDevice"
    Identifier      "Generic Mouse"

    Driver          "mouse"

    Option          "CorePointer"
    Option          "Device"            "/dev/input/mice"
    Option          "Protocol"          "ImPS/2"
    Option          "ZAxisMapping"      "4 5"
    Option          "Emulate3Buttons"   "true"
EndSection

Section "InputDevice"
    Identifier      "Synaptics Touchpad"

    Driver          "synaptics"

    Option          "SendCoreEvents"    "true"
    Option          "Device"            "/dev/psaux"
    Option          "Protocol"          "auto-dev"
    Option          "HorizEdgeScroll"   "0"
EndSection

Section "Files"
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"

    # path to defoma fonts
 FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load            "bitmap"
    Load            "ddc"
    Load            "dri"
    Load            "extmod"
    Load            "freetype"
    Load            "glx"
    Load            "int10"
    Load            "type1"
    Load            "vbe"
EndSection

# graphic card definition
Section "Device"
    Identifier  "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
    Driver      "ati"
    BusID       "PCI:1:0:0"
    Screen      0
EndSection


# define external monitor
Section "Monitor"
    Identifier      "LG External Monitor"


    VendorName      "LG Electronics"
    ModelName       "L194WS-SF 19inch"


    HorizSync       30-66
    VertRefresh     60

    # modeline generated using 'gtf 1440 900 60'
    Modeline        "1440x900_60.00"    106.47  1440 1520 1672 1904  900 901 904 932 -HSync +Vsync

    # enable monitor signal offing from the OS
    Option          "DPMS"
EndSection

#define laptop monitor
Section "Monitor"
    Identifier      "Laptop Monitor"

    # enable monitor signal offing from the OS
    Option          "DPMS"
EndSection



# Define the external "Screen" (a "Screen" is a grouping of a device and a monitor)
Section "Screen"
    Identifier      "Main Screen"

    Device          "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
    Monitor         "LG External Monitor"


    DefaultDepth    24

    SubSection "Display"
        #Modes      "1440x900_60.00"
        Virtual     1440 1440
    EndSubSection
EndSection


#ServerLayout: define a complete server configuration
# binding one or more screen sections wiith various input devices
Section "ServerLayout"
    Identifier      "Default Layout"

    Screen          "Main Screen"

    # input devices
    InputDevice     "Generic Keyboard"
    InputDevice     "Generic Mouse"
    InputDevice     "Synaptics Touchpad"

    # Off the signal after 30 minutes of no user activity
    Option          "OffTime"           "30"
EndSection

# Define global server options
Section "ServerFlags"

    # Select the default server layout
    Option          "DefaultServerLayout"       "Default Layout"

EndSection



One other thing: I tried installing 915resolution (I found some mentions of it in this forum), but it doesn't work. When installing it, I get an error message saying:
**Wrong chipset detected. 915resolution only works with Intel 800/900 series graphic chipsets.**

---

