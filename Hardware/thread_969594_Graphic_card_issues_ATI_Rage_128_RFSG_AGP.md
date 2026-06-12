---
title: "Graphic card issues ATI Rage 128 RF/SG AGP"
date: 2008-11-03
forum: Hardware
---

### Post by Berduchwal on 2008-11-03
Hi
I have just tried to install 8.10 Ubuntu on old PC and run into problems with graphics.
Generated following outputs:
lspci -v 
```

01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 RF/SG AGP
Subsystem: ATI Technologies Inc Device 0008
Flags: bus master, stepping 66MHz, medium devsel, latency 64, IRQ 11
Memory at d4000000 (32-bit, prefetchable) [size=64M]
I/O ports at c000 [size=256]
Memory at d9000000 (32-bit, non-prefetchable) [size=16k]
[virtual] Expansion ROM at d8000000 [disabled] [size=128k]
Capabilities: <access denied>
Kernel modules: aty128fb

```
/etc/X11/xorg.conf
```

Section "Device"
Identifier "Configured Video Device"
Option "UseFBDev" "true"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Video Device"
Device "Configured Monitor"
EndSection

```

startx
```

(EE) Unable to find a valid framebuffer
(EE) R128(0): Failed to open framebuffer device, consult warnings and/or errors above for possible reasons
(EE) Screen(s) found, but none have a usable configuration

Fatal server error:
no screens found
giving up
xinit: Connection refused (errno 111): unable to connect to X server
xinit: No such process (errno 3): Server error.

```

tried:
1)
```
dpkg-reconfigure xerver-xorg
```
no effect still the same

2)
```
apt-get install xserver-xorg --reinstall
```
no effect still the same

Any clues where to go now?

---

### Post by riverfr0zen on 2008-11-04
I had quite a similar problem with a Radeon HD 3200 /  Radeon HD 3450 combo. I had thought that X somehow didn't know which card to use, and gave up (even though it worked fine in 8.04), but not sure if that is the actual issue.

I was able to fix it by specifying the BusID for the 3450 in the Device section. So my config looks like this now:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
	BusId		"2:0:0"
EndSection
```

(Your config may be slightly different, but the BusId part is what is important here - adding it made my setup work as usual again).

---

