---
title: "Toshiba M200 Tablet Features"
date: 2010-10-20
forum: Hardware
---

### Post by bradburyn on 2010-10-20
Hello, I am new to the forums and am looking for some help. I understand there are posts out already about this but I cannot seem to get a straight set of instruction to get this working. After several reinstalls I still haven't found any luck. I have a Toshiba Portege M200 and have Ubuntu 10.10 installed, I need help setting up the rotation feature. I haven't seemed to have found any luck yet, if I could get some help on this I would appreciate it!!!

---

### Post by Favux on 2010-10-20
Hi bradburyn,

Welcome to Ubuntu forums!

First let's figure out what your video chipset is.  Enter in a terminal:
```
lspci | grep VGA
```

---

### Post by bradburyn on 2010-10-21
Favux, here is what I get

01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 32M/64M] (rev a1)

---

### Post by Favux on 2010-10-21
OK.  Have you installed the Nvidia proprietary driver?

What's your xorg.conf look like currently?  Do you have one?:
```
gedit /etc/X11/xorg.conf
```

On the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1") method 1 or 3 should work for you once we iron out video.

---

### Post by bradburyn on 2010-10-21
When I first installed Ubuntu I did install the proprietary driver. To my knowledge it should be installed on my system. The xorg.conf looks like this.....


Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
    Option        "RandRRotation"  "on"
EndSection

---

### Post by Favux on 2010-10-21
OK, with:
> Option "RandRRotation" "on"
you should be set.

Go to the Rotation HOW TO and pick method 1 or 3.  On method 3 I'm not yet sure the Lucid version of wacomrotate will install on Maverick but it's worth a shot.

Ask if you have questions.

---

### Post by bradburyn on 2010-10-21
Thanks, I will go give method 1 a shot, I have tried method 3 before and didn't quite get all the quirks out of it. I will let you know if I have any more questions. Thanks for your help!

---

