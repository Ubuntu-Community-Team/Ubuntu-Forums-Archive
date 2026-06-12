---
title: "X not starting after installing 2nd VGA"
date: 2009-02-20
forum: Hardware
---

### Post by ultravox on 2009-02-20
Hi!
I'm a noob just using linux for some months and learning every day.

I've a fresh install of ubuntu 8.10 in a asus M3N78-EM with onboard graphics(nvidia 8300). All updates installed and nvidia driver selected.

If I only use onboard graphics, x runs OK.
If I add a nvidia 6600GT X will not start.

dpkg-reconfigure xserver-xorg doesn't display video driver configuration.

lspci list both VGA.

I kindly ask this amazing community help to get x runing.

---

### Post by taurus on 2009-02-20
Go into the BIOS and turn off the onboard graphic card.

---

### Post by ultravox on 2009-02-20
sorry, forgot to mention that i want both runing until I get my new TV by Summer time.

Onboard doesn't have s-video out.

This motherboard has a hybrid sli mode to save energy. I would like to use it.

I can boot and use X with both VGA individually, but can't get both.

---

### Post by mckeja on 2009-02-20
> **ultravox said:**
> sorry, forgot to mention that i want both runing until I get my new TV by Summer time.

Onboard doesn't have s-video out.

This motherboard has a hybrid sli mode to save energy. I would like to use it.

I can boot and use X with both VGA individually, but can't get both.

The X config file (/etc/X11/xorg.conf) is very minimal with the default install. The issue I ran into with two video cards was that X didn't know which one to initialize first, so it promptly failed. What I had to do was manually edit the Device section to add a BusID line. Since both my cards are Nvidia, I then used the Nvidia X Server Settings application to add the second device/monitor. You probably won't be able to do it this way since you have two differing video cards. 

However, you should have no problem doing it all manually. I've included a snip of my xorg.conf to give an example. The important lines are the BusID lines. These relate to the information you find from the lspci command. 
Example:

```
wolf@n-star:~$ lspci | grep nVidia
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)
04:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)
```

These translate into the following Device sections in /etc/X11/xorg.conf:

```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
    BusID          "PCI:4:0:0"
EndSection
```


You will also need two Monitor sections and two Screen sections. Examples are taken, again, from my xorg.conf file and are not necessarily representative of your system:

```
Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Proview Rad-7gs"
    HorizSync       30.0 - 80.0
    VertRefresh     55.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "BenQ T701"
    HorizSync       31.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```


PS: And if I could figure out why all my posts have a thumbs-down icon... *sigh*

---

### Post by ultravox on 2009-02-27
Thx.

I'll try it when possible.

Cheers

---

