---
title: "No USB in Dapper Drake"
date: 2006-09-01
forum: Hardware &amp; Laptops
---

### Post by winthrophill on 2006-09-01
I've just loaded ubuntu onto my three year old presario 2500 with high hopes but none of my USB ports are recognized.  I've tried my ipod and an external flash drive with no sucess, no indications, no nothing.  i've attached the output of the dmesg to help diagnose my woes.
thanks much.

[17179581.736000] usbcore: registered new driver usbfs
[17179581.736000] usbcore: registered new driver hub
[17179581.740000] USB Universal Host Controller Interface driver v2.3
[17179581.744000] PCI: Enabling device 0000:00:0b.0 (0000 -> 0001)
[17179581.744000] ACPI: PCI Interrupt 0000:00:0b.0[A]: no GSI
[17179581.744000] uhci_hcd 0000:00:0b.0: Found HC with no IRQ.  Check BIOS/PCI 0000:00:0b.0 setup!
[17179581.744000] uhci_hcd 0000:00:0b.0: init 0000:00:0b.0 fail, -19
[17179581.744000] PCI: Enabling device 0000:00:0b.1 (0000 -> 0001)
[17179581.744000] ACPI: PCI Interrupt 0000:00:0b.1[B]: no GSI
[17179581.744000] uhci_hcd 0000:00:0b.1: Found HC with no IRQ.  Check BIOS/PCI 0000:00:0b.1 setup!
[17179581.744000] uhci_hcd 0000:00:0b.1: init 0000:00:0b.1 fail, -19
[17179581.768000] PCI: Enabling device 0000:00:0b.2 (0000 -> 0002)
[17179581.768000] ACPI: PCI Interrupt 0000:00:0b.2[C]: no GSI
[17179581.768000] ehci_hcd 0000:00:0b.2: Found HC with no IRQ.  Check BIOS/PCI 0000:00:0b.2 setup!
[17179581.768000] ehci_hcd 0000:00:0b.2: init 0000:00:0b.2 fail, -19
[17179581.800000] ieee1394: Initialized config rom entry `ip1394'
[17179581.804000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[17179581.808000] PCI: Enabling device 0000:00:0c.0 (0010 -> 0012)
[17179581.808000] **** SET: Misaligned resource pointer: db9fb302 Type 07 Len 0
[17179581.808000] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 10
[17179581.808000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNK2] -> GSI 10 (level, low) -> IRQ 10
[17179581.844000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179581.844000] **** SET: Misaligned resource pointer: db9fb302 Type 07 Len 0
[17179581.844000] ACPI: PCI Interrupt Link [LNK8] enabled at IRQ 10
[17179581.844000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNK8] -> GSI 10 (level, low) -> IRQ 10
[17179581.844000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[17179582.096000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[17179582.096000] ohci_hcd 0000:00:02.0: irq 10, io mem 0xd0000000
[17179582.152000] hub 1-0:1.0: USB hub found
[17179582.152000] hub 1-0:1.0: 3 ports detected
[17179582.168000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[d0006000-d00067ff]  Max Packet=[2048]
[17179582.256000] **** SET: Misaligned resource pointer: dba9bec2 Type 07 Len 0
[17179582.256000] ACPI: PCI Interrupt Link [LNK4] enabled at IRQ 10
[17179582.256000] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LNK4] -> GSI 10 (level, low) -> IRQ 10
[17179582.256000] ohci_hcd 0000:00:0f.0: OHCI Host Controller
[17179582.472000] ohci_hcd 0000:00:0f.0: new USB bus registered, assigned bus number 2
[17179582.472000] ohci_hcd 0000:00:0f.0: irq 10, io mem 0xd0007000
[17179582.528000] hub 2-0:1.0: USB hub found
[17179582.528000] hub 2-0:1.0: 3 ports detected
[17179582.728000] usb 1-3: new low speed USB device using ohci_hcd and address 2[17179582.776000] Attempting manual resume
[17179582.832000] EXT3-fs: mounted filesystem with ordered data mode.
[17179582.832000] kjournald starting.  Commit interval 5 seconds
[17179582.908000] usb 1-3: device descriptor read/64, error -110
[17179583.192000] usb 1-3: device descriptor read/64, error -110
[17179583.440000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000d9d71a05e2a51]
[17179583.472000] usb 1-3: new low speed USB device using ohci_hcd and address 3[17179583.652000] usb 1-3: device descriptor read/64, error -110
[17179583.936000] usb 1-3: device descriptor read/64, error -110
[17179584.216000] usb 1-3: new low speed USB device using ohci_hcd and address 4[17179584.624000] usb 1-3: device not accepting address 4, error -110
[17179584.800000] usb 1-3: new low speed USB device using ohci_hcd and address 5[17179585.208000] usb 1-3: device not accepting address 5, error -110
[17179585.512000] usb 2-3: new low speed USB device using ohci_hcd and address 2[17179585.696000] usb 2-3: device descriptor read/64, error -110
[17179585.980000] usb 2-3: device descriptor read/64, error -110
[17179586.260000] usb 2-3: new low speed USB device using ohci_hcd and address 3[17179586.440000] usb 2-3: device descriptor read/64, error -110
[17179586.724000] usb 2-3: device descriptor read/64, error -110
[17179587.004000] usb 2-3: new low speed USB device using ohci_hcd and address 4[17179587.412000] usb 2-3: device not accepting address 4, error -110
[17179587.588000] usb 2-3: new low speed USB device using ohci_hcd and address 5[17179587.996000] usb 2-3: device not accepting address 5, error -110
[17179601.464000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNK5] -> GSI 11 (level, low) -> IRQ 11

---

### Post by Jussi Kukkonen on 2006-09-01
Are you using a K7 kernel?

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/54273](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/54273)

---

### Post by winthrophill on 2006-09-02
hmmm...sorry, I'm very new to linux/ubuntu. How would I determine if I'm using a K7 kernel?

---

### Post by winthrophill on 2006-09-05
ok, I got smart.  I loaded the 686 kernel but am still having the same problem: no USB recognition and the same dmesg readout.
What could it be? Any advice or direction?
thanks

---

