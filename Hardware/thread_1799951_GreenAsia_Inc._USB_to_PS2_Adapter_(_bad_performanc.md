---
title: "GreenAsia Inc. USB to PS/2 Adapter ( bad performance )"
date: 2011-07-08
forum: Hardware
---

### Post by kuifje09 on 2011-07-08
Because I use my "ubuntu" computer(usb) together with a 4-port KVM-switch(ps2) I needed a ps2-to-usb converter.
I use now :
Bus 002 Device 008: ID 0e8f:0020 GreenAsia Inc. USB to PS/2 Adapter

On ubuntu 11.04 , 2.6.38-8-generic

It basicaly works, but regular and once every second or two , the input from the keyboard or mouse does not reach the computer. Even typing this post is interupted now and then.

Letters or mouse move during the interruption gets lost. Very very disturbing.

My question, is it the adapter or something to do with usb.

---

### Post by kuifje09 on 2011-07-08
UPDATE:  In dmesg/messages  I found with an uptime of 2:53 240 times:

[10402.276062] usb 2-2: new low speed USB device using uhci_hcd and address 88
[10402.492236] input: GASIA PS2toUSB Adapter as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input238
[10402.492474] generic-usb 0003:0E8F:0020.00F2: input,hidraw0: USB HID v1.10 Keyboard [GASIA PS2toUSB Adapter] on usb-0000:00:1d.0-2/input0
[10402.517397] input: GASIA PS2toUSB Adapter as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.1/input/input239
[10402.517714] generic-usb 0003:0E8F:0020.00F3: input,hidraw1: USB HID v1.10 Mouse [GASIA PS2toUSB Adapter] on usb-0000:00:1d.0-2/input1
[10432.536077] usb 2-2: USB disconnect, address 88
[10434.804042] usb 2-2: new low speed USB device using uhci_hcd and address 89
[10435.080250] input: GASIA PS2toUSB Adapter as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input240
[10435.080547] generic-usb 0003:0E8F:0020.00F4: input,hidraw0: USB HID v1.10 Keyboard [GASIA PS2toUSB Adapter] on usb-0000:00:1d.0-2/input0
[10435.104585] input: GASIA PS2toUSB Adapter as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.1/input/input241
[10435.105146] generic-usb 0003:0E8F:0020.00F5: input,hidraw1: USB HID v1.10 Mouse [GASIA PS2toUSB Adapter] on usb-0000:00:1d.0-2/input1

This must tell some usb-guru something...

---

### Post by kuifje09 on 2011-07-08
Did some tests :

No matter which usb-bus I plug-in the PS/2 - usb converter,  even beside a usb-joystick the keyboard and the mouse are unstable. Joystick keeps on working.

Must be the converter.

Can somebody shine some light on this please ?

---

### Post by kuifje09 on 2011-07-09
after some other posts the conclusion must be this is just about the combination.
So this device or de switchbox is not 100%  ps/2  or the other usb compliant?

It is defenit,  with the original Dell PS2/mouse/keyboard converter it works perfect.

---

