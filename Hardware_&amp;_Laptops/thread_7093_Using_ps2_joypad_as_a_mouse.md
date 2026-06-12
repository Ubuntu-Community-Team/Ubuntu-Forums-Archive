---
title: "Using ps2 joypad as a mouse"
date: 2004-12-04
forum: Hardware &amp; Laptops
---

### Post by zeik on 2004-12-04
hi, 
How can I configure Xfree to use my ps2 controller as a mouse instead of using my 
mouse.. can I bind each controller button to different commands?\




Thanks 
Nathan

---

### Post by Knoeki on 2007-05-12
Sorry for reviving an old topic (again..>.>) but I'd like to know if this is possible aswell... (heh, and I thought I was the only one with this idea o.o)

---

### Post by sabrewolf2006 on 2007-05-12
I'd be interested in this one too..
as far as I can tell, the xserver-xorg-input-joystick driver is unmaintained..
I have tried calling the module to control the pad in xorg.conf like so:
```
Section "InputDevice"
    Identifier     "PlayStation Pad"
    Driver         "joystick"
    Option      "Device" "/dev/input/js0"
    Option      "CenterX"       "128"
    Option      "CenterY"       "128"
    Option      "MinX"          "0"
    Option      "MaxX"          "255"
    Option      "MinY"          "0"
    Option      "MaxY"          "255"
    Option      "Delta"         "8"
    Option      "Timeout"       "20"
    Option      "DebugLevel"    "0"    
EndSection
```
but the system just unloads the module before the server starts:
```

(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "SyncMaster"
(**) |   |-->Device "NVIDIA Corporation NV34 [GeForce FX 5500]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "PlayStation Pad"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
--snip--
(II) LoadModule: "joystick"
(II) Loading /usr/lib/xorg/modules/input//joystick_drv.so
(II) Module joystick: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) UnloadModule: "joystick"
(II) Unloading /usr/lib/xorg/modules/input//joystick_drv.so
(EE) Failed to load module "joystick" (out of memory, 136265776)

```
The out of memory error just relates to some of the config options that I added, it doesn't appear if they're not there, it just unloads..
So unfortunately.. unless someone picks up the driver and gets it back into a working state, using the pad is a no go :(

---

### Post by Knoeki on 2007-05-12
it would be a pitty if this would be abandoned... I mean.. it would be awesome to use a pad as a mouse... 


...I should start learning python...>.>

---

### Post by sabrewolf2006 on 2007-05-24
Definitely! :D
I always figured I would use it rather like a remote for example:
D-pad = cursor
L1 = left click
L2 = Right click
L3 = Wheel Click (jiggle to roll wheel)
R1 = Skip track on <insert media player here>
R2 = Skip backwards on <insert media player here>
R3 = ?? <jiggle to ??> (would be awesome to have effect like sweep for scanning round tracks/vids)
Triangle = switch to Browser
Square = switch to GOK or Dasher
Circle = 'enter'
Square = 'Scale' on Beryl
Select/Select = Lock Screen
Start = 'switch to Deskbar/affinity'

any other configs people would like to share?

---

### Post by ksenos on 2008-02-29
I am looking for the same thing here. Has anyone tried this?
[http://sourceforge.net/projects/joymouse-linux]("http://sourceforge.net/projects/joymouse-linux")

---

### Post by millie95 on 2008-05-01
joymouse-linux works. The X driver does not seem to work yet.

To use joymouse, add this to /etc/X11/xorg.conf:

Section "InputDevice"
        Identifier      "Joystick"
        Driver          "mouse"
        Option          "Protocol"      "ExplorerPS/2"
        Option          "Device"        "/dev/joymouse"
        Option          "SendCoreEvents"        "true"
        Option          "ZAxisMapping"  "4 5 6 7"
EndSection

and add
        InputDevice     "Joystick"

to Section "SeverLayout"

Also maybe add

Section "ServerFlags"
        Option "AllowMouseOpenFail" "true"
EndSection


Then run joymouse
I also installed joystick calibration to calibrate the joystick
I'm using XBOX 360 controller

---

