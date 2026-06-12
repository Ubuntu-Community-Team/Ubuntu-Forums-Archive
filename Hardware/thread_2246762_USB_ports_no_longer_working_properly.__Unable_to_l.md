---
title: "USB ports no longer working properly.  Unable to locate mounted items"
date: 2014-10-03
forum: Hardware
---

### Post by sir-marky on 2014-10-03
I have two USB ports on my Samsung Series 9.  One USB2 and one USB3.
Until now they perform fine, however in the past day they have stopped responding properly.

If I plug a USB stick into the port and start the computer Ubuntu 14.04 recognises the stick and mounts it.
The same applies to my USB wireless mouse adpater.

If I remove the items and try putting them into each others ports, or start the computer without anything attached and try after Ubuntu has started, nothing is recognised.

I checked gparted to see if the USB stick was recognised but simply not mounted but alas no.  It's not there.

I don't know how to resolve this.

Can someone advise what the next steps should be?

---

### Post by kc1di on 2014-10-03
It sounds like your automount settings got messed up somehow - This sometimes happens if you fail to eject or unmount a disk properly. 
in any event [this page]("https://help.ubuntu.com/community/Mount/USB") may be of help to you.

---

### Post by sir-marky on 2014-10-03
I'm afraid I cannot see anything on this page to help me.
I have narrowed the problem to only the USB3 port now.  The USB2 one does mount devices.  It would seem the USB3 port software simply falls over.  When plugging the mouse adapter into the USB 2 port I see the following in /var/log/syslog

Oct  3 14:09:48 markys-samsung-series9 kernel: [  572.350928] usbhid: USB HID core driver
Oct  3 14:09:48 markys-samsung-series9 kernel: [  572.368359] input: Microsoft Microsoft&#65533; Nano Transceiver v1.0 as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input11
Oct  3 14:09:48 markys-samsung-series9 kernel: [  572.368534] hid-generic 0003:045E:0773.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Microsoft&#65533; Nano Transceiver v1.0] on usb-0000:00:1d.0-1.2/input0
Oct  3 14:09:48 markys-samsung-series9 laptop-mode: Laptop mode 
Oct  3 14:09:48 markys-samsung-series9 kernel: [  572.369059] input: Microsoft Microsoft&#65533; Nano Transceiver v1.0 as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.1/input/input12
Oct  3 14:09:48 markys-samsung-series9 kernel: [  572.370106] hid-generic 0003:045E:0773.0002: input,hidraw1: USB HID v1.11 Mouse [Microsoft Microsoft&#65533; Nano Transceiver v1.0] on usb-0000:00:1d.0-1.2/input1
Oct  3 14:09:48 markys-samsung-series9 laptop-mode: enabled, not active
Oct  3 14:09:48 markys-samsung-series9 kernel: [  572.381567] input: Microsoft Microsoft&#65533; Nano Transceiver v1.0 as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.2/input/input13
Oct  3 14:09:48 markys-samsung-series9 kernel: [  572.381822] hid-generic 0003:045E:0773.0003: input,hiddev0,hidraw2: USB HID v1.11 Device [Microsoft Microsoft&#65533; Nano Transceiver v1.0] on usb-0000:00:1d.0-1.2/input2

The USB3 port, however says,

Oct  3 14:08:57 markys-samsung-series9 kernel: [  521.404603] usb usb2: root hub lost power or was reset
Oct  3 14:08:57 markys-samsung-series9 kernel: [  521.404612] usb usb3: root hub lost power or was reset
Oct  3 14:08:57 markys-samsung-series9 kernel: [  521.412008] xhci_hcd 0000:03:00.0: irq 40 for MSI/MSI-X
Oct  3 14:08:57 markys-samsung-series9 kernel: [  521.412029] xhci_hcd 0000:03:00.0: irq 41 for MSI/MSI-X
Oct  3 14:08:57 markys-samsung-series9 kernel: [  521.412044] xhci_hcd 0000:03:00.0: irq 42 for MSI/MSI-X
Oct  3 14:08:57 markys-samsung-series9 kernel: [  521.412058] xhci_hcd 0000:03:00.0: irq 43 for MSI/MSI-X
Oct  3 14:08:57 markys-samsung-series9 kernel: [  521.412072] xhci_hcd 0000:03:00.0: irq 44 for MSI/MSI-X
Oct  3 14:08:57 markys-samsung-series9 kernel: [  521.462070] xhci_hcd 0000:03:00.0: Host took too long to start, waited 16000 microseconds.
Oct  3 14:08:57 markys-samsung-series9 kernel: [  521.462094] xhci_hcd 0000:03:00.0: PCI post-resume error -19!
Oct  3 14:08:57 markys-samsung-series9 kernel: [  521.462099] xhci_hcd 0000:03:00.0: HC died; cleaning up
Oct  3 14:08:57 markys-samsung-series9 kernel: [  521.462112] xhci_hcd 0000:03:00.0: HC died; cleaning up
Oct  3 14:08:57 markys-samsung-series9 kernel: [  521.481114] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.

I have checked if USB wake is enabled in the BIOS and it is and always has been.

---

