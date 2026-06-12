---
title: "Nvidia gforce 9600 gt : low performance ."
date: 2008-11-02
forum: Hardware
---

### Post by szadek_ on 2008-11-02
Hello people , i have a hp laptop dv5-1050ep with a nvidia 9600 gt graphic card , and , in ubuntu 8.04 with gnome , works fine , i installed the restricted driver .But i installed kde 4 ( kubuntu desktop ) , and the performance ( graphical ) is very poor , its slow on the minimize and maximize options , and overall it runs slow on kde 4 ambient .

Is this a bug ( unsolved ? ) or it needs any configuration ?? 

Thanks in advance for the help .

---

### Post by robert114 on 2008-11-02
you might have a look here:
[http://www.nvnews.net/vbulletin/showthread.php?t=118088](http://www.nvnews.net/vbulletin/showthread.php?t=118088) 

Below are some tweaks i made in Xorg.conf 
Rememer this is at your onw risk!

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    Option         "PixmapCacheSize" "1000000"
    Option         "AllowSHMPixmaps" "0"
    Option         "RenderAccel" "True"
    Option         "NoRenderExtension" "False"
    Option         "AllowGLXWithComposite" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "DamageEvents" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---

### Post by szadek_ on 2008-11-04
Is there anyone who tested the latest 8.10 , with this graphical card and could tell me how it behaves ? is the latest version of ubuntu shipping the latest nvidia driver ?? 

Any help is welcome , thanks in advance =) .

---

### Post by robert114 on 2008-11-04
Ubuntu shipes the latest driver (version 177.80)

---

