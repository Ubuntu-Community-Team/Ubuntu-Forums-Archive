---
title: "Cannot use Gnome 3D when xorg is configured for 2 AMD graphics cards"
date: 2013-04-23
forum: Hardware
---

### Post by mark1977 on 2013-04-23
Hi,
I have 2 AMD HD7*** series cards in my machine running 12.04. The fglrx driver in the repos failed to work when I installed the second card. I have tried purging and reinstalling many times (Ubuntu hangs during boot at the point "stopping sytem V runlevel compatability".
Then I tried to install the AMD driver directly from the manufacturer's website, but this did not correctly install the catalyst control center. This was recommended here:[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
 So I followed the wiki instructions instead:
[http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx/129200#129200](http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx/129200#129200)
i.e. to build my own package instead and install these. After doing this and running
```
sudo aticonfig --initial -f
```
this worked, it enabled me to use Ubuntu 3D fine but this did not configure x to use the 2nd graphics card. In order to do that, you need to run

```
sudo aticonfig --initial -f --adapter=all
```
instead. This modifies xorg.conf to allow for the 2nd card. Now that allows me to see both cards with fglrxinfo
```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 7900 Series 
OpenGL version string: 4.2.12002 Compatibility Profile Context 9.012



display: :0.0  screen: 1
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 7900 Series 
OpenGL version string: 4.2.12002 Compatibility Profile Context 9.012


```
and with clinfo (I want to do opencl).

However I can no longer log into unity 3D or cinnamon or any other 3D desktops (I get routed automatically to gnome classic with an extra 4 panels and notification areas appearing).

It seems I can switch from either
(a) 3d working but only 1 card seen
or
(b) 3d not working but both cards seen
when I run aticonfig without --adapter=all and with.
For comparison, here are my xorg.conf files for the case of```
aticonfig --initial
```:
```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection


```

and the case of ```
aticonfig --initial --adapter=all
```:

```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
    Screen         "aticonfig-Screen[1]-0" RightOf "aticonfig-Screen[0]-0"
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[1]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[1]-0"
    Driver      "fglrx"
    BusID       "PCI:2:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[1]-0"
    Device     "aticonfig-Device[1]-0"
    Monitor    "aticonfig-Monitor[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection


```

Can anyone see why a difference in these xorg.conf's will switch me from being able to use 3D desktops to not being able to?

Thanks,

Mark

---

### Post by mark1977 on 2013-06-10
bump :)

I would really like to be able to use 2 graphics cards with gnome!

---

### Post by Yellow Pasque on 2013-06-10
What version of fglrx did you install? If you just copied/pasted commands, then you probably installed an older version.

---

### Post by mark1977 on 2013-06-11
I first installed via apt-get, then I tried manual installation of the proprietary catalyst drivers from the AMD website, then I followed the advice in the Ubuntu documentation:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

then I tried creating my own package :

[http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx/129200#129200](http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx/129200#129200)

All worked fine for a single graphics card. None worked for 2 cards...

I am sorry I do not remember the version, it would have been whatever was in the repos at the time of my first post?

---

