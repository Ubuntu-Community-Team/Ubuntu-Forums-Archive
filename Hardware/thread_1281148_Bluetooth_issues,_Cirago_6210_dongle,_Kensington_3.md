---
title: "Bluetooth issues, Cirago 6210 dongle, Kensington 3071 headset"
date: 2009-10-03
forum: Hardware
---

### Post by ceverett on 2009-10-03
When I turn on the headset, it pairs up no problem.  

it shows up in the desktop applet, and in hciconfig:
```
hci0:	Type: USB
	BD Address: 00:1B:DC:0F:6B:24 ACL MTU: 310:10 SCO MTU: 64:8
	UP RUNNING PSCAN ISCAN 
	RX bytes:4568 acl:44 sco:0 events:147 errors:0
	TX bytes:4438 acl:46 sco:0 commands:76 errors:0
	Features: 0xff 0xff 0x8f 0xfe 0x9b 0xff 0x59 0x83
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH HOLD SNIFF PARK 
	Link mode: SLAVE ACCEPT 
	Name: 'headset-01'
	Class: 0x4a210c
	Service Classes: Networking, Capturing, Telephony
	Device Class: Computer, Laptop
	HCI Ver: 2.1 (0x4) HCI Rev: 0x12e7 LMP Ver: 2.1 (0x4) LMP Subver: 0x12e7
	Manufacturer: Cambridge Silicon Radio (10)

```

and I can see it using sdptool

```
sdptool browse 00:19:15:80:F8:EB
Browsing 00:19:15:80:F8:EB ...
Service Name: HSU
Service RecHandle: 0x90001
Service Class ID List:
  "Headset" (0x1108)
  "Generic Audio" (0x1203)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 1
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Headset" (0x1108)
    Version: 0x0100

Service Name: HFU
Service RecHandle: 0x90002
Service Class ID List:
  "Handsfree" (0x111e)
  "Generic Audio" (0x1203)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 2
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Handsfree" (0x111e)
    Version: 0x0101

Service Name: A2DPSink
Service Provider: RF Micro Devices
Service RecHandle: 0x90003
Service Class ID List:
  "Audio Sink" (0x110b)
Protocol Descriptor List:
  "L2CAP" (0x0100)
    PSM: 25
  "AVDTP" (0x0019)
    uint16: 0x100
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Advanced Audio" (0x110d)
    Version: 0x0100

Service Name: AVRCP Controller
Service Provider: RF Micro Devices
Service RecHandle: 0x90004
Service Class ID List:
  "AV Remote" (0x110e)
Protocol Descriptor List:
  "L2CAP" (0x0100)
    PSM: 23
  "AVCTP" (0x0017)
    uint16: 0x100
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "AV Remote" (0x110e)
    Version: 0x0100
```


However, i don't see it in lsusb, and in kern.log I see this:

