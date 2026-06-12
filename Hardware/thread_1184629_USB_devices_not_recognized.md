---
title: "USB devices not recognized"
date: 2009-06-11
forum: Hardware
---

### Post by Anquietas on 2009-06-11
Hello,

For some time, I have a wierd problem with my USB on my Ubuntu Desktop.

The problem is that Ubuntu cannot acces and write the new USB devices. However, an USB mouse can be used and an USB Hub's leds are functioning, but when I introduce a Card Reader or a Memory Stick, it doesn't react to it.

Here is the message log:

```

Jun 11 01:03:04 betabase kernel: [  757.704052] usb 3-3: new full speed USB device using ohci_hcd and address 11
Jun 11 01:03:05 betabase kernel: [  758.112038] usb 3-3: device not accepting address 11, error -62
Jun 11 01:03:05 betabase kernel: [  758.248069] usb 3-3: new full speed USB device using ohci_hcd and address 12
Jun 11 01:03:05 betabase kernel: [  758.656039] usb 3-3: device not accepting address 12, error -62
Jun 11 01:03:05 betabase kernel: [  758.792587] usb 3-3: new full speed USB device using ohci_hcd and address 13
Jun 11 01:03:05 betabase kernel: [  758.932035] usb 3-3: device descriptor read/64, error -62
Jun 11 01:03:06 betabase kernel: [  759.176584] usb 3-3: device descriptor read/64, error -62
Jun 11 01:03:06 betabase kernel: [  759.416047] usb 3-3: new full speed USB device using ohci_hcd and address 14
Jun 11 01:03:06 betabase kernel: [  759.556033] usb 3-3: device descriptor read/64, error -62
Jun 11 01:03:06 betabase kernel: [  759.800556] usb 3-3: device descriptor read/64, error -62
Jun 11 01:03:06 betabase kernel: [  759.904055] hub 3-0:1.0: unable to enumerate USB device on port 3

```

It cannot enumerate, it returns a "-62" error and it does not accept address.

Ubuntu version: 9.04 Jaunty Jackalope 64 Bit version, Kernel 2.6.28-11-generic.

Please advice

---

### Post by Anquietas on 2009-06-13
Anyone active here ???????

At least tell from where the hell can I get some support !

---

