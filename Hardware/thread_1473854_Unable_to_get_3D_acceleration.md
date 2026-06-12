---
title: "Unable to get 3D acceleration"
date: 2010-05-05
forum: Hardware
---

### Post by Braik on 2010-05-05
Hello every body,

I have installed Lucid recently but I have a (big) issue with my ATI graphic card, here are some outputs of this problem:

```
lspci | grep VGA
```Output:
```
05:00.0 VGA compatible controller: ATI Technologies Inc RV515 PRO [Radeon X1300/X1550 Series]
```So I have a Radeon X1300, which I think (checked on other forums) is not more supported by ATI on Linux. By the moment I have correct screen resolution and display, but when I try to install something that uses OpenGL it does not work, to illustrate this:
```
glxinfo
```Output:
```
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Segmentation fault

```

Can somebody give me a solution, or it is impossible to fix this

Thanks a lot

Braik

---

### Post by Yellow Pasque on 2010-05-05
Try reinstalling the packages: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

---

### Post by Braik on 2010-05-07
Thanks, I will try this between tonight and tomorrow. Not at home now ;)

---

### Post by Braik on 2010-05-08
So I did what you proposed me but it still does not work, when I put:

glxinfo

Output

```
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

```

What to do ? :(

---

### Post by Yellow Pasque on 2010-05-08
I'm not really sure what else to tell you. If you can reproduce the same thing with a Lucid LiveCD, then you know it's a problem with Ubuntu, and you can file a bug report.

One other thing you could try is the xorg-edgers PPA: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by Braik on 2010-05-09
Hi

I am wrinting you from the live CD, and 3D seems to work.

Now, since the live CD is a 32bit version (no live CD with 64) and I have a 64 version installed (upgrade from Karmic) don't know what to think, it is a problem of the installation? or it is a problem from the 64b version?

---

### Post by Braik on 2010-05-09
So, I have the solution to my problem, it came with the upgrade (or maybe some odd manipulation I did), I have just made a clean install of my system (64bits) and the 3D came back.

Thanks a lot

---

