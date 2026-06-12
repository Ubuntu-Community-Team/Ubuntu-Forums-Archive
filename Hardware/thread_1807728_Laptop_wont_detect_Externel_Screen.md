---
title: "Laptop wont detect Externel Screen"
date: 2011-07-19
forum: Hardware
---

### Post by whynot on 2011-07-19
Hi everyone,
I have a computer ubuntu 11.4 Sony Vaio laptop with NVIDIA GeForce Go 6400 screen card. how could we control our external TFT monitor? 
Im tring to use nvidia-settings but it wont help me either
Thanks.

---

### Post by realzippy on 2011-07-19
Press Fn + F4 key...

---

### Post by whynot on 2011-07-19
> **realzippy said:**
> Press FN + F4 key...

Thanks but sony vaio hotkeys not supported by ubuntu :(
i have Sony Vaio VGN-FS750P/W

---

### Post by realzippy on 2011-07-19
..nvidia-settings working but not detecting the 2nd panel?

---

### Post by whynot on 2011-07-19
> **realzippy said:**
> ..nvidia-settings working but not detecting the 2nd panel?
What can i say there are two screens but not working i guess.

---

### Post by realzippy on 2011-07-19
Run in terminal

```
sudo nvidia-bug-report.sh
```

This script creates a file containing relevant information in your user's home directory.
Post that file.

---

### Post by whynot on 2011-07-19
> **realzippy said:**
> Run in terminal

```
sudo nvidia-bug-report.sh
```

This script creates a file containing relevant information in your user's home directory.
Post that file.
Ok

---

### Post by realzippy on 2011-07-19
```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6400"
#   Option "ConnectedMonitor" "DFP-0,CRT-0"
#   Option "UseDisplayDevice" "DFP-0,CRT-0"
#   Option "TwinView" "true"
#   Option "TwinViewOrientation" "Clone"
#   Option "TwinViewXineramaInfoOrder" "DFP-0,CRT-0"
#   Option "MonitorLayout" "LFP,LFP+CRT"
#   Option "metamodes" "DFP-0: 1024x768 +0+0, CRT-0: 1024x768 +0+0; DFP-0: 1280x1024 +0+0, CRT-0: 1280x1024 +0+0; DFP-0: 1024x768 +0+0, CRT-0: NULL"
EndSection
```


This is the device section of your xorg.conf..
Since there is a disabled (#) CRT-0 ,the nvidia driver "sees"
your crt output,but it seems to be not configurated,also
a "screen section" for CRT-0 does not (yet) exist.

Check nvidia-settings,very likely you have just overlooked a configuration option.
Also reconfigurating xorg.conf with
```
sudo nvidia-xconfig --twinview
```
might be worth a shot..

---

### Post by whynot on 2011-07-20
> **realzippy said:**
> ```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6400"
#   Option "ConnectedMonitor" "DFP-0,CRT-0"
#   Option "UseDisplayDevice" "DFP-0,CRT-0"
#   Option "TwinView" "true"
#   Option "TwinViewOrientation" "Clone"
#   Option "TwinViewXineramaInfoOrder" "DFP-0,CRT-0"
#   Option "MonitorLayout" "LFP,LFP+CRT"
#   Option "metamodes" "DFP-0: 1024x768 +0+0, CRT-0: 1024x768 +0+0; DFP-0: 1280x1024 +0+0, CRT-0: 1280x1024 +0+0; DFP-0: 1024x768 +0+0, CRT-0: NULL"
EndSection
```


This is the device section of your xorg.conf..
Since there is a disabled (#) CRT-0 ,the nvidia driver "sees"
your crt output,but it seems to be not configurated,also
a "screen section" for CRT-0 does not (yet) exist.

Check nvidia-settings,very likely you have just overlooked a configuration option.
Also reconfigurating xorg.conf with
```
sudo nvidia-xconfig --twinview
```
might be worth a shot..
I did that i tried some inputs that i find in google . But those changes dont worked.

Here is the new changes
```

Section "Device"

#   Option "ConnectedMonitor" "DFP-0,CRT-0"
#   Option "UseDisplayDevice" "DFP-0,CRT-0"
#   Option "TwinView" "true"
#   Option "TwinViewOrientation" "Clone"
#   Option "TwinViewXineramaInfoOrder" "DFP-0,CRT-0"
#   Option "MonitorLayout" "LFP,LFP+CRT"
#   Option "metamodes" "DFP-0: 1024x768 +0+0, CRT-0: 1024x768 +0+0; DFP-0: 1280x1024 +0+0, CRT-0: 1280x1024 +0+0; DFP-0: 1024x768 +0+0, CRT-0: NULL"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6400"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "True"
    Option         "MetaModes" "nvidia-auto-select, nvidia-auto-select"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```
in nvidia-settings window i tried to switch to Tft monitor mode but nothing happend. Tft tv dont detected.

---

### Post by realzippy on 2011-07-20
...please run in terminal

```
xrandr -q
```

and post output.

..........................
Also try this modified device section:

```
Section "Device"

    Option "ConnectedMonitor" "DFP-0,CRT-0"
    Option "UseDisplayDevice" "DFP-0,CRT-0"
    Option "TwinView" "true"
    Option "TwinViewOrientation" "Clone"
    Option "TwinViewXineramaInfoOrder" "DFP-0,CRT-0"
#   Option "MonitorLayout" "LFP,LFP+CRT"
    Option "metamodes" "DFP-0: 1024x768 +0+0, CRT-0: 1024x768 +0+0; DFP-0: 1280x1024 +0+0, CRT-0: 1280x1024 +0+0; DFP-0: 1024x768 +0+0, CRT-0: NULL"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6400"
EndSection

```

---

### Post by whynot on 2011-07-20
> **realzippy said:**
> ...please run in terminal

```
xrandr -q
```

and post output


```

$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1280 x 800, current 1280 x 800, maximum 1280 x 800
default connected 1280x800+0+0 0mm x 0mm
   1280x800       50.0*

```


This is the last changes
i have saved in nvidia-settings window display menu there is a button called Detect Displays.


```

$ cat /etc/X11/xorg.conf
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 270.29  (buildd@roseapple)  Fri Feb 25 14:43:24 UTC 2011

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder75)  Thu Apr 14 09:22:52 PDT 2011

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"

#   Option "ConnectedMonitor" "DFP-0,CRT-0"
#   Option "UseDisplayDevice" "DFP-0,CRT-0"
#   Option "TwinView" "true"
#   Option "TwinViewOrientation" "Clone"
#   Option "TwinViewXineramaInfoOrder" "DFP-0,CRT-0"
#   Option "MonitorLayout" "LFP,LFP+CRT"
#   Option "metamodes" "DFP-0: 1024x768 +0+0, CRT-0: 1024x768 +0+0; DFP-0: 1280x1024 +0+0, CRT-0: 1280x1024 +0+0; DFP-0: 1024x768 +0+0, CRT-0: NULL"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6400"
EndSection

Section "Screen"

# Removed Option "TwinView" "True"
# Removed Option "MetaModes" "nvidia-auto-select, nvidia-auto-select"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```


Thanks a lot.

---

### Post by realzippy on 2011-07-20
Confused:

This is your 1rst monitor section:

```
Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Nvidia Default Flat Panel"
    HorizSync       29.0 - 49.0
    VertRefresh     0.0 - 61.0
    Option         "DPMS"
EndSection

```
Which seems to be your laptop's panel.

Now you have:

```
Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

```

??
Also not sure about what you are saying with:
[I]i have saved in nvidia-settings window display menu there is a button called Detect Displays.

[/I]

Edited post #10,can you try the device section?

---

### Post by whynot on 2011-07-20
> **realzippy said:**
> Confused:

This is your 1rst monitor section:

```
Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Nvidia Default Flat Panel"
    HorizSync       29.0 - 49.0
    VertRefresh     0.0 - 61.0
    Option         "DPMS"
EndSection

```
Which seems to be your laptop's panel.

Now you have:

```
Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

```

??
Also not sure about what you are saying with:
[I]i have saved in nvidia-settings window display menu there is a button called Detect Displays.

[/I]

Edited post #10,can you try the device section?

sorry for making it complicated. I saved new settings under nvidia-settings application in this application there is a button called detect displays, which eventually saves after you click to save to x configuration file. by the way I just realized that you edited your previous message. I am waiting for your suggestions. thank you for your time.

---

### Post by realzippy on 2011-07-20
Well,my suggestion was to edit the device section (post #10),means
removing the # to enable the options,especially the:
#   Option "ConnectedMonitor" "DFP-0,CRT-0"

because: (from [ftp://download.nvidia.com/XFree86/Linux-x86/173.14.30/README/chapter-13.html](ftp://download.nvidia.com/XFree86/Linux-x86/173.14.30/README/chapter-13.html))
FAQs
**Nothing gets displayed on my second monitor; what is wrong?**
Monitors that do not support monitor detection using Display Data Channel (DDC) protocols (this includes most older monitors) are not detectable by your NVIDIA card. You need to explicitly tell the NVIDIA X driver what you have connected using the "ConnectedMonitor" option; e.g.,

    Option "ConnectedMonitor" "CRT, CRT"

ConnectedMonitor

    With this option you can override what the NVIDIA kernel module detects is connected to your graphics card. This may be useful, for example, if any of your display devices do not support detection using Display Data Channel (DDC) protocols. Valid values are a comma-separated list of display device names; for example:

        "CRT-0, CRT-1"
        "CRT"
        "CRT-1, DFP-0"

    WARNING: this option overrides what display devices are detected by the NVIDIA kernel module, and is very seldom needed. You really only need this if a display device is not detected, either because it does not provide DDC information, or because it is on the other side of a KVM (Keyboard-Video-Mouse) switch. In most other cases, it is best not to specify this option.

---

### Post by realzippy on 2011-07-20
Sorry,we have visitors,so I am out for 2 hours..

---

