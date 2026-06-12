---
title: "No USB Ports Working"
date: 2008-10-26
forum: General Help
---

### Post by mfmbcpman on 2008-10-26
None of the USB ports in my laptop are working with Ubuntu (they do work with XP.) I am trying to use a mouse and an external drive, neither of which is recognized. I have no idea how this broke.

---

### Post by cariboo on 2008-10-26
Could post the output of dmesg when you plug in one of your devices. To get the output of dmesg, Open a Applications-->Accessories-->Terminal and type:

```
tail -n 15 /var/log/dmesg
```

this will print out the last 15 lines of the output of dmesg. Highlight the test in the terminal, then use the right and left touch pad buttons to paste.

Jim

---

### Post by mfmbcpman on 2008-10-26
```
[   28.105703] hci_usb: Unknown symbol hci_recv_fragment
[   28.105772] hci_usb: Unknown symbol hci_register_dev
[   28.132717] Bluetooth: HCI USB driver ver 2.9
[   28.133801] usbcore: registered new interface driver hci_usb
[   30.486104] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   30.486115] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   30.486242] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.12  Thu Jul 17 18:11:36 PDT 2008
[   28.731242] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 20
[   28.731268] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   28.773583] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   28.774797] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   28.997191] lp: driver loaded but no devices found
[   29.134745] Adding 248968k swap on /dev/sda5.  Priority:-1 extents:1 across:248968k
[   30.978340] EXT3 FS on sda1, internal journal
[   29.784668] ip_tables: (C) 2000-2006 Netfilter Core Team

```

---

### Post by mfmbcpman on 2008-10-27
Bumppity bump...

---

