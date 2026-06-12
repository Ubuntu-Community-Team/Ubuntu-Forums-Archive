---
title: "[SOLVED] Ubuntu 8.1, Nvidia and multiple monitors"
date: 2008-11-06
forum: General Help
---

### Post by blis102 on 2008-11-06
Hello everyone,

I just upgraded to Ubuntu 8.1 and everything seemed to go smoothly other than when I restarted, my second monitor stopped working. I have 2 22" screens that were running off of the restricted Nvidia driver using TwinView. Now that the Xorg.conf file has been removed from ubuntu, I am struggling to figure out how to get TwinView working again.

If I go to "nvidia-settings" and click on the second monitor and turn on TwinView for it, it works. But when I logout or restart, the settings get lost. I have the restricted drivers installed.

I am wondering how I can force the display settings to stay so I don't have to change them every time I restart. Anyone know how to do this?

Thanks,
D

---

### Post by quazi on 2008-11-06
Try saving the nvidia-settings to a file in your home directory.  Then backup the old xorg.conf (in /etc/X11/) and replace it with the one just created.

---

### Post by blis102 on 2008-11-07
How do I save it to a file other than the xorg.conf file? Also, I have read that xorg.conf is no longer used, so what use would that have anyways?

---

### Post by quazi on 2008-11-07
My understanding is that the new Xorg version is trying to minimize the use of the xorg.conf file.  However, I'm not sure what this means in practice as I've used the same file for both Hardy and Intrepid.  The way to save it to another file is go to "X Server Display Configuration" and click on "Save to X Configuration File".  Then type in a file in your home directory (so you have write access) and click save.  Copy that over to /etc/X11/xorg.conf (after backing up of course).

---

### Post by blis102 on 2008-11-07
That's interesting about the xorg file, I'll have to try it out since my mouse is also busted. 

I have tried saving to xorg.conf in nvidia-settings but it crashes every time. Any idea why that would happen? I've ran it with and without sudo but it fails either way. 

Thanks, 
D

---

### Post by blis102 on 2008-11-15
So it seems to have worked now. I believe that I one of the updates I installed fixed the issue and now, starting nvidia-settings as root and changing my settings and clicking "Save to X file" works. Here is what I have for my screens in case it helps anyone in the future:

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "SCN GL-1920B"
    HorizSync       30.0 - 81.0
    VertRefresh     40.0 - 76.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-0: 1280x1024 +0+0, DFP-1: nvidia-auto-select +1280+0; DFP-0: 1280x960 +0+0, DFP-1: nvidia-auto-select +1280+0; DFP-0: 1152x864 +0+0, DFP-1: nvidia-auto-select +1152+0; DFP-0: 1024x768 +0+0, DFP-1: nvidia-auto-select +1024+0; DFP-0: 832x624 +0+0, DFP-1: nvidia-auto-select +832+0; DFP-0: 800x600 +0+0, DFP-1: nvidia-auto-select +800+0; DFP-0: 640x480 +0+0, DFP-1: nvidia-auto-select +640+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

