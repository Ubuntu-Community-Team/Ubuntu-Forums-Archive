---
title: "Dual screens on Radeon Mobility M6 LY card"
date: 2006-07-14
forum: Hardware &amp; Laptops
---

### Post by javaJake on 2006-07-14
I want to get dual screens working on Linux. I haven't found a thing in Ubuntu itself, so I hope someone can point me onto some certain road. I am a newbie to this, if you can't tell.

This is on a Compaq Presario 1700 laptop. Here's some information on my video card:
Radeon Mobility M6 LY (or ATI Mobility M1 hardware-accelerated 3D Graphics) - 1002:4c59

---

### Post by javaJake on 2006-07-15
*bump*

I **know** there's someone that can help me out. It's just a matter o' posting. :)

---

### Post by ltmon on 2006-07-15
I've been trying similar myself on a mobility x1600 card, but haven't gotten too far.

Try first:
```

sudo fireglcontrolpanel

```

and see if it works for you.

L.

---

### Post by spiregrain on 2006-07-16
Just yesterday, I got this working on my ATI Technologies Inc Radeon Mobility 7000 IGP (4437).  The key seems to be the "MonitorLayout" and "CRT2VRefresh" lines.  The xorg.conf then goes like this:

```

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility 7000 (M6) (Primary)"
        Driver          "radeon"
        BusID           "PCI:1:5:0"
        Option          "MetaModes" "1024x768-1024x768 1024x768 1024x768-800x600"
        Option          "MergedDPI" "100 100"
        Option "MergedFB" "True"
        Option "MonitorLayout" "LVDS, CRT"
        Option          "CRT2Position" "RightOf"
#        Option          "CRT2Hsync" "40-80"
        Option          "CRT2VRefresh" "30-82"

EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility 7000 (M6) (Secondary)"
        Driver          "radeon"
        BusID           "PCI:1:5:0"
        Screen          1
EndSection




Section "Monitor"
        Identifier      "Generic Monitor (Laptop LCD)"
        Option          "DPMS"
        HorizSync       28-49
        VertRefresh     43-72
EndSection

Section "Monitor"
        Identifier      "External Monitor"
        Option          "DPMS"
EndSection


Section "Screen"
        Identifier      "Internal Screen"
        Device          "ATI Technologies, Inc. Radeon Mobility 7000 (M6) (Primary)"
        Monitor         "Generic Monitor (Laptop LCD)"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
Section "Screen"
        Identifier      "External Screen"
        Device          "ATI Technologies, Inc. Radeon Mobility 7000 (M6) (Secondary)"
        Monitor         "External Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          0 "Internal Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

```


Then I have to put this into my gnome startup with the "session" tool. ```
xrandr -s 0
```

Running xrandr on its own will list available modes.  The one I wanted happened to be zero.

---

### Post by javaJake on 2006-07-17
YAY! Some answers! Yipee! :D

I'll try this later today when I get home. I really appreciate it!

---

### Post by thelusiv on 2006-07-17
Any luck? I have been working on a Presario 1700US and would like to get dual VGA working.

---

### Post by javaJake on 2006-07-18
> **thelusiv said:**
> Any luck? I have been working on a Presario 1700US and would like to get dual VGA working.

Sorry... things have been very busy lately. If you want, I can give you my e-mail, and then you can use my e-mail to bug me if I don't do it in a couple of days. :D It is in my interests to figure this out, so I don't *want* to forget. :p

---

### Post by javaJake on 2006-07-19
> **ltmon said:**
> I've been trying similar myself on a mobility x1600 card, but haven't gotten too far.

Try first:
```

sudo fireglcontrolpanel

```

and see if it works for you.

L.

I ran that, and it gave me errors. I ran fireglcontrol instead and it said that the "XFree86-DRI" module is missing. Strange, because I think I am using Xorg, not XFree86...

---

