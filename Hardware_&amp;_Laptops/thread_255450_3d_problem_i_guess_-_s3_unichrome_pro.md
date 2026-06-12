---
title: "3d problem i guess - s3 unichrome pro"
date: 2006-09-11
forum: Hardware &amp; Laptops
---

### Post by katsolimon on 2006-09-11
i have S3 Graphics UniChromePro IGP on my packard bell. i have ubuntu 6.06.
i realized that there is a problem with 3d stuff but i really can not name the problem. screen resolution is fine, xorg via driver is installed.
i realized the problem when i tried to execute glxgears. it says
```
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
```

glxinfo says:
```
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
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Segmentation fault

```
screen saver also crashes :) that is another side effect.

i have searched almost all topics about via and unichrome so before you demand let me tell you what i have:

in the xorg.conf i have
```
Section "Device"
	Identifier	"VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
	Driver		"via"
	BusID		"PCI:1:0:0"
	Option "DisableIRQ"
	Option "EnableAGPDMA"
EndSection
******
Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection
```

i added the two options after searching the forum but it made no visible difference.

the installation of os was standard, i didnt run into any 3d related problems.

what can be the problem? i am sure the driver is fine cause many others are using this driver and say this is the most stable driver, so i dont want to install the openchrome driver. so what are your suggestions? how to solve this problem :)

---

### Post by 1smg on 2006-09-11
maybe "xserver-xorg-driver-via_+194-1_i386.deb"
from 
[http://www.kubuntu.de/forum/forum.php?req=derefer&url=http%3A%2F%2Fgamesplace.info%2Fopensource%2Fopenchrome%2Fdapper-binaries%2F](http://www.kubuntu.de/forum/forum.php?req=derefer&url=http%3A%2F%2Fgamesplace.info%2Fopensource%2Fopenchrome%2Fdapper-binaries%2F)

i've got a Packard Hell EasyNote R1100, works fine here

---

### Post by katsolimon on 2006-09-13
thanks for the reply, that driver did no good. i really dont think it is because of driver. i believe there is some configuration or something missing on X... any other suggestions?

---

