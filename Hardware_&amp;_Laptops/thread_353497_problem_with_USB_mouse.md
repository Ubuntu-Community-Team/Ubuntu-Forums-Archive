---
title: "problem with USB mouse"
date: 2007-02-04
forum: Hardware &amp; Laptops
---

### Post by guaiacum on 2007-02-04
I recently bought a new keyboard and mouse from amazon.com. In particular, a M$ Natural ergononic 4000 and M$ natural wireless laser 6000. I working now using the keyboard, no problems with that:

[17179583.792000] usbcore: registered new driver hiddev
[17179583.836000] input: Microsoft Natural&#65533; Ergonomic Keyboard 4000 as /class/input/input1
[17179583.836000] input: USB HID v1.11 Keyboard [Microsoft Natural&#65533; Ergonomic Keyboard 4000] on usb-0000:00:07.2-2
[17179583.860000] input: Microsoft Natural&#65533; Ergonomic Keyboard 4000 as /class/input/input2
[17179583.860000] input: USB HID v1.11 Device [Microsoft Natural&#65533; Ergonomic Keyboard 4000] on usb-0000:00:07.2-2
[17179583.860000] usbcore: registered new driver usbhid
[17179583.860000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver

But the pointer is giving me problems:

[17179581.272000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[17179581.392000] usb 1-1: device descriptor read/64, error -71
[17179581.628000] usb 1-1: device descriptor read/64, error -71
[17179581.844000] usb 1-1: new low speed USB device using uhci_hcd and address 3
[17179581.964000] usb 1-1: device descriptor read/64, error -71
[17179582.188000] usb 1-1: device descriptor read/64, error -71
[17179582.404000] usb 1-1: new low speed USB device using uhci_hcd and address 4
[17179582.812000] usb 1-1: device not accepting address 4, error -71
[17179582.924000] usb 1-1: new low speed USB device using uhci_hcd and address 5
[17179583.332000] usb 1-1: device not accepting address 5, error -71
[17179583.572000] usb 1-2: new low speed USB device using uhci_hcd and address 6
[17179583.752000] usb 1-2: configuration #1 chosen from 1 choice

I tried connecting the device again several times, but the error still shows.

The output from lsusb shows:

Bus 001 Device 006: ID 045e:00db Microsoft Corp. 
Bus 001 Device 001: ID 0000:0000 

lspci shows:

00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 64, IRQ 9
        I/O ports at 1400 [size=32]

uname -a
Linux tuxbuntu 2.6.17-10-386 #2 Tue Dec 5 22:26:18 UTC 2006 i686 GNU/Linux

I have used USB pointers in the past in my linux box without problems, so before thinking that I may have broken hardware in my hands I want to ask you guys for any hints on the matter.

Thanks in advanced.

Luis

---

