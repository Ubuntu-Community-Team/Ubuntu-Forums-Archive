---
title: "Dual Monitors Different Resolutions"
date: 2006-01-18
forum: Hardware &amp; Laptops
---

### Post by WalterDirt on 2006-01-18
A long while ago I tried using Ubuntu and dual monitors but it came out they needed to be the same resolution. I've made up my mind to go full force into Linux leaving Windows behind, but this is really bugging me.

Does anyone know if its possible yet to run dual monitors (big desktop) with two different resolutions (different monitors)? I would appreciate any help, a working sample conf would be incredible if possible.

Hardware: ATI 9800 Pro
Monitor Resolutions: 1920x1200 (16:10) and 1600x1200 (4:3)

Thanks

---

### Post by siorai on 2006-01-18
It's definitely possible. Even though I'm using an Nvidia card I would think it's pretty much well the same. It's all about the MetaModes. Here's the relevant sections of my xorg.conf:

```
Section "ServerLayout"
    Identifier     "Dual1"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse" "CorePointer"
EndSection



Section "Module"

#    Load    "GLcore"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
#    Load    "dri"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "false"
EndSection

Section "Monitor"
    Identifier     "DELL 2005FPW"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
    Modeline	   "1680x1050@60" 154.20 1680 1712 2296 2328 1050 1071 1081 1103
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV40 [GeForce 6800]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV40 [GeForce 6800]"
    Monitor        "DELL 2005FPW"
    DefaultDepth    24
    Option         "TwinView"
    Option         "NoLogo" "1"
    Option         "MetaModes" "1280x1024, 1680x1050; 1280x1024, 1280x1024; 1280x1024, 1152x864; 1024x768, 1024x768; NULL,1680x1050; NULL,1280x1024; NULL,1152x864; NULL,1024x768"
    Option         "SecondMonitorHorizSync" "31-85"
    Option         "SecondMonitorVertRefresh" "55-85"
    Option         "TwinViewOrientation" "RightOf"
    Option         "RenderAccel" "true"
    Option         "AGPFastWrite" "true"
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

So I have the one videocard, an Nvidia 6800 and two monitors, a Dell 2005FPW @ 1680x1050 (primary) and a Dell 1800FP @ 1280x1024 as the secondary to the left of the primary. You just need to include the various resolution combinations that you will need. Use NULL when you want that particular monitor to turn off. I use NULL so that when I play games on the primary, the secondary turns off as this eleviates any games wanting to go fullscreen across both monitors.

I haven't used an ATI card in Linux for quite awhile (the headache is what drove me to buy Nvidia actually) so I hope this isn't totally irrelevant and helps at least somewhat.

---

