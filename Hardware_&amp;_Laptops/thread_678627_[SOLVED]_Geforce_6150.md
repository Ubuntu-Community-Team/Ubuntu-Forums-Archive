---
title: "[SOLVED] Geforce 6150"
date: 2008-01-26
forum: Hardware &amp; Laptops
---

### Post by qhimq on 2008-01-26
HI

I've got a big problem with my driver.

I've read everything there is about howtos of installing various drivers for it.

===What happened===
I wanted a new version of my working driver that was installed from the time I installed ubuntu.

So I downloaded  NVIDIA-Linux-x86_64-169.07-pkg2.run and ran it...ever since then the nvidia driver will not load. Instead the vesa generic one does.

I've done envy too many times to remember.  I've done the clean all nvidia drivers opinion, i've changed the xorg.conf to nvidia...nothing.  I've done the restricted drivers manager, I've checked out the package manager with anything that has nvidia in the name.

wtf happened? wtf can I do ?        I really don't want to wipe my computer, but it seems like the only choice.

---

### Post by Z_o-s-o on 2008-01-26
You should just use the driver from the restricted drivers manager.

I have a 6150 and it works fine for compiz and all that.

You should be able to use envy to remove any Nvidia drivers, and then go into the RDM and use the one thats there.

Z_o-s-o

---

### Post by qhimq on 2008-01-26
that is what i've precisely done multiple times.  its very frustrating that its not working.

also if it helps, i get many messages after the ubuntu load screen saying:

"hda: disk not ready for command"


I usually get this message, however sometimes it doesn't pop up.  Every time it does pop up though sound juicer comes up saying a have a new disk inserted.  I don't have anything in my cdrom drive.

---

### Post by canthus13 on 2008-01-26
I had the same problem... I just gave up and used Envy.  It worked perfectly...

---

### Post by qhimq on 2008-01-26
yeah...tried envy and it doesn't do its supposed work.


Here is my xorg log attached.  Its really weird.  I get this log from running the nv driver.  It appears as though it runs parts of the nvidia driver that envy installed (169.09).  Now everything is running pretty fast too, which what was most important.  However 3d accel is not working.

my glxinfo says:

name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 16 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 16 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None


Here is the important part of my xorg.conf:


Section "Device"
    Identifier     "nVidia Corporation C51 [Geforce 6150 Go]"
    Driver         "nv"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation C51 [Geforce 6150 Go]"
    Monitor        "Generic Monitor"
    DefaultDepth    16
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1280x800" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
	Option		"Composite"	"Disable"
EndSection

Section "Module"
    Load           "glx"
EndSection

---

### Post by canthus13 on 2008-01-26
Did you have envy remove everything first?

One other note - I'm running 169.07, not .09, and that may be the difference.

---

### Post by qhimq on 2008-01-28
Yeah I had envy remove everything first.


I solved the problem.

I found that I didn't have my Xorg server updated.  So I updated it, and found:

NVIDIA-Linux-x86_64-169.09-pkg2.run

ran it again, after cleaning with envy once again.

changed my xorg.conf to:

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
    InputDevice    "EETI" "SendCoreEvents"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "EETI"
    Driver         "egalax"
    Option         "Device" "/dev/usb/hiddev0"
    Option         "Parameters" "/etc/egalax.cal"
    Option         "ScreenNo" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation C51 [Geforce 6150 Go]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation C51 [Geforce 6150 Go]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1280x800"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection


```


My complete setup:

HP tx1000
gusty 64

working touchscreen, wireless, sound, all buttons, webcam, usb, 6150 (idle at 70C really freakin hot on graphics intense programs  > 95C)

---

