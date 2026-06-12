---
title: "After install nvidia driver gdm3 won't load (blank screen)"
date: 2020-07-31
forum: Hardware
---

### Post by dukercs on 2020-07-31
Good morning!

I've upgraded my system from ubuntu 16 LTS to 18.04 LTS and now to 20.04 LTS. I really want to believe that's a good practice. So no I don't tried to reinstall, yet.


I've installed the nvidia with this command:
```
sudo apt-get install nvidia-driver-418
```

My journalctl after tried to prime-select nvidia and a systemctl restart gdm3 

[https://paste.ubuntu.com/p/t7vKhRBt9H/](https://paste.ubuntu.com/p/t7vKhRBt9H/)


This is my /etc/X11/xorg.conf

```
egrep -v "^#|^$" xorg.conf
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
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
        # Monitor Manufactured week 35 of 2011
        # EDID version 1.3
        # Digital Display
    Identifier     "Monitor0"
    VendorName     "CMN"
    ModelName      "Unknown"
    DisplaySize     310    170
    Gamma           1
    ModeLine       "Mode 0" 69.30 1366 1414 1446 1466 768 769 773 788 -hsync -vsync
    Option         "DPMS" "false"
EndSection
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
EndSection
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1366x768"
    EndSubSection
EndSection

```

Packages installed with nvidia

```


dpkg -l "*nvi*"|egrep ^ii
ii  libnvidia-cfg1-440:amd64         440.100-0ubuntu0.20.04.1 amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-440             440.100-0ubuntu0.20.04.1 all          Shared files used by the NVIDIA libraries
ii  libnvidia-compute-440:amd64      440.100-0ubuntu0.20.04.1 amd64        NVIDIA libcompute package
ii  libnvidia-compute-440:i386       440.100-0ubuntu0.20.04.1 i386         NVIDIA libcompute package
ii  libnvidia-decode-440:amd64       440.100-0ubuntu0.20.04.1 amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-440:i386        440.100-0ubuntu0.20.04.1 i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-440:amd64       440.100-0ubuntu0.20.04.1 amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-440:i386        440.100-0ubuntu0.20.04.1 i386         NVENC Video Encoding runtime library
ii  libnvidia-extra-440:amd64        440.100-0ubuntu0.20.04.1 amd64        Extra libraries for the NVIDIA driver
ii  libnvidia-fbc1-440:amd64         440.100-0ubuntu0.20.04.1 amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-440:i386          440.100-0ubuntu0.20.04.1 i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-440:amd64           440.100-0ubuntu0.20.04.1 amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-440:i386            440.100-0ubuntu0.20.04.1 i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-440:amd64         440.100-0ubuntu0.20.04.1 amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  libnvidia-ifr1-440:i386          440.100-0ubuntu0.20.04.1 i386         NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  nvidia-compute-utils-440         440.100-0ubuntu0.20.04.1 amd64        NVIDIA compute utilities
ii  nvidia-dkms-440                  440.100-0ubuntu0.20.04.1 amd64        NVIDIA DKMS package
ii  nvidia-driver-418                430.50-0ubuntu3          amd64        Transitional package for nvidia-driver-430
ii  nvidia-driver-430                440.100-0ubuntu0.20.04.1 amd64        Transitional package for nvidia-driver-440
ii  nvidia-driver-440                440.100-0ubuntu0.20.04.1 amd64        NVIDIA driver metapackage
ii  nvidia-kernel-common-440         440.100-0ubuntu0.20.04.1 amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-440         440.100-0ubuntu0.20.04.1 amd64        NVIDIA kernel source package
ii  nvidia-prime                     0.8.14                   all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                  440.82-0ubuntu0.20.04.1  amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-440                 440.100-0ubuntu0.20.04.1 amd64        NVIDIA driver support binaries
ii  xserver-xorg-video-nvidia-440    440.100-0ubuntu0.20.04.1 amd64        NVIDIA binary Xorg driver

```

Thanks for any help!!!! I'm going crazy about this..... I just want to play a game :'(

---

### Post by CatKiller on 2020-07-31
```
jul 31 09:48:14 notelnx /usr/lib/gdm3/gdm-x-session[9376]: (II) NVIDIA(0): Validated MetaModes:
jul 31 09:48:14 notelnx /usr/lib/gdm3/gdm-x-session[9376]: (II) NVIDIA(0):     "NULL"
```

This is likely the issue. You could rename your xorg.conf to something else, so that you aren't trying to use that ModeLine that you've specified for some reason.

---

### Post by dukercs on 2020-07-31
> **CatKiller said:**
> ```
jul 31 09:48:14 notelnx /usr/lib/gdm3/gdm-x-session[9376]: (II) NVIDIA(0): Validated MetaModes:
jul 31 09:48:14 notelnx /usr/lib/gdm3/gdm-x-session[9376]: (II) NVIDIA(0):     "NULL"
```

This is likely the issue. You could rename your xorg.conf to something else, so that you aren't trying to use that ModeLine that you've specified for some reason.

Solved!!

Thank you !!! Thank you

I've been tried to solve this for the last 6 days since the upgrade.... THANK YOU Now I'm going to install steam!:)

---

