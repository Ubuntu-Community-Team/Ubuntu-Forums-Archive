---
title: "More intel GL960 Problems"
date: 2009-06-03
forum: Hardware
---

### Post by pawnrocket on 2009-06-03
[CENTER]Ubuntu Version : 9.04
Kernel Version : 2.6.29-020629-generic

Problem : Cant enable 3D graphics 
          2D Graphics are choppy
[/CENTER]

output of lspci

```
r3l1c@r3l1c:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

```

xorg.org settings

```
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection


```

I have also ran ```
sudo dpkg-reconfigure -phigh xserver-xorg

``` hoping reconfiguring would help... 

Any help would be appreciated.

---

### Post by pawnrocket on 2009-06-03
bump

---

