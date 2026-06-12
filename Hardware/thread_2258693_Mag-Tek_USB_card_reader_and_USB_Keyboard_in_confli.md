---
title: "Mag-Tek USB card reader and USB Keyboard in conflict"
date: 2014-12-29
forum: Hardware
---

### Post by johnking364 on 2014-12-29
Hi:

Recently upgraded my desktop to lubuntu 14.04. everything seemed to go well until I needed to use Mag-Tek card reader to run a credit card. Two things happened: 1) the card reader failed to read the card and 2) the keyboard no longer functioned properly. 

I have tried several keyboards and several different credit cards but nothing has changed.
The reader and the cards all work on an earlier version of lubuntu (13.1)  that I still  have on a laptop.
I have reinstalled 13.10 on my desktop, but that made no difference either.

between each individual attempt, I restarted the computer and found the keyboard working properly, at least as far as I know.

If I open an app, like leafpad or the normal web page that the card reader is used with, and disconnect the keyboard, then I can read the card successfully, Plugging the keyboard back in finds it working as well.

One thing to note: I have the system bios setting for NUM LOCK to ON,  During POST, the NUM LOCK key goes on, then during the remainder of the startup process, it goes off, comes back on momentarily, and then turns off before the login screen appears.

I haven't been able to find any posts that fit this problem, the closest is the NUM LOCK set to ON at start up.

Below is a portion of the syslog file. The line "Dec 29 14:34:21 homeplate kernel: [    3.556895] random: nonblocking pool is initialized" is kind of interesting, but I don't know what that means or what the implications are. The card reader and the keyboard both follow that message though.

Any ideas?

John

Dec 29 14:34:21 homeplate kernel: [    2.236049] usb 1-7: new high-speed USB device number 6 using ehci-pci
Dec 29 14:34:21 homeplate kernel: [    2.441450] usb 1-7: New USB device found, idVendor=0644, idProduct=0200
Dec 29 14:34:21 homeplate kernel: [    2.441456] usb 1-7: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Dec 29 14:34:21 homeplate kernel: [    2.441460] usb 1-7: Product: CA-200
Dec 29 14:34:21 homeplate kernel: [    2.441464] usb 1-7: Manufacturer: TEAC
Dec 29 14:34:21 homeplate kernel: [    2.441467] usb 1-7: SerialNumber: 00000205A9BD
Dec 29 14:34:21 homeplate kernel: [    2.680057] usb 2-2: new full-speed USB device number 2 using uhci_hcd
Dec 29 14:34:21 homeplate kernel: [    2.852334] usb 2-2: New USB device found, idVendor=03f0, idProduct=0517
Dec 29 14:34:21 homeplate kernel: [    2.852341] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Dec 29 14:34:21 homeplate kernel: [    2.852345] usb 2-2: Product: hp LaserJet 1000
Dec 29 14:34:21 homeplate kernel: [    2.852349] usb 2-2: Manufacturer: Hewlett-Packard
Dec 29 14:34:21 homeplate kernel: [    2.876120] Switched to clocksource tsc
Dec 29 14:34:21 homeplate kernel: [    3.092077] usb 3-2: new low-speed USB device number 2 using uhci_hcd
Dec 29 14:34:21 homeplate kernel: [    3.260235] usb 3-2: New USB device found, idVendor=0461, idProduct=4d15
Dec 29 14:34:21 homeplate kernel: [    3.260241] usb 3-2: New USB device strings: Mfr=0, Product=2, SerialNumber=0
Dec 29 14:34:21 homeplate kernel: [    3.260246] usb 3-2: Product: USB Optical Mouse
Dec 29 14:34:21 homeplate kernel: [    3.500053] usb 4-1: new low-speed USB device number 2 using uhci_hcd
Dec 29 14:34:21 homeplate kernel: [    3.556895] random: nonblocking pool is initialized
Dec 29 14:34:21 homeplate kernel: [    3.674112] usb 4-1: New USB device found, idVendor=413c, idProduct=2003
Dec 29 14:34:21 homeplate kernel: [    3.674119] usb 4-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Dec 29 14:34:21 homeplate kernel: [    3.674123] usb 4-1: Product: Dell USB Keyboard
Dec 29 14:34:21 homeplate kernel: [    3.674127] usb 4-1: Manufacturer: Dell
Dec 29 14:34:21 homeplate kernel: [    3.916079] usb 4-2: new full-speed USB device number 3 using uhci_hcd
Dec 29 14:34:21 homeplate kernel: [    4.091112] usb 4-2: New USB device found, idVendor=0801, idProduct=0001
Dec 29 14:34:21 homeplate kernel: [    4.091119] usb 4-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Dec 29 14:34:21 homeplate kernel: [    4.091124] usb 4-2: Product: USB Swipe Reader
Dec 29 14:34:21 homeplate kernel: [    4.091127] usb 4-2: Manufacturer: Mag-Tek

Dec 29 14:34:21 homeplate kernel: [   13.714630] hid-generic 0003:0461:4D15.0001: input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1d.1-2/input0
Dec 29 14:34:21 homeplate kernel: [   13.728389] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input12
Dec 29 14:34:21 homeplate kernel: [   13.740197] hid-generic 0003:413C:2003.0002: input,hidraw1: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.2-1/input0
Dec 29 14:34:21 homeplate kernel: [   13.765803] input: Mag-Tek USB Swipe Reader as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input13
Dec 29 14:34:21 homeplate kernel: [   13.777547] hid-generic 0003:0801:0001.0003: input,hidraw2: USB HID v1.00 Keyboard [Mag-Tek USB Swipe Reader] on usb-0000:00:1d.2-2/input0

---

### Post by johnking364 on 2014-12-29
My apologies, The sentence 

"The card reader and the keyboard both follow that message though."

is misplaced in the original post. It was meant to be appended to 

"Below is a portion of the syslog file. The line "Dec 29 14:34:21  homeplate kernel: [    3.556895] random: nonblocking pool is  initialized" is kind of interesting, but I don't know what that means or  what the implications are."

---