```
Oct  2 22:45:16 johannes kernel: [16982.705936] ehci_hcd 0000:00:1d.7: port 7 reset error -110
Oct  2 22:45:16 johannes kernel: [16982.705946] hub 1-0:1.0: hub_port_status failed (err = -32)
Oct  2 22:45:17 johannes kernel: [16982.911263] ehci_hcd 0000:00:1d.7: port 7 reset error -110
Oct  2 22:45:17 johannes kernel: [16982.911271] hub 1-0:1.0: hub_port_status failed (err = -32)
Oct  2 22:45:17 johannes kernel: [16983.115280] ehci_hcd 0000:00:1d.7: port 7 reset error -110
Oct  2 22:45:17 johannes kernel: [16983.115289] hub 1-0:1.0: hub_port_status failed (err = -32)
Oct  2 22:45:17 johannes kernel: [16983.317947] ehci_hcd 0000:00:1d.7: port 7 reset error -110
Oct  2 22:45:17 johannes kernel: [16983.317955] hub 1-0:1.0: hub_port_status failed (err = -32)
Oct  2 22:45:17 johannes kernel: [16983.521946] ehci_hcd 0000:00:1d.7: port 7 reset error -110
Oct  2 22:45:17 johannes kernel: [16983.521955] hub 1-0:1.0: hub_port_status failed (err = -32)
Oct  2 22:45:17 johannes kernel: [16983.521958] hub 1-0:1.0: Cannot enable port 7.  Maybe the USB cable is bad?
Oct  2 22:45:17 johannes kernel: [16983.577942] ehci_hcd 0000:00:1d.7: port 7 reset error -110
Oct  2 22:45:17 johannes kernel: [16983.577950] hub 1-0:1.0: hub_port_status failed (err = -32)
Oct  2 22:45:17 johannes kernel: [16983.781945] ehci_hcd 0000:00:1d.7: port 7 reset error -110
Oct  2 22:45:17 johannes kernel: [16983.783023] hub 1-0:1.0: hub_port_status failed (err = -32)
Oct  2 22:45:18 johannes kernel: [16983.985948] ehci_hcd 0000:00:1d.7: port 7 reset error -110
Oct  2 22:45:18 johannes kernel: [16983.985956] hub 1-0:1.0: hub_port_status failed (err = -32)
Oct  2 22:45:18 johannes kernel: [16984.189943] ehci_hcd 0000:00:1d.7: port 7 reset error -110
Oct  2 22:45:18 johannes kernel: [16984.189950] hub 1-0:1.0: hub_port_status failed (err = -32)
Oct  2 22:45:18 johannes kernel: [16984.393913] ehci_hcd 0000:00:1d.7: port 7 reset error -110
Oct  2 22:45:18 johannes kernel: [16984.393924] hub 1-0:1.0: hub_port_status failed (err = -32)
Oct  2 22:45:18 johannes kernel: [16984.393927] hub 1-0:1.0: Cannot enable port 7.  Maybe the USB cable is bad?
Oct  2 22:45:18 johannes kernel: [16984.449968] ehci_hcd 0000:00:1d.7: port 7 reset error -110
Oct  2 22:45:18 johannes kernel: [16984.449977] hub 1-0:1.0: hub_port_status failed (err = -32)
Oct  2 22:45:18 johannes kernel: [16984.653947] ehci_hcd 0000:00:1d.7: port 7 reset error -110
Oct  2 22:45:18 johannes kernel: [16984.653955] hub 1-0:1.0: hub_port_status failed (err = -32)
Oct  2 22:45:19 johannes kernel: [16984.857944] ehci_hcd 0000:00:1d.7: port 7 reset error -110
Oct  2 22:45:19 johannes kernel: [16984.858262] hub 1-0:1.0: hub_port_status failed (err = -32)
Oct  2 22:45:19 johannes kernel: [16985.061947] ehci_hcd 0000:00:1d.7: port 7 reset error -110
Oct  2 22:45:19 johannes kernel: [16985.061955] hub 1-0:1.0: hub_port_status failed (err = -32)
Oct  2 22:45:19 johannes kernel: [16985.266008] ehci_hcd 0000:00:1d.7: port 7 reset error -110
Oct  2 22:45:19 johannes kernel: [16985.266016] hub 1-0:1.0: hub_port_status failed (err = -32)
Oct  2 22:45:19 johannes kernel: [16985.266019] hub 1-0:1.0: Cannot enable port 7.  Maybe the USB cable is bad?
Oct  2 22:45:19 johannes kernel: [16985.321940] ehci_hcd 0000:00:1d.7: port 7 reset error -110
Oct  2 22:45:19 johannes kernel: [16985.321946] hub 1-0:1.0: hub_port_status failed (err = -32)
Oct  2 22:45:19 johannes kernel: [16985.525945] ehci_hcd 0000:00:1d.7: port 7 reset error -110
Oct  2 22:45:19 johannes kernel: [16985.525953] hub 1-0:1.0: hub_port_status failed (err = -32)
Oct  2 22:45:19 johannes kernel: [16985.729943] ehci_hcd 0000:00:1d.7: port 7 reset error -110
Oct  2 22:45:19 johannes kernel: [16985.729954] hub 1-0:1.0: hub_port_status failed (err = -32)
Oct  2 22:45:20 johannes kernel: [16985.933943] ehci_hcd 0000:00:1d.7: port 7 reset error -110
Oct  2 22:45:20 johannes kernel: [16985.933951] hub 1-0:1.0: hub_port_status failed (err = -32)
Oct  2 22:45:20 johannes kernel: [16986.137950] ehci_hcd 0000:00:1d.7: port 7 reset error -110
Oct  2 22:45:20 johannes kernel: [16986.137969] hub 1-0:1.0: hub_port_status failed (err = -32)
Oct  2 22:45:20 johannes kernel: [16986.137973] hub 1-0:1.0: Cannot enable port 7.  Maybe the USB cable is bad?
Oct  2 22:45:20 johannes kernel: [16986.137989] hub 1-0:1.0: unable to enumerate USB device on port 7
Oct  2 22:45:20 johannes kernel: [16986.392037] usb 5-1: new low speed USB device using uhci_hcd and address 38
Oct  2 22:45:20 johannes kernel: [16986.512056] usb 5-1: device descriptor read/64, error -71
Oct  2 22:45:21 johannes kernel: [16987.408945] usb 5-1: device descriptor read/64, error -71
Oct  2 22:45:21 johannes kernel: [16987.624055] usb 5-1: new low speed USB device using uhci_hcd and address 39
Oct  2 22:45:22 johannes kernel: [16988.429088] usb 5-1: device descriptor read/64, error -71
Oct  2 22:45:22 johannes kernel: [16988.656076] usb 5-1: device descriptor read/64, error -71
Oct  2 22:45:23 johannes kernel: [16988.872356] usb 5-1: new low speed USB device using uhci_hcd and address 40
Oct  2 22:45:23 johannes kernel: [16989.289038] usb 5-1: device not accepting address 40, error -71
Oct  2 22:45:24 johannes kernel: [16990.680076] usb 5-1: new low speed USB device using uhci_hcd and address 41
Oct  2 22:45:25 johannes kernel: [16991.092057] usb 5-1: device not accepting address 41, error -71
Oct  2 22:45:25 johannes kernel: [16991.092080] hub 5-0:1.0: unable to enumerate USB device on port 1
```
however hcitool gives very conflicting results:
```
$ hcitool dev
Devices:
	hci0	00:1B:DC:0F:6B:24
$ hcitool con
Connections:
$ hcitool cc 00:1B:DC:0F:6B:24
Device is not available.
```
please help, I'm at my wits end ...

Edit: oh yeah, I'm using an up to date Jaunty on a Dell Inspiron 6400 lappie.

---

