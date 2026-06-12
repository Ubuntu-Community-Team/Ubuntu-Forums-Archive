---
title: "kompmgr/xcompmgr performance hit (possibly after kernel/nvidia upgrades?)"
date: 2008-08-30
forum: General Help
---

### Post by mrowth on 2008-08-30
I'm using kompmgr now. Never got Compiz to run on Mint 4.0 - based on Gutsy - although it used to work well. kompmgr gives me fading, shadows, and transparency. It's enough for that extra sense of "depth".

Now, though... resizing windows has become incredibly laggy/choppy. (Menu fade-ins/outs etc. are as fast as before.) Glxgears FPS dropped to ~1100, used to be 3400-3500 IIRC (too little? Dunno). It's still about 3300 without kompmgr running. This is in KDE 3.5.8. In Window Maker it's ~2900 without kompmgr or xcompmgr and ~1100 with.

The slowdown happens even with xcompmgr with **no** features activated. 

Fonts also became smaller for some reason - possibly quite unrelated. 

The last things I remember installing:

VMware server (uninstalled again to make sure it's not it)
Kernel 2.6.22-15 generic and rt
Nvidia drivers 100.14.23 (necessitated by above), first through Envy, then through apt-get install nvidia-glx-new, not sure about the difference, results seem the same

Am using the same xorg.conf as before. Tried enabling "Composite" extension, no effect (can you tell I don't know what's what?). The Nvidia drivers are running. glxinfo says direct rendering: Yes. 

Does anyone have any ideas? All suggestions welcome*... I've finally got a mostly-running system (mostly: rt kernel grr), and this puts a dent in it...


xorg.conf:
 
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
    FontPath        "/var/lib/defoma/fontconfig.d/B"
    FontPath        "/usr/share/fonts/truetype/ttf-bitstream-vera"
    FontPath        "/var/lib/defoma/fontconfig.d/N"
    FontPath        "/usr/share/fonts/type1/gsfonts"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
    Load           "freetype"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "janny"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "AOC Spectrum7K"
    HorizSync       30.0 - 95.0
    VertRefresh     50.0 - 160.0
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "false"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "TwinView" "1"
    Option         "metamodes" "CRT-0: 1600x1200 +0+0, CRT-1: 1600x1200 +1600+0; CRT-0: NULL, CRT-1: 1280x1024 +0+0; CRT-0: NULL, CRT-1: 1280x960 +0+0; CRT-0: NULL, CRT-1: 1024x768 +0+0; CRT-0: NULL, CRT-1: 800x600 +0+0; CRT-0: NULL, CRT-1: 640x480 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

.xcompmgrrc (kompmgr uses it, xcompmgr itself doesn't seem to... makes sense...):

```
[xcompmgr]
Compmode=CompClientShadows
DisableARGB=false
FadeInStep=0.1
FadeOutStep=0.1
FadeTrans=true
FadeWindows=true
ShadowColor=0x000000
ShadowOffsetX=-22
ShadowOffsetY=-80
ShadowRadius=15
```




(*except "install Hardy"... last time I tried that I couldn't get DVDs to play, DVD drives were making disgusting grinding noises for a minute before even letting go of the disc... and I'm not so keen on fighting with Pulse... and if ACPI doesn't work I'm lost... and so on)

---

