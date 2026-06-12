---
title: "Wizardpen compatible graphics tablet."
date: 2013-12-14
forum: Hardware
---

### Post by neojames on 2013-12-14
Hello, I have a rather old (well about 5+ years) graphics tablet that I am trying to get working with Linux again. It is apparently supported by evdev, however it doesn't seem to want to do anything. Does anybody have any idea on how to get this working?

Here are the outputs of a few commands, hopefully they will help!

```
$ lsusb                                                              [22:18:19]
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 010 Device 002: ID 0e39:0137 Smart Modular Technologies, Inc. Bluetooth Device
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 1bcf:0c31 Sunplus Innovation Technology Inc. SPIF30x Serial-ATA bridge
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 003: ID 046d:c051 Logitech, Inc. G3 (MX518) Optical Mouse
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 5543:0004 UC-Logic Technology Corp. Tablet WP5540U
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

```

$ xinput list                                                        [22:18:21]
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC Tablet WP5540U                 	id=8	[slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC Tablet WP5540U                 	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse         	id=10	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]

```

```

$ xinput list-props 8                                                [22:18:33]
Device 'UC-LOGIC Tablet WP5540U':
	Device Enabled (141):	1
	Coordinate Transformation Matrix (143):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (263):	0
	Device Accel Constant Deceleration (264):	1.000000
	Device Accel Adaptive Deceleration (265):	1.000000
	Device Accel Velocity Scaling (266):	10.000000

```

```

$ xinput list-props 9                                                [22:18:38]
Device 'UC-LOGIC Tablet WP5540U':
	Device Enabled (141):	1
	Coordinate Transformation Matrix (143):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (263):	0
	Device Accel Constant Deceleration (264):	1.000000
	Device Accel Adaptive Deceleration (265):	1.000000
	Device Accel Velocity Scaling (266):	10.000000

```

As far as I can tell, its being assigned as a pointer but not receiving any positional information, could this be a misconfiguration with evdev or something?

---

