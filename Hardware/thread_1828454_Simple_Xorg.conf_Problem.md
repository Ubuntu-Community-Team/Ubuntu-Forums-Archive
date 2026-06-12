---
title: "Simple Xorg.conf Problem"
date: 2011-08-18
forum: Hardware
---

### Post by fenderr357 on 2011-08-18
Hi All,

I have a laptop with two GPU's, one integrated, one dedicated, and I would like to set it up to where the X server runs off the dedicated GPU. 

I think I am close, Here is my xorg.conf:
```
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
    ModelName      "DELL 2009W"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "9400m"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9400M G"
    BusID          "PCI:3:0:0"
EndSection

Section "Device"
    Identifier     "g210m"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce G210M"
    BusID          "PCI:2:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "g210m"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

The above configuration results in a "No Screens Found" error. What am I doing wrong?

---

### Post by sbraz on 2011-08-19
this might help:
[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

also, try this on a terminal:
```
sudo nvidia-xconfig
```

---

### Post by realzippy on 2011-08-19
You have a 
9400m
**and** a 
210m ????????????????????
Where does your xorg.conf come from?Did you edit it?
Post output from:

```
lspci |grep VGA
```

---

### Post by fenderr357 on 2011-08-19
Thanks for the quick replies!

I looked at the VGA switcheroo page (which sounds exactly like what I'm looking for), and the first grep command returns this:
```
/boot/config-2.6.38-10-generic:CONFIG_VGA_SWITCHEROO=y
/boot/config-2.6.38-8-generic:CONFIG_VGA_SWITCHEROO=y

```
However, the "switch" file does not exist. Do I just create the directory and the "switch" file?

And yes, I have both of those GPU's. I'm on a Dell XPS 13 with hybrid graphics (SLI). I did edit my xorg.conf, but only to include the second device and switch Screen0 to use a different device. 

Output of lspci:
```
02:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce G210M] (rev a2)
03:00.0 VGA compatible controller: nVidia Corporation C79 [GeForce 9400M G] (rev b1)


```

Thanks for all the help.

---

### Post by realzippy on 2011-08-19
Do you have a "switch" in your laptop's BIOS for graphics ?

---

### Post by fenderr357 on 2011-08-21
> **realzippy said:**
> Do you have a "switch" in your laptop's BIOS for graphics ?

Nope.. they didn't make it that easy on me. :-x

---

### Post by realzippy on 2011-08-22
Install bumblebee,fingers crossed.
[https://github.com/MrMEEE/bumblebee](https://github.com/MrMEEE/bumblebee)

---

### Post by fenderr357 on 2011-08-23
Well, I installed bumblebee. It installed fine and everything, but it looks like all it does is use the acpi_call module to turn the discrete card on and off - but I can already do that with acpi_call itself. 

Is there no way to actually utilize the discrete card when its on? This is where I figured the X server could simply be configured to run the screen off of that device.

If I'm beating a dead horse here, just let me know.

Thanks again!

---

