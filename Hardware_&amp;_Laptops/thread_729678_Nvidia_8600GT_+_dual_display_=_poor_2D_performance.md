---
title: "Nvidia 8600GT + dual display = poor 2D performance"
date: 2008-03-20
forum: Hardware &amp; Laptops
---

### Post by artin1982 on 2008-03-20
Hi ,
This is over a week that I'm trying to run dual display with 8600gt but I always had 2d performance problem .

there is very small lag every 2-3 secs and its annoying :( 
I have this problem when dual display is enabled ! mean there is no any problem with single display. ( or its not noticeable )

I've tried last Nvidia drivers (171.06 , 168.12 , 100.14.19) but I had same result with all of them,

also Xorg process is using 15-40% cpu usage ! ( even when i am surfing web pages )

here is my xorg.conf

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
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
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "vmmouse"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    SubSection     "Display"
        Modes      "800x600"
    EndSubSection
EndSection

Section "Screen"

# Removed Option "TwinView" "0"
# Removed Option "metamodes" "CRT-0: 1280x1024_75 +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT-0: 1280x1024 +0+0, CRT-1: 1280x1024 +1280+0"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection


```

other information :
CPU: Q6600
RAM : 2GB
HDD : 160GB SATA II Hitachi
Ubuntu : 8.04
Kernel : 2.4.23.3

---

### Post by chewearn on 2008-03-20
Just confirming, you use twinview for dual displays, and not "separate X screens" ?

The 1 to 2 seconds lag, I have only seen on the "separate X screens" option, and it only happens to the primary screen, in gnome desktop only, and with compiz effect enabled.  There is a fix for this, but from your xorg.conf, I see twinview is used in your set-up, so I don't know.

---

### Post by artin1982 on 2008-03-20
> **AstalaVista said:**
> Just confirming, you use twinview for dual displays, and not "separate X screens" ?

The 1 to 2 seconds lag, I have only seen on the "separate X screens" option, and it only happens to the primary screen, in gnome desktop only, and with compiz effect enabled.  There is a fix for this, but from your xorg.conf, I see twinview is used in your set-up, so I don't know.

now I am  using "twinview" but I've tried "separate X screen" too and I had very very poor result with that ! :( just imagine it was taking 3-4 secs  for opening main menu !

/

compiz is disabled

---

### Post by IsawSp4rks on 2008-03-20
Are you using nvidia-glx-new?

EDIT : Ignore the question, I didn't read your post properly.

I have similar issues on Hardy Heron.

---

### Post by artin1982 on 2008-03-22
GtkPerf test result

first time :
```

GtkPerf 0.40 - Starting testing: Sat Mar 22 19:47:51 2008

GtkEntry - time:  0.04
GtkComboBox - time:  2.22
GtkComboBoxEntry - time:  1.61
GtkSpinButton - time:  0.33
GtkProgressBar - time:  5.05
GtkToggleButton - time:  1.21
GtkCheckButton - time:  0.68
GtkRadioButton - time:  0.78
GtkTextView - Add text - time:  0.57
GtkTextView - Scroll - time:  0.27
GtkDrawingArea - Lines - time:  0.42
GtkDrawingArea - Circles - time:  0.53
GtkDrawingArea - Text - time:  0.37
GtkDrawingArea - Pixbufs - time:  0.55
 --- 
Total time: 14.62

```

second time:
```

GtkPerf 0.40 - Starting testing: Sat Mar 22 19:48:28 2008

GtkEntry - time:  0.05
GtkComboBox - time:  4.34
GtkComboBoxEntry - time:  2.24
GtkSpinButton - time:  1.33
GtkProgressBar - time:  9.34
GtkToggleButton - time:  2.54
GtkCheckButton - time:  1.03
GtkRadioButton - time:  0.80
GtkTextView - Add text - time:  1.79
GtkTextView - Scroll - time:  0.47
GtkDrawingArea - Lines - time:  0.41
GtkDrawingArea - Circles - time:  1.53
GtkDrawingArea - Text - time:  0.55
GtkDrawingArea - Pixbufs - time:  0.75
 --- 
Total time: 27.14


```

---

