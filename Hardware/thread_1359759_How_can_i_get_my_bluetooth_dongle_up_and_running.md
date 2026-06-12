---
title: "How can i get my bluetooth dongle up and running"
date: 2009-12-20
forum: Hardware
---

### Post by rosier on 2009-12-20
Hi I'm on my second dongle and cant get it up and running- cant get it listed on lsusb.

dad@dad-desktop:~$ lsusb
Bus 002 Device 002: ID 05a9:8519 OmniVision Technologies, Inc. OV519 Webcam
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 125f:1040 A-DATA Technology Co., Ltd. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
dad@dad-desktop:~$ 

(Ive got  a USB 4GB Pendrive and a Webcam installed- both mount fine. Also tried my PDA phone all ok- syncs another issue thought- besides the point...

and when i do connect it i get the following error in my sys logs.

[INDENT]Dec 20 21:05:24 dad-desktop kernel: [15108.996024] usb 4-2: new full speed USB device using uhci_hcd and address 17
Dec 20 21:05:24 dad-desktop kernel: [15109.404024] usb 4-2: device not accepting address 17, error -71
Dec 20 21:05:24 dad-desktop kernel: [15109.404049] hub 4-0:1.0: unable to enumerate USB device on port 2
[/INDENT]can anyone help to get my bluetooth dongle up and running- same problem when i install it on a fresh copy of hardy heron.

Seems to be happy with fedora...

Help please.....:P

---

### Post by IcarusR on 2009-12-20
Have you tried it in all usb ports with no other usb devices plugged in ?

---

### Post by rosier on 2009-12-20
yeah the hardware has 4 rear ports and two in the front of the case- its a custom built box- reads all other usb gadjets etc.. cant make any sense of it- UBUNTU seems shallow on Bluetooth support- would have thought that the builtin software would be robust enough with this widespread technology???
Anyway doesnt help me anymore...will keep asking and bumping, thanks all the same.

---

### Post by IcarusR on 2009-12-21
I read several incidents with this error & causes were multiple...
Broken wire in USB cable.
Insufficient power for device. = reason why suggesting only plugging bluetooth in.

Silly question, does the bluetooth actually work ? Can you try it on another box to confirm ?

---

### Post by rosier on 2010-01-03
hi Icarus, back from holiday, yeah works on a fedora box real nice easy interface- plug and play- Ubuntu has not been compliant- still unsure what to do- if you can help further would be appreciated.

---

