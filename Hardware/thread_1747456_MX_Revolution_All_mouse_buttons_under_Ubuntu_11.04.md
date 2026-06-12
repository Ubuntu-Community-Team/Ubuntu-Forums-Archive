---
title: "MX Revolution All mouse buttons under Ubuntu 11.04"
date: 2011-05-02
forum: Hardware
---

### Post by outleradam on 2011-05-02
I just thought I'd post this if someone came looking for the information.   In order to get the MX Revolution mouse working under Ubuntu 11.04, all that is required is to replace a few lines in the /etc/X11/xorg.conf file.

**1. Install your mouse by modifying the /etc/X11/Xorg.conf file to add support.**

1A. modify the server layout section which refers to "mouse".  Change it to MX Rev
```

     InputDevice    "MX Rev"

```1B. And replace the inputDevice section which refers to the default mouse with this:
```

 Section "InputDevice"
 
      #VX Rev users can type "VX Rev"
     Identifier     "MX Rev"
     Driver         "evdev"
     Option         "Device" "/dev/input/event3"
     Option         "CorePointer"
     Option         "Protocol" "ExplorerPS/2"
     Option         "ZAxisMapping" "4 5"
     Option         "HWheelRelativeAxisButtons" "7 6"
     Option         "Buttons" "19"
 EndSection
```
Here is my entire /etc/X11/xorg.conf file.
```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "MX Rev"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

     #VX Rev users can type "VX Rev"
    Identifier     "MX Rev"
    Driver         "evdev"
    Option         "Device" "/dev/input/event3"
    Option         "CorePointer"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "HWheelRelativeAxisButtons" "7 6"
    Option         "Buttons" "19"
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
    ModelName      "HP 2009"
    HorizSync       24.0 - 85.0
    VertRefresh     48.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 260"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-0: nvidia-auto-select +1920+0, DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```After modifying the /etc/X11/Xorg.conf file, you should reboot so that the X server changes can take effect.


[B]2. Map your buttons
[/B]You can use the terminal command 'xev' to find out the numbers of your buttons.    Add the grep command to the statement to filter out the useless information
```
xev|grep button
```Here's the button numbers:
1-Left Mouse
2-Scroll wheel click
3-Right mouse
4-scroll wheel scrolll up
5-scroll wheel scroll down
6-scroll wheel tilt left
7-scroll wheel tilt right
8-thumb back
 9-thumb forward
xf86-search-"search button"
13-thumb wheel up
14-thumb wheel down
16-thumb wheel click
[B]
3. Assign buttons
[/B]3a.  using app "Keyboard shortcuts" you can assign some buttons
3b.  Using compiz-config, you can assign most buttons.
 Install compizconfig and run ```
sudo aptitude *install compizconfig*-settings-manage
compiz-config
```Personally, I've got my "Search" button mapped to run gnome-terminal.  The thumbwheel forward and back are mapped to zoom in and zoom out.  The thumbwheel click is mapped to "expo" so I can see all of my desktops.

let me know if this helps you!

---

### Post by nike234 on 2011-05-03
Thank's a lot... going to try that next time I boot into Natty. Refused to upgrade 10.04 yet because I use my MX Revo and all of its buttons (e.g. for turning the desktop cube).

My question: Do you have any idea if there's a little gui like BTNX to configure my MX?
I'm looking for a tool, that combines the button-configuration and the scroll-wheel configuration (free spin on/off).

thank you
greetz
nike234

---

### Post by outleradam on 2011-05-10
yep.  all buttons are working as they should and reprogrammable through the compiz-config program and handled practically natively under 11.04..   No need to not upgrade.   Also, if you are wanting to use 10.04, you can use my other guide on how to do that.  Search my profile.

---

### Post by the hoplite on 2011-05-14
Hi. I have a MX1100 mouse but the button layout is identical a part from the second wheel. I was hoping to apply your solution but then I realized that I don't have any xorg.conf file. Could I just create it and apply your corrections, just those inherent to the mouse?

Thanks, bye.

---

### Post by mofirouz on 2011-09-30
Thank you thank you thank you thank you thank you thank you

---

### Post by monkley on 2011-10-31
Hi, I'm trying to get the MX Revolution working in 11.10 but I don't have an Xorg.conf file!

If I try to create one by
sudo Xorg -configure, I get a Fatal server error, Server is already active message.

Does anyone know how I go about creating the conf file or how to set up the mouse in 11.10?

---

