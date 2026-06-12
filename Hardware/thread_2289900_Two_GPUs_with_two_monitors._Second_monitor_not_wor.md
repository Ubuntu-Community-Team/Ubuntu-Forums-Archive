---
title: "Two GPUs with two monitors. Second monitor not working"
date: 2015-08-07
forum: Hardware
---

### Post by aki199 on 2015-08-07
So, I'm on Ubuntu 14.04 LTS
My first GPU - XFX R9 295x2
Second GPU - Radeon 7950 Twin Frozrz III
Two samsung monitors - S22D300 and S22C300
S22C300 is connected to XFX R9 295x2 and is working fine, as it used to.
I hooked up Radeon 7950 to the other monitor and expected Ubuntu to detect it but had no luck...
Now, when I run **lspci | grep VGA**
> 03:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Vesuvius [Radeon R9 295X2]
05:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti PRO [Radeon HD 7950/8950 OEM / R9 280]

Tried editing **xorg.conf** and adding
> Section "Device"
    Identifier             "Screen1"
    Driver                 "fglrx"
    BusID                  "PCI:5:0:0"
EndSection

PCI:5:0:0 - is the port for Radeon 7950 - no luck.

Also, when I go to **All Settings>Displays **and click **Detect Displays**, it does nothing.

Basically I've tried a few things without any progress.
I'd appreciate any help.

---

### Post by gordintoronto on 2015-08-08
I don't follow the AMD GPU product line, but most graphics cards have two (or more) outputs these days. Have you tried connecting both monitors to the same video card?

---

