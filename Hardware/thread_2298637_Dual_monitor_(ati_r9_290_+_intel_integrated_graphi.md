---
title: "Dual monitor (ati r9 290 + intel integrated graphics) proprietary driver issues"
date: 2015-10-12
forum: Hardware
---

### Post by Psy8cho on 2015-10-12
Hi,

I am running Kubuntu 15.04 and have trouble setting up the proprietary drivers with my dual monitor setup.

I use the ATI/AMD Radeon R9 290 graphics card for the main screen and I use Intel Integrated Graphics (mobo: MSI H97 GUARD-PRO) for the second screen. I can't connect the second screen to my graphics card because it needs an analog signal, or I would need to buy an active converter.

The problem is when using the proprietary drivers from ATI/AMD: fglrx or fglrx-updates (don't think there is a version difference of the catalyst contorl center between the two right now). My second monitor does not work. At first, when changing from the open source drivers from xorg, my computer would not even boot anymore and get stuck at the splash screen of kubuntu. I fixed this using the command
```
sudo aticonfig --initial 
```
in recovery mode got it to boot, however on my second monitor I keep seeing the kubuntu splashscreen nor can I move any windows to that screen. It's just unusable. The second option in fixing this problem is to disable the integrated graphics in the UEFI bios.

To be clear the second screen does work with the opensource drivers of xorg: xserver-xorg-video-ati. In the driver manager of kubuntu.

Some debug information, contents of xorg.conf in /etc/X11/xorg.conf:
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
I have been searching and trying some solutions all day, but my linux knowledge is still limited and could not fix it by myself. The main things were reinstalling the drivers and using 'dpkg' in recovery mode to repair and delete broken packages. Editing the GRUB boot commands using 'e' while in the GRUB boot menu, with things like nomodeset, radeon.modeset=0 etc. Don't know if I did that right though.

Anyone here who can help me fix this issue?

Thnx!

---

### Post by Psy8cho on 2015-10-17
Anyone? Do I need to post more debug information? Or places to look/things to try?

---

