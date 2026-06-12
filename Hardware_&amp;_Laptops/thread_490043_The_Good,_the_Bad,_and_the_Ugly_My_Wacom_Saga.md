---
title: "The Good, the Bad, and the Ugly: My Wacom Saga"
date: 2007-07-02
forum: Hardware &amp; Laptops
---

### Post by mjfernandez on 2007-07-02
Hello fellow Ubuntuites:

**The Good**
My Wacom tablet, an Intuos2 USB, Works in Feisty Fawn. 

**The Bad**
Its movement is currently relative, and I'd like the stylus to position the cursor absolutely on the screen. I've already added this to my /etc/X11/xorg.conf according to several HOWTO's:
    Option         "Mode" "Absolute"
But it's had no effect.

**The Ugly**
Although the "3D Mouse" works fine, the stylus is impossible to use because the tablet registers seemingly random clicks every couple of seconds, or more often. I've added this line to xorg.conf, and it has also had no effect on my problem:
    Option         "PressCurve" "50,0,100,50"



So I'm at a loss. Here's my entire Xorg configuration file, for reference. I know it's not pretty, but this is how Ubuntu wrote it, except for the added Wacom lines.

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
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
#    Load	"dri"
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
    Option         "XkbLayout" "us"
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
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option 	   "USB" "on"
    Option 	   "PressCurve" "50,0,100,50"
    Option         "Mode" "Absolute"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option 	   "USB" "on"
    Option 	   "Mode" "Absolute"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
    Option 	   "USB" "on"
    Option 	   "Mode" "Relative"
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV25 [GeForce4 Ti 4200]"
    Driver         "nvidia"
    Option	"AllowGLXWithComposite" "true"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV25 [GeForce4 Ti 4200]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option	   "AddARGBGLXVisuals" "true"
    Option         "RenderAccel" "true"
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

---

### Post by mjfernandez on 2007-07-03
I'm out of ideas, folks :) Do any of you have one?

---

### Post by mjfernandez on 2007-07-04
Still trying to figure this out. Can I provide more information?

---

### Post by naught101 on 2007-08-22
would also be interested in this information.

---

