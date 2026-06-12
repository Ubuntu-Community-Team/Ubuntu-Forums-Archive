---
title: "Resolution on a T42, ATI Radeon Mobility 7500"
date: 2007-09-01
forum: Hardware &amp; Laptops
---

### Post by kristiankarlson on 2007-09-01
Dear all,

I have read some of the related threads, but has not found a solution to the following problem with my resolution:

I use a Thinkpad IBM T42 w ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500].

I dock my laptop and use a 19" screen. In Windows, it is possible to use 1280*1024 and 75 hz freq. However, I can only choose 1024*768 in the screen resolution window with 60 hz freq.

Can somebody help me out on that one? I have already tried to see the '/etc/X11/xorg.conf', but it looks fine...

Thanks,  Kristian

---

### Post by ctt1wbw on 2007-09-01
Have you tried adding the desired screen resolution in front of the 1024x768 on the same line?

---

### Post by kristiankarlson on 2007-09-03
Yes I have. In fact, it was already 1280*1024 in the xorg.
Any ideas?

---

### Post by angryfirelord on 2007-09-03
Run:
```
sudo dpkg-reconfigure xserver-xorg
```
You can keep the default values (unless you know what you're doing) until you hit the resolutions at the end.

---

### Post by kristiankarlson on 2007-09-11
It does not seem to help.
The screen looks like a whirlpool.

Any other suggestions?

---

### Post by jaroots on 2007-09-11
I also have a Thinkpad T42 and am frustrated at the 1024x768 screen limitation. I have had my laptop for a year now and from what I have come to understand is that this is a hardware limitation of the lcd itself. I made numerous attempts to increase resolution when  it was running XP and finally called into support. They said I would need to upgrade my lcd for $800+. Regardless of where the driver comes from, this resolution cannot increase. The only workaround is to use an external monitor. :mad:
- which btw I am still having a challenge to extend to both the lcd and external monitor.

---

### Post by kristiankarlson on 2007-09-12
Yeah. My problem resides with the external monitor. I am aware of the limitation of 1024*768 at the laptop-LCD. This also goes for Windows. However, using an external 19"-LCD monitor is not a problem in Windows - the ATI RADEON 7500 supports the resolution of 1280*1024 (@75hz), but it doesn't seem to do so in Ubuntu.

Is it necessary to configure the xorg manually? Hope somebody can help me. I can post the xorg if needed. The problem seems to be the extension to the external monitor.

br Kristian

---

### Post by angryfirelord on 2007-09-12
> **kristiankarlson said:**
> It does not seem to help.
The screen looks like a whirlpool.

Any other suggestions?
Are you sure you picked the right driver? (Should say ati). Also, make sure you've selected the proper resolutions at the end.

---

### Post by rybu on 2007-09-12
I have an ATI mobility radeon in my thinkpad T30, and it's running 1400x1050 at the moment.   From a generic distribution of Ubuntu, all I had to do was modify the device and screen bits of the xorg.conf file like below:

```

Section "Device"
        Identifier        "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility
9000]"
        Driver                "radeon"        
        BusID                "PCI:1:0:0"
        Option                "XAANoOffscreenPixmaps"
        VideoRam        32768
        Option              "Accel"
        Option              "AGPFastWrite"              "on" #changed
        Option              "AGPMode"                   "4"
        Option              "AGPSize"                   "64"
        Option              "BufferSize"                "2"
        Option              "ColorTiling"               "true" #changed
#        Option                "DisplayPriority"            "BIOS"
        Option              "DynamicClocks"             "yes"
        Option              "EnableDepthMoves"          "true" #changed
        Option              "EnablePageFlip"            "true" #changed
        Option                 "GARTSize"                     "64"
        Option              "RenderAccel"               "true" #changed
        Option              "RingSize"                  "8"
EndSection

Section "Monitor"
        Identifier        "Generic Monitor"
        Option                "DPMS"
EndSection

Section "Screen"
        Identifier        "Default Screen"
        Device                "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility
9000]"
        Monitor                "Generic Monitor"
        DefaultDepth        16
        SubSection "Display"
                Depth                1
                Modes                "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth                4
                Modes                "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth                8
                Modes                "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth                15
                Modes                "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth                16
                Modes                "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth                24
                Modes                "1400x1050"
        EndSubSection
EndSection


```

Works great for me.

---

