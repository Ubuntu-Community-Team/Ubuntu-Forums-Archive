---
title: "3D acceleration not working (Radeon HD 4250)"
date: 2010-09-22
forum: Hardware
---

### Post by DoktorNo on 2010-09-22
Hi,

I know, that this is question more related to Debian forum (because I'm using Lenny 5 now), but since Ubuntu is based on Debian, then I think I could find a solution here. I also tried to run Ubuntu LiveCD (10.4) to check, if this hardware would ever work on Linux. It worked, however it was clear, that it demanded proprietary drivers for 3D acceleration.

I have a Gigabyte motherboard with ATI Radeon  HD 4250 gfx card on board.  "lspci -v | grep VGA" gives me following output:

```
Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
01:05.0 VGA compatible controller: ATI Technologies Inc Device 9715 (prog-if 00 [VGA controller])

```

I also have proprietary drivers installed properly (Catalyst 10.9), and my xorg.conf is dumped below:

```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "pl"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Monitor    "Configured Monitor"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

I can use 1080p resolution without any problem, however the 3D GLX support seems to be broken:

```
me@workstation:~$ glxgears
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  144 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  13
  Current serial number in output stream:  13

```

Also: scrolling in web-browsers or dragging a window works terrible slow, for such modern adapter. I wish, I could use GPU-accelerated Compiz...

---

### Post by DoktorNo on 2010-09-23
I analyzed Xorg.0.log, and it seems, that indeed fglrx is not loaded, hence acceleration is not working. modprobe fglrx gives me following error:

```

FATAL: Module fglrx not found.

```

Snippet from Xorg.0.log:

```

(WW) fglrx(0): ***********************************************************
(WW) fglrx(0): * DRI initialization failed                               *
(WW) fglrx(0): * kernel module (fglrx.ko) may be missing or incompatible *
(WW) fglrx(0): * 2D and 3D acceleration disabled                         *
(WW) fglrx(0): ***********************************************************

```

I tried to make a DEB package from ATI's Catalyst installer, but it failed:

```
cp: cannot stat `./usr/X11R6/lib64/modules/linux': No such file or directory
dh_install: command returned error code 256
make: *** [binary] Error 1
dpkg-buildpackage: failure: debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.xNgTvN

```

---

