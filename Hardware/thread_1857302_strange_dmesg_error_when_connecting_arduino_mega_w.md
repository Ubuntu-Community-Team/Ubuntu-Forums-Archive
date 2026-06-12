---
title: "strange dmesg error when connecting arduino mega with ethernet shield"
date: 2011-10-10
forum: Hardware
---

### Post by strider3700 on 2011-10-10
I've been using an arduino mega for awhile now and it connects just fine when I plug it in.  it's dmesg is 
```
[10721.471787] usb 5-1: new full speed USB device using ohci_hcd and address 66
[10721.710252] ftdi_sio 5-1:1.0: FTDI USB Serial Device converter detected
[10721.710313] usb 5-1: Detected FT232RL
[10721.710319] usb 5-1: Number of endpoints 2
[10721.710324] usb 5-1: Endpoint 1 MaxPacketSize 64
[10721.710329] usb 5-1: Endpoint 2 MaxPacketSize 64
[10721.710333] usb 5-1: Setting MaxPacketSize 64
[10721.712115] usb 5-1: FTDI USB Serial Device converter now attached to ttyUSB0

```
and it shows up in lsusb as
```
 Bus 005 Device 066: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
```

now if I attach the ethernet shield to the mega and then plug it in it doesn't show up in lsusb.  and here is the error message in dmesg
```
[10987.600132] usb 5-1: new full speed USB device using ohci_hcd and address 67
[10987.750158] usb 5-1: device descriptor read/64, error -62
[10988.011789] usb 5-1: device descriptor read/64, error -62
[10988.290173] usb 5-1: new full speed USB device using ohci_hcd and address 68
[10988.441802] usb 5-1: device descriptor read/64, error -62
[10988.700137] usb 5-1: device descriptor read/64, error -62
[10988.981796] usb 5-1: new full speed USB device using ohci_hcd and address 69
[10989.401784] usb 5-1: device not accepting address 69, error -62
[10989.551788] usb 5-1: new full speed USB device using ohci_hcd and address 70
[10989.970119] usb 5-1: device not accepting address 70, error -62
[10989.970192] hub 5-0:1.0: unable to enumerate USB device on port 1

```

I can't figure out what device "descriptor read/64, error -62" means or even where to start figuring this out.   Any suggestions?

---

### Post by strider3700 on 2011-10-10
Well I've kind of figured it out.  There's something wrong with the power on my arduino. With the shield attached the voltage drags way down and the USB can't power it.   Add a 9V battery and things connect again  but I still get weird readings on the 3.3v and 5V lines.   oh well.  If anyone can tell me what the  error -62 actually means I'm still curious.

---

