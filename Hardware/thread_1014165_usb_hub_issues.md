---
title: "usb hub issues"
date: 2008-12-17
forum: Hardware
---

### Post by king vash on 2008-12-17
My computer is recessed so I ran a extender to a hub that is easier to reach. 
from the hub I attempt to plug in my keyboard, mouse and webcam. it does not work
I can have three devices working (keyboard, mouse, flash drive) but not keyboard, mouse, webcam. I can have keyboard and webcam  but not with the mouse

with keyboard and mouse plugged into the hub and webcam plugged into computers my lsusb is
```
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 046d:08c7 Logitech, Inc. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 005: ID 045e:00d1 Microsoft Corp. Optical Mouse with Tilt Wheel
Bus 003 Device 004: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 003 Device 003: ID 058f:9254 Alcor Micro Corp. Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```


when I move the webcam to the hub I get this

```

Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 007: ID 046d:08c7 Logitech, Inc. 
Bus 003 Device 005: ID 045e:00d1 Microsoft Corp. Optical Mouse with Tilt Wheel
Bus 003 Device 004: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 003 Device 003: ID 058f:9254 Alcor Micro Corp. Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

I can move the keyboard and mouse around the hub to prove that all the ports work. 


I can connect to the webcam and the power led on it will blink but then it will fail.

---

