---
title: "Touchpad has no drag or scroll"
date: 2005-08-21
forum: Hardware &amp; Laptops
---

### Post by zugvogel on 2005-08-21
Hi everyone,

I recently installed ubuntu, and I'm impressed with it so far, but one very annoying problem I have is with the touchpad - I can't get it to drag things around the screen (usually by double-tapping, and holding down the last tap and moving the cursor) and there's no up-down scroll on the right of the touchpad.

I have xorg-driver-synaptics installed (ver. 0.13.6-0ubuntu5) and the section of the xorg.conf file looks like this:

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

I only use the touchpad, and no external mouse is fitted. Do I need to add/remove lines from xorg.conf, or is it more involved?

Any help would be much appreciated. Thanks.

---

### Post by s_p_a_r_k_y on 2005-08-21
Try adding the following to your mouse section
```

  Option        "Protocol"      "auto-dev"
  Option        "LeftEdge"      "1700"
  Option        "RightEdge"     "5300"
  Option        "TopEdge"       "1700"
  Option        "BottomEdge"    "4200"
  Option        "FingerLow"     "25"
  Option        "FingerHigh"    "30"
  Option        "MaxTapTime"    "180"
  Option        "MaxTapMove"    "220"
  Option        "VertScrollDelta" "100"
  Option        "MinSpeed"      "0.06"
  Option        "MaxSpeed"      "0.12"
  Option        "AccelFactor" "0.0010"
  Option        "SHMConfig"     "on"

```
It works for my synaptics mouse pad, although I also use a USB mouse. You may need to tune the settings a bit, but hope it works for you.

---

### Post by zugvogel on 2005-08-22
Many thanks for your reply - I thought that was going to cure the problem, but it turned out not to do anything. It's confusing since I do have the driver installed... I tried deleting the "configured mouse" input device section to see if that helped, but that turned out not to be healthy at all. I used to have Suse 9.1 installed on this computer, and after installing the driver it worked fine; but that was a long time ago now and I don't have the config file from then, any more.

Does anyone have any other ideas? It's a fairly important part of using my computer.

Thanks.

---

### Post by s_p_a_r_k_y on 2005-08-22
post your xorg.conf file here

---

### Post by jamesrw on 2005-08-23
i have same issue, but if my usb mouse is plugged in before booting it works fine... real strange.

---

### Post by zugvogel on 2005-08-23
Horray! It works! Your request for me to post the xorg.conf file made me notice something and gave me an idea, and I tried it and it worked!

My new xorg.conf file is as follows:

```

Section "Files"
        FontPath        "unix/:7100"                    # local font server
        # if the local font server has problems, we can fall back on these
        FontPath        "/usr/lib/X11/fonts/misc"
        FontPath        "/usr/lib/X11/fonts/cyrillic"
        FontPath        "/usr/lib/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/Type1"
        FontPath        "/usr/lib/X11/fonts/CID"
        FontPath        "/usr/lib/X11/fonts/100dpi"
        FontPath        "/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "LeftEdge"              "1700"
        Option          "RightEdge"             "5300"
        Option          "TopEdge"               "1700"
        Option          "BottomEdge"            "4200"
        Option          "FingerLow"             "25"
        Option          "FingerHigh"            "30"
        Option          "MaxTapTime"            "180"
        Option          "MaxTapMove"            "220"
        Option          "VertScrollDelta"       "100"
        Option          "MinSpeed"              "0.06"
        Option          "MaxSpeed"              "0.12"
        Option          "AccelFactor"           "0.0010"
        Option          "SHMConfig"             "on"
EndSection

Section "Device"
        Identifier      "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-49
        VertRefresh     43-72
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

The 6th line from the bottom which now reads:
InputDevice     "Synaptics Touchpad"
originally read as:
InputDevice     "Configured Mouse"

so this must be the section of the config file which tells the computer which part of the available InputDevices listed earlier, to use.

So, Jamesrw, it might be worth seeing what this area of your config file says, and playing around with that area to get the touchpad to work properly.

Sparky, many thanks for your help - if you hadn't asked to see the config file, I wouldn't have got it sorted.

---

### Post by jamesrw on 2005-08-23
thanx, I needed that bottom part, this thread also helped me out:

[http://ubuntuforums.org/showthread.php?t=45841](http://ubuntuforums.org/showthread.php?t=45841)

---

### Post by s_p_a_r_k_y on 2005-08-23
and everyone is happy : )

---

### Post by JLB on 2005-08-23
[QUOTE=jamesrw]thanx, I needed that bottom part, this thread also helped me out:

[http://ubuntuforums.org/showthread.php?t=45841](http://ubuntuforums.org/showthread.php?t=45841)[/QUOTE]

Glad It helped you out :D

---

