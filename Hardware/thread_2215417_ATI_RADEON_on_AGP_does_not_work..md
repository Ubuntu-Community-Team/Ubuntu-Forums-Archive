---
title: "ATI RADEON on AGP does not work."
date: 2014-04-06
forum: Hardware
---

### Post by DidierDrigbi on 2014-04-06
Hi,

To begin with, I am new Ubuntu user. I moved from the Win XP and felt in love with the Linux family straight away.
But I faced hardware problem with graphics card and I will be very gratefull if you help me to solve it.

My ubunutu version: **12.04.04 LTS** (all updates installed during installation +those installed after the installation process).
**Please, don't try to encourage me to move to the newest version. I know it does exist, but I don't want it, cause not everything is properly translated and fully stable.**

My graphics card: **ATI RADEON HD4670 AGP (8X). **
My processor: Intel Pentium 4 2.8 Ghz Hyper-Threating (I read that disabling hype-threating may help, but it doesn't).

_**PROBLEM:**_
My graphics card after system installation appears to be "Unknown", "Interface: Standard".
I tried to enable the 3D acceleration by installing the driver from the AMD site. No go (Card not supported). 
So I tried to install fglrx (propierity). 

After installation of the fglrx and fglrx-amdcccle i tried to configure the xorg.conf automatically:
```
$ sudo aticonfig --initial
```
 it says: no supported adapters found.

I checked the bus ID 
```
$ lspci | grep VGA
```
and tried to create the xorg.conf manually
```

$ sudo gedit /etc/X11/xorg.conf
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
    Option      "AGPMode" "4"
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

but the system does not boot this way (says that it must run in low settings but doesn't allow me anywhere but into console. So i removed the driver from the console (apt-get remove, rm xorg.conf), and now it boots.

I have no idea how to enable 3D acceleration in this card. 
Would you be so kind and help me with this?

---

### Post by Yellow Pasque on 2014-04-06
It's probably already enabled (or at least it was until you tried to install the proprietary driver). You got hit with the n00b bug:
[https://bugs.launchpad.net/ubuntu/+bug/946620](https://bugs.launchpad.net/ubuntu/+bug/946620)

---

### Post by DidierDrigbi on 2014-04-06
This was helpful, thank you. I re-installed the whole system to clean all the mess and on a clean installation, I installed mesa-utils. Now, it recognises my card as Gallium 0.4 on AMD RV730. Is that correct, does it mean i have 3D acceleration? Becasue I there is no xorg.conf file.

---

### Post by Yellow Pasque on 2014-04-06
Yes, "Gallium 0.4 on AMD RV730" is correct. xorg.conf is usually not needed nowadays.

Please mark thread solved.

---

### Post by DidierDrigbi on 2014-04-06
Thank you very much, your help was brilliant and, what is very important, you responded quickly.
Thanks once more, thread marked.

---

