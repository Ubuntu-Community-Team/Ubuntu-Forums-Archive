---
title: "1 device existant, 4 shown in /dev"
date: 2007-05-27
forum: Hardware &amp; Laptops
---

### Post by proxess on 2007-05-27
Just yesterday i updated to the latest kernel. When i do this i have to recompile the drivers for my xpad360, no biggy.

All i have to do is make then copy paste the .ko file into some system folder as shown in the guides, then depmod -a and modprobe xpad and my pad would as if magically work.

Problem is this time it didn't work, what happened was instead of making a device /dev/input/js0, the gamepad doesnt work and it makes the following:

/dev/input/js0
/dev/input/js1
/dev/input/js2
/dev/input/js3
/dev/input/event6
/dev/input/event7
/dev/input/event8
/dev/input/event9

doing sudo modprobe -r xpad removes all these, but that would kill the purpose of the gamepad.

i've tried recompiling the drivers but the problem persists.


/dev/input without xpad:
```
proxess@prxss:/dev/input$ ls
by-id    event0  event2  event4  mice    mouse1  ts1
by-path  event1  event3  event5  mouse0  ts0
```

/dev/input with xpad:
```
proxess@prxss:/dev/input$ ls
by-id    event0  event2  event4  event6  event8  js0  js2  mice    mouse1  ts1
by-path  event1  event3  event5  event7  event9  js1  js3  mouse0  ts0
```

lsmod with xpad:
```
proxess@prxss:/dev/input$ lsmod | grep xpad
xpad                   10116  0 
usbcore               134280  6 xpad,epcam,usbhid,ehci_hcd,ohci_hcd
```

lsusb:
```
proxess@prxss:/dev/input$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 045e:028e Microsoft Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 041e:400d Creative Technology, Ltd WebCam PD1001
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 0000:0000
```

---

