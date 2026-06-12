---
title: "need help with laptop"
date: 2007-08-05
forum: Hardware &amp; Laptops
---

### Post by karlpox on 2007-08-05
Im using ATI Raedon Mobility X1300 how do I install drivers? and how do i use 1024x768 resolution? and every time i click on my Compiz Fusion icon nothing happens? need help I'm very noob & new with Ubuntu.

---

### Post by ugm6hr on 2007-08-05
Generally, for ATI cards - you just go to Restricted Drivers Manager (in System Menu) and select the ATI accelerated graphics driver.  Then the driver is installed.

Give it a try.

In order to get different resolutions - that may work - or you *may* have to edit xorg.conf.

---

### Post by karlpox on 2007-08-05
ok i think i installed my Video Card's driver already since i can go beyond 800x600.

but under xorg.conf

```
Section "Device"
	Identifier  "Generic Video Card"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection
```

isnt this suppose to change and become something like ati??

and if i key in fglrxinfo this is the output

```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
```

---

### Post by ugm6hr on 2007-08-05
You haven't enable the restricted drivers - since xorg still refers to "vesa" - which is the "safe" driver.

Presumably - you installed from the Safe Graphics mode?  Or was it an AlternateCD install?

Either way - this will probably help (although I haven't had to use it):
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

When you get it sorted - don't forget to post your updated (fully functional) xorg file to the link in my signature.

---

### Post by karlpox on 2007-08-05
tried that and now it says

```
display: :0.0 screen:0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1300
OpenGL version: 2.0.6650 (8.39.4)
```

and under xorg.conf it says

```
Section "Device"
Identifier "Generic Video Card"
Driver "fglrx"
Option "VideoOverLay" "on"
Option "VideoOverLay" "off"
BusID "PCI:1:0:0"
EndSection

Section "Device"
Identifier "aticonfig-Device[0]"
Driver "fglrx"
Option "VideoOverLay" "on"
Option "OpenGLOverLay" "off"
EndSection
```

is this good??

---

### Post by ugm6hr on 2007-08-05
> **karlpox said:**
> 
is this good??

Probably - it means you are now using the restricted drivers, which give better screen resolution options, and various other options (apparently).

Do a reboot (or restart X with Ctrl_alt-Backspace), and it should start using the new driver.

If it is - you should be able to use Compiz-Fusion, assuming your graphics card is up to it.

You'll have to do a bit more research, I'm afraid - because I don't use Compiz-Fusion.

---

### Post by karlpox on 2007-08-05
i tried installing compiz fusion but after typing compiz --replace nothing happens though. Is Ati mobility X1300 comaptible with compiz?

---

### Post by karlpox on 2007-08-05
i tried re installing ubuntu and now my resolution is back to 800x600 again.:confused::confused:

---

### Post by ugm6hr on 2007-08-05
> **karlpox said:**
> i tried re installing ubuntu and now my resolution is back to 800x600 again.:confused::confused:

Every time you (re)install - the xorg.conf file will reconfigure to the default.

So you will have to follow the same instructions as previously to use the fglrx driver.

---

