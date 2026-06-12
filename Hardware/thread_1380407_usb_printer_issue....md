---
title: "usb printer issue..."
date: 2010-01-13
forum: Hardware
---

### Post by masavini on 2010-01-13
hi,
i plugged a usb-parallel adapter to one an old oki ml380 printer.

here is dmsg output:

```
[  903.377228] usb 7-1: new full speed USB device using uhci_hcd and address 4
[  903.541092] usb 7-1: configuration #1 chosen from 1 choice
[  903.583092] usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x1A86 pid 0x7584
```

and here is lsusb:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

if i try to install the printer, this is not recognized.
please mind that i have another usb printer (samsung laser printer) which perfectly works on my system.
could anyone help me?
many thanks

---

### Post by USB_NL on 2010-01-13
That's an old penprinter, right?

i had an oki long time ago (running with windows)

i dont think i can help any further

---

### Post by masavini on 2010-01-13
yeap, it's a penprinter... and yes, it's quite old!

i'm still working on this case:

- if i start winxp via virtualbox and i can't enable the USB2.0-Print[0252] device: it's not selectable (greyed)

- i checked into /dev/usb: the only existing device is lp0

- i tryed and put usb:/dev/usb/lp0 as URI in CUPS, but i still can't print... i get this message: ```
idle - "/usr/lib/cups/backend/usb failed"
```

- if i try to print a testpage with the previous settings, i get this error from dmesg:
```
usb[3113]: segfault at bfd3a000 ip 0027aad3 sp bfd32318 error 4 in libc-2.10.1.so[206000+13e000]
```

- tried to blacklist usblp in blacklist.conf and rebooted: nothing happened

- tried to change URI to parallel:/dev/usb/lp0: ```
Processing - printer not connected; will retry in 30 seconds...
```

still need help...

---

### Post by masavini on 2010-01-14
solved with:

1) usblp NOT blacklisted
2) manual install of the printer ppd driver downloaded from openprinting.org (this solved the backend problem)
3) set the printer URI as parallel:/dev/usb/lp0

nothing else, it started working like a charm!
lsusb can't see the printer, yet, but it works... :o)

---

