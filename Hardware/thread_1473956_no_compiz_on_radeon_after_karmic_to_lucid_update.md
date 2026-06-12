---
title: "no compiz on radeon after karmic to lucid update"
date: 2010-05-05
forum: Hardware
---

### Post by krabunski on 2010-05-05
Hi,

starting the lucid lynx live cd gives me the compiz visual effects. If I upgrade the same system from karmic to lucid compiz won't work.
Trying to set Appearence>Visual Effects to Normal gives me "Desktop effects could not be enabled".
$ lspci -k
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
        Kernel driver in use: radeon
        Kernel modules: radeon

$ glxinfo 
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
3 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Segmentation fault

Help would be appreciated.

**Solved it:**
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch")

---

### Post by xtracool_protik on 2010-08-12
hey krabunski did it work for u?
I seem to have same issue with 4500 series card on my studio

---

### Post by krabunski on 2010-08-12
Solved it:
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

---

### Post by xtracool_protik on 2010-08-12
Hey thanks I'll try it and report

---

### Post by xtracool_protik on 2010-08-13
Hey that went pretty well I removed all fglrx stuff. And installed 10.7 ATI drivers (IMPORTANT needed to use sudo to get them installed and working properly).
 However still don't have rendering support and for some reason teamviewer stopped working (I was working on brother's laptop remotely)
 Well while working on one of friends laptop I did something really horrible. It just doesn't boot up (blank screen), no safe (recovery) mode nothing :confused:

---

### Post by xtracool_protik on 2010-08-13
I've posted thread about second computer here: [http://ubuntuforums.org/showthread.php?t=1552467](http://ubuntuforums.org/showthread.php?t=1552467)

---

