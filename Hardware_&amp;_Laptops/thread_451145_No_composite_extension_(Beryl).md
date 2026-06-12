---
title: "No composite extension (Beryl)"
date: 2007-05-22
forum: Hardware &amp; Laptops
---

### Post by Bakudan on 2007-05-22
I've read a lot about this in the past few days but can't seem to find quite what I'm looking for. I just installed Feisty on my laptop with an ATI Radeon Mobility 9600 card and I *thought* I had everything installed correctly.

When I run...

```
$fglrxinfo
    display: :0.0  screen: 0
    OpenGL vendor string: ATI Technologies Inc.
    OpenGL renderer string: MOBILITY RADEON 9700
    OpenGL version string: 2.0.6334 (8.34.8)
```


```
$glxinfo | grep direct
   direct rendering: Yes
```


But when I call beryl-manager it throws an error (as seen below.)

```
$ beryl-manager
    **************************************************************
    * Beryl system compatiblity check                            *
    **************************************************************
    Detected xserver                                : AIGLX
    Checking Display :0.0 ...
    Checking for XComposite extension               : failed
    No composite extension
    beryl: No composite extension
```

What did I break?

---

### Post by psayre23 on 2007-05-24
I found a solution that worked for me. I have a 9700 with the same problem. I found it here. [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

The heart and soul of it is to add this line to your xconf.

Section "Extensions"
Option "Composite" "false"
EndSection

The other thing I did was changed the session I logged into. That seemed to work. Good luck!

---

