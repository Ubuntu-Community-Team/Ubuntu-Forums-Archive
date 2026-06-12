---
title: "help me to install router Telit Ar520"
date: 2008-11-04
forum: Hardware
---

### Post by 0abcdefg0 on 2008-11-04
output of usb view
```
Unknown Device
Manufacturer: Viking II
Serial Number: N14B026004775
Speed: 12Mb/s (full)
USB Version:  1.10
Device Class: 02(comm.)
Device Subclass: 00
Device Protocol: 00
Maximum Default Endpoint Size: 64
Number of Configurations: 1
Vendor Id: 0915
Product Id: 0005
Revision Number:  0.14

Config Number: 1
	Number of Interfaces: 1
	Attributes: c0
	MaxPower Needed: 200mA

	Interface Number: 0
		Name: (none)
		Alternate Number: 0
		Class: 0a(data ) 
		Sub Class: 00
		Protocol: 00
		Number of Endpoints: 3

			Endpoint Address: 81
			Direction: in
			Attribute: 3
			Type: Int.
			Max Packet Size: 32
			Interval: 100ms

			Endpoint Address: 83
			Direction: in
			Attribute: 2
			Type: Bulk
			Max Packet Size: 64
			Interval: 0ms

			Endpoint Address: 05
			Direction: out
			Attribute: 2
			Type: Bulk
			Max Packet Size: 64
			Interval: 0ms
```
output of sudo eciadsl-probe-device
```


5:  ? / Viking II (0915:0005)

probed USB device: ? / Viking II
VID1=0915, PID1=0005
VID2=0915, PID2=0005
Did you really unplug/replug your modem before launching this script?

```
output of sudo eciadsl-start
```

[EciAdsl 1/5] Setting up USB support...

Preliminary USB device filesystem is OK
Loading UHCI support... Warning: uhci-hcd module doesn't exist

[EciAdsl 2/5] Uploading firmware...

Process skipped .. no more needed
firmware loaded successfully

[EciAdsl 3/5] Synchronization...

ERROR can't set interface 0 to use alt setting 5
ERROR eciadsl-synch: failed
ERROR: failed to get synchronization
```

---

### Post by 0abcdefg0 on 2008-11-05
up pls help

---

### Post by 0abcdefg0 on 2008-11-06
```
 sudo eciadsl-vendor-device.pl ./usbsnoop.log
WARNING: interrupt packet not detected! File 'synch999.bin' was generated anyway but is probably incorrect.

```

---

