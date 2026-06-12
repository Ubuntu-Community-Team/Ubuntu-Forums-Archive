---
title: "USB problems 6.06 Dapper"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by underwaterbob on 2007-04-20
Hey,

My Samsung SENSP28 laptop has been acting up lately with the USB ports turning on and off and on and off.  dmesg gives me this:

[17186814.384000] hub 1-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
[17186814.384000] usb 1-2: USB disconnect, address 9
[17186814.564000] usb 1-2: new low speed USB device using ohci_hcd and address 10
[17186814.788000] input: USB OpticalWheel Mouse as /class/input/input1311
[17186814.788000] input: USB HID v1.10 Mouse [USB OpticalWheel Mouse] on usb-0000:02:06.0-2
[17186820.936000] hub 1-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
[17186820.936000] usb 1-2: USB disconnect, address 10
[17186821.116000] usb 1-2: new low speed USB device using ohci_hcd and address 11
[17186821.340000] input: USB OpticalWheel Mouse as /class/input/input1312
[17186821.340000] input: USB HID v1.10 Mouse [USB OpticalWheel Mouse] on usb-0000:02:06.0-2

this happens over and over again, you can watch the  USB mouse appear and disappear in device manager.  The mouse works fine on another computer.  I have an external USB harddrive that the machine has trouble detecting often as well.  The laptop has four ports and I get the same results in all of them.

Any ideas on how to fix?

---

