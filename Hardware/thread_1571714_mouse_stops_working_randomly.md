---
title: "mouse stops working randomly"
date: 2010-09-10
forum: Hardware
---

### Post by koalaJason on 2010-09-10
Hello all.

Ive been having an intermittent problem with my mouse. It will randomly stop working. It does not move, and clicking does nothing. The keyboard works fine though.

The mouse is a USB Logitech trackman 2 button with wheel that acts as a 3rd button.

I use Karmic, and keep up to date on updates.

Ive had the mouse for years and the problem is only about a month old.

I can not duplicate the problem with this mouse on a windows machine.

The only real 'clue' is the logs file (To check, click system->administration->log file viewer. In there, click on the word 'messages' on the left side.)

Here is an example of what the log says when the freze event occurs :

Sep 10 00:35:04 jason-desktop kernel: [47408.840059] usb 5-1: USB disconnect, address 89
Sep 10 00:35:04 jason-desktop kernel: [47409.080063] usb 5-1: new low speed USB device using uhci_hcd and address 90
Sep 10 00:35:04 jason-desktop kernel: [47409.477913] usb 5-1: configuration #1 chosen from 1 choice
Sep 10 00:35:05 jason-desktop kernel: [47409.502937] input: Logitech Trackball as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/input/input31
Sep 10 00:35:05 jason-desktop kernel: [47409.503053] generic-usb 0003:046D:C404.001C: input,hidraw0: USB HID v1.10 Mouse [Logitech Trackball] on usb-0000:00:1d.3-1/input0
Sep 10 00:35:11 jason-desktop kernel: [47416.032056] usb 5-1: USB disconnect, address 90
Sep 10 00:35:11 jason-desktop kernel: [47416.272042] usb 5-1: new low speed USB device using uhci_hcd and address 91
Sep 10 00:35:12 jason-desktop kernel: [47416.832038] usb 5-1: new low speed USB device using uhci_hcd and address 92
Sep 10 00:35:12 jason-desktop kernel: [47417.400038] usb 5-1: new low speed USB device using uhci_hcd and address 93
Sep 10 00:35:13 jason-desktop kernel: [47417.928039] usb 5-1: new low speed USB device using uhci_hcd and address 94
Sep 10 00:36:20 jason-desktop kernel: [47484.944033] usb 5-1: new low speed USB device using uhci_hcd and address 95
Sep 10 00:36:20 jason-desktop kernel: [47485.136186] usb 5-1: configuration #1 chosen from 1 choice
Sep 10 00:36:20 jason-desktop kernel: [47485.158458] input: Logitech Trackball as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/input/input32
Sep 10 00:36:20 jason-desktop kernel: [47485.158580] generic-usb 0003:046D:C404.001D: input,hidraw0: USB HID v1.10 Mouse [Logitech Trackball] on usb-0000:00:1d.3-1/input0
Sep 10 00:36:23 jason-desktop kernel: [47487.952058] usb 5-1: USB disconnect, address 95
Sep 10 00:36:23 jason-desktop kernel: [47488.193395] usb 5-1: new low speed USB device using uhci_hcd and address 96
Sep 10 00:36:23 jason-desktop kernel: [47488.372944] usb 5-1: configuration #1 chosen from 1 choice
Sep 10 00:36:23 jason-desktop kernel: [47488.401351] input: Logitech Trackball as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/input/input33
Sep 10 00:36:23 jason-desktop kernel: [47488.401471] generic-usb 0003:046D:C404.001E: input,hidraw0: USB HID v1.10 Mouse [Logitech Trackball] on usb-0000:00:1d.3-1/input0
Sep 10 00:36:24 jason-desktop kernel: [47489.440477] usb 5-1: USB disconnect, address 96
Sep 10 00:36:25 jason-desktop kernel: [47489.680041] usb 5-1: new low speed USB device using uhci_hcd and address 97
Sep 10 00:36:25 jason-desktop kernel: [47490.240037] usb 5-1: new low speed USB device using uhci_hcd and address 98
Sep 10 00:36:26 jason-desktop kernel: [47490.800034] usb 5-1: new low speed USB device using uhci_hcd and address 99
Sep 10 00:36:26 jason-desktop kernel: [47491.324031] usb 5-1: new low speed USB device using uhci_hcd and address 100
Sep 10 00:36:29 jason-desktop kernel: [47494.032046] usb 5-1: new low speed USB device using uhci_hcd and address 101
Sep 10 00:36:29 jason-desktop kernel: [47494.205273] usb 5-1: configuration #1 chosen from 1 choice
Sep 10 00:36:29 jason-desktop kernel: [47494.230619] input: Logitech Trackball as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/input/input34
Sep 10 00:36:29 jason-desktop kernel: [47494.230739] generic-usb 0003:046D:C404.001F: input,hidraw0: USB HID v1.10 Mouse [Logitech Trackball] on usb-0000:00:1d.3-1/input0
Sep 10 00:36:32 jason-desktop kernel: [47496.880239] usb 5-1: USB disconnect, address 101
Sep 10 00:36:32 jason-desktop kernel: [47497.136031] usb 5-1: new low speed USB device using uhci_hcd and address 102
Sep 10 00:36:33 jason-desktop kernel: [47497.696037] usb 5-1: new low speed USB device using uhci_hcd and address 103
Sep 10 00:36:33 jason-desktop kernel: [47498.260034] usb 5-1: new low speed USB device using uhci_hcd and address 104
Sep 10 00:36:33 jason-desktop kernel: [47498.322528] usb 5-1: configuration #1 chosen from 1 choice
Sep 10 00:36:33 jason-desktop kernel: [47498.349274] input: Logitech Trackball as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/input/input35
Sep 10 00:36:33 jason-desktop kernel: [47498.349391] generic-usb 0003:046D:C404.0020: input,hidraw0: USB HID v1.10 Mouse [Logitech Trackball] on usb-0000:00:1d.3-1/input0
Sep 10 00:36:34 jason-desktop kernel: [47499.112068] usb 5-1: USB disconnect, address 104
Sep 10 00:36:37 jason-desktop kernel: [47501.548033] usb 5-1: new low speed USB device using uhci_hcd and address 105
Sep 10 00:36:37 jason-desktop kernel: [47501.722116] usb 5-1: configuration #1 chosen from 1 choice
Sep 10 00:36:37 jason-desktop kernel: [47501.746393] input: Logitech Trackball as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/input/input36
Sep 10 00:36:37 jason-desktop kernel: [47501.746512] generic-usb 0003:046D:C404.0021: input,hidraw0: USB HID v1.10 Mouse [Logitech Trackball] on usb-0000:00:1d.3-1/input0
Sep 10 00:36:38 jason-desktop kernel: [47502.832085] usb 5-1: USB disconnect, address 105
Sep 10 00:36:38 jason-desktop kernel: [47503.072227] usb 5-1: new low speed USB device using uhci_hcd and address 106
Sep 10 00:36:38 jason-desktop kernel: [47503.245575] usb 5-1: configuration #1 chosen from 1 choice
Sep 10 00:36:38 jason-desktop kernel: [47503.274543] input: Logitech Trackball as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/input/input37
Sep 10 00:36:38 jason-desktop kernel: [47503.274661] generic-usb 0003:046D:C404.0022: input,hidraw0: USB HID v1.10 Mouse [Logitech Trackball] on usb-0000:00:1d.3-1/input0
Sep 10 00:36:40 jason-desktop kernel: [47505.312059] usb 5-1: USB disconnect, address 106
Sep 10 00:36:41 jason-desktop kernel: [47505.552037] usb 5-1: new low speed USB device using uhci_hcd and address 107
Sep 10 00:36:41 jason-desktop kernel: [47505.949664] usb 5-1: configuration #1 chosen from 1 choice
Sep 10 00:36:41 jason-desktop kernel: [47505.972105] input: Logitech Trackball as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/input/input38
Sep 10 00:36:41 jason-desktop kernel: [47505.972225] generic-usb 0003:046D:C404.0023: input,hidraw0: USB HID v1.10 Mouse [Logitech Trackball] on usb-0000:00:1d.3-1/input0

Note that all takes place in 1.5 seconds!

Any tips on whats going on?

---

