---
title: "resolution won't stay set"
date: 2006-06-13
forum: Hardware &amp; Laptops
---

### Post by one_ro on 2006-06-13
Hi all,

I have this annoying problem I can't solve: my laptop is a Toshiba Satellite Pro 6100 with a NVidia video card.
From the command **sudo ddcprobe** I get:

vbe: VESA 3.0 detected.
oem: NVidia
vendor: NVidia Corporation
product: NV17 () Board Chip Rev A2

I also used lspci to find out more: **lspci | grep -i vga**
0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 
Go] (rev a3)

I've installed the latest NVIDIA drivers but I can't use them.

My xorg.conf file (below) shows driver "nv" in the Device section
I tried setting it to "nvidia" (that's what nvidia-xconfig does anyway) but I 
only get a blank screen after restarting the X server.
I tried stopping the X server before, and then restarting it, same result. In 
the blank screen I can't even use the command line (opened with Ctrl+Alt+F2); 
the laptop just freezes and I have to power it off manually.

With my current xorg.conf file I can set the resolution to 1024x768, but it 
gets to 640x480 after each reboot (which is kind of annoying). 
Could anybody please give me a hint on what should I do in order to set the resolution permanently?

Oh, I have to mention that I'm using an external monitor (Philips 107P) for which I have edited the Hsync and VertRefresh.

TIA,
Adrian

Here's my xorg.conf:
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
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
    Load           "extmod"
    Load           "freetype"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
    Load           "glx"
  #load "GLcore"
    Load           "v4l"
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
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

  # /dev/input/event
  # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"# Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"

  # /dev/input/event
  # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"# Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"

  # /dev/input/event
  # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"# Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    ModelName      "Custom 1"
    HorizSync       30.0 - 92.0
    VertRefresh     60.0 - 160.0
    ModeLine       "1024x768_85.00" 94.4 1024 1088 1200 1376 768 769 772 807 -hsync +vsync
EndSection

Section "Monitor"
 # 
    Identifier     "monitor1"
    Gamma           1
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV17 [GeForce4 420 Go]"
    Driver         "nv"
    BoardName      "nv"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
 # 
    Identifier     "device1"
    Driver         "nv"
    BoardName      "nv"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV17 [GeForce4 420 Go]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1024x768"
    EndSubSection
EndSection

Section "Screen"
 # 
    Identifier     "screen1"
    Device         "device1"
    Monitor        "monitor1"
    DefaultDepth    24
EndSection
```

---

### Post by tseliot on 2006-06-13
Try point 7 of the Problems section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION")

---

### Post by one_ro on 2006-06-14
[QUOTE=tseliot]Try point 7 of the Problems section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION")[/QUOTE]

Hello tseliot, thanks very much for the reply.
Sigh...
Nope, it didn't work. I tried both changes to xorg.conf but after restarting the X server the resolution is back to 640x350 and refresh rate to 60 Hz.
If you have any other ideas, what else to check for, i'd be more than happy to hear...

---

### Post by tseliot on 2006-06-14
Try point 10 or point 5 of the problems section

---

### Post by one_ro on 2006-06-14
[QUOTE=tseliot]Try point 10 or point 5 of the problems section[/QUOTE]

Tried both, still the same result.
**dpkg-reconfigure xserver-xorg** (after stopping kdm with **/etc/init.d/kdm stop**) only changed my xorg.conf (sure, it did a backup before)
Curious enough, even though the new xorg.conf doesn't have any modelines, I can still change the resolution and refresh rate manually from System Settings.

Am I doomed?

---

### Post by tseliot on 2006-06-14
Try point 7 again but this time use this option:
```
options nvidia NVreg_SoftEDIDs=0 NVreg_Mobile=4
```

and make sure the driver is set to nvidia


[COLOR="Red"]P.S. and of course all the suggestions I provided until now only work with a the nvidia driver enabled[/COLOR]

---

### Post by one_ro on 2006-06-14
[QUOTE=tseliot]Try point 7 again but this time use this option:
```
options nvidia NVreg_SoftEDIDs=0 NVreg_Mobile=4
```

and make sure the driver is set to nvidia

[COLOR="Red"]P.S. and of course all the suggestions I provided until now only work with a the nvidia driver enabled[/COLOR][/QUOTE]

Hmm... I them but everytime I set "nvidia" instead of "nv" I get a blank screen after restarting X.
I tried **sudo xinit -- :2** with the same result: everything is frozen, I can't even get back to Alt+Ctrl+F7. Nothing responds so I had to switch it off, reboot in recovery mode, unset "nvidia" to "nv" and everything is back to... setting the resolution manually from 640x350.

Sigh... this is really annoying...

---

### Post by drewbie03909 on 2006-07-25
Did you ever solve this problem?  I also have a Satellite Pro 6100 (but with higher res display).  I experienced the same frustration installing the nvidia driver.

I've attached the relevant section of my xorg.conf file - hope it helps.

I wound up removing everything and restarted from scratch, using tseliot's guide - which is excellent!  Thanks for the great doc!  Excellent work.


Section "Monitor"
    Identifier     "SatPro LCD"
    HorizSync       28.0 - 70.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV17 [GeForce4 420 Go]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV17 [GeForce4 420 Go]"
    Monitor        "SatPro LCD"
    DefaultDepth    16
    Option "ExactModeTimingsDVI"
    Option "UseEdidDpi" "FALSE"
    Option "ModeValidation" "NoEdidDFPMaxSizeCheck, NoVesaModes"
    SubSection     "Display"
        Depth       1
        Modes      "1400x1050"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1400x1050"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1400x1050"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1400x1050"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1400x1050"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1400x1050"
    EndSubSection
EndSection

---

