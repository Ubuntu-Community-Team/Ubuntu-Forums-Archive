---
title: "Problem installing nvidia driver"
date: 2009-10-28
forum: Hardware
---

### Post by elnacho12 on 2009-10-28
Hi all,

    I'm not being able to install the nvidia 180 driver for my GeForce 6200 on Ubuntu 9.04 - Jaunty Jackalope.
> 
inieto@inieto-desktop:~$ uname -a
Linux inieto-desktop 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:24 UTC 2009 i686 GNU/Linux

inieto@inieto-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

inieto@inieto-desktop:~$ glxinfo 
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
...
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
...
Xlib:  extension "GLX" missing on display ":0.0".
3 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Segmentación Fault


I've tried with:
- System -> Administration -> Hardware, activating the 180 nvidia driver
- checking the xorg.conf:
> 
Section "Module"
  Load  "glx"
  Disable "dri2"
EndSection
...
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

- tried to install the 185 new driver (attached is the installation log file, which displays some errors)

The xorg log shows in different tries the following:
> 
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

> 
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
dlopen: /usr/lib/xorg/modules/extensions//libglx.so: undefined symbol: _nv000046gl
(EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (loader failed, 7)


The sympthom is that after the Ubuntu logo loading black screen which hides the boot sequence, when gdm starts, the system hangs. It doesn't respond to the keyboard.
I have then to reboot in safe mode and restore the X, which makes my xorg load with the basic "nv" driver.

Any ideas?

Thanks in advance,

Ignacio

---

### Post by compiledkernel on 2009-10-28
hrmmm...

[http://gwos.org/udsf/doku.php/hardware:nvidia](http://gwos.org/udsf/doku.php/hardware:nvidia)

look over that guide and see if it gives any insight.

---

### Post by elnacho12 on 2009-10-29
> **compiledkernel said:**
> hrmmm...

[http://gwos.org/udsf/doku.php/hardware:nvidia](http://gwos.org/udsf/doku.php/hardware:nvidia)

look over that guide and see if it gives any insight.

Thanks, I've tried all the steps from the document but still getting the same results.
Attached are the documents that the nvidia-bug-report.sh script threw.
Any other ideas?

Ignacio

---

### Post by mercury00 on 2010-02-11
elnacho12, did you ever get this working?

---

