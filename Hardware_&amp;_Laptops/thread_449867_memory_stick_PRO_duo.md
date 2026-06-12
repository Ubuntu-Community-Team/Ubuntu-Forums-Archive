---
title: "memory stick PRO duo"
date: 2007-05-20
forum: Hardware &amp; Laptops
---

### Post by timmytron on 2007-05-20
i'm using ubuntu studio (fiesty) on a slightly old VAIO laptop, and have trouble making my PRO duo memory card reader activate. the LED lights up, but no read. do i need special drivers? any help would be greatly appreciated.

---

### Post by moosesoom on 2007-05-21
Can you please execute "dmesg" command after inserting memory stick in the reader and then post here the output of that command?

You better post "lspci" output too.

---

### Post by timmytron on 2007-05-21
ok, here they are...

---

### Post by timmytron on 2007-05-21
[ 1193.247000] pnp 00:00: resuming
[ 1193.247000] pnp 00:01: resuming
[ 1193.247000] pnp 00:02: resuming
[ 1193.247000] pnp 00:03: resuming
[ 1193.247000] system 00:04: resuming
[ 1193.247000] pnp 00:05: resuming
[ 1193.247000] pnp 00:06: resuming
[ 1193.247000] i8042 kbd 00:07: resuming
[ 1193.247000] pnp: Device 00:07 does not support activation.
[ 1193.247000] i8042 aux 00:08: resuming
[ 1193.247000] pnp: Device 00:08 does not support activation.
[ 1193.247000] platform pcspkr: resuming
[ 1193.247000] serial8250 serial8250: resuming
[ 1193.247000] i8042 i8042: resuming
[ 1193.247000] atkbd serio0: resuming
[ 1193.286000] platform eisa.0: resuming
[ 1193.286000] psmouse serio1: resuming
[ 1193.305000] platform vesafb.0: resuming
[ 1193.305000] usb usb1: resuming
[ 1193.337000] usb usb2: resuming
[ 1193.369000]  usbdev3.1_ep00: PM: resume from 0, parent usb3 still 2
[ 1193.369000]  usbdev3.1_ep81: PM: resume from 0, parent 3-0:1.0 still 2
[ 1193.369000] sd 0:0:0:0: resuming
[ 1193.369000] ata1: soft resetting port
[ 1193.369000] sr 1:0:0:0: resuming
[ 1193.369000] ata2: soft resetting port
[ 1193.369000] platform iTCO_wdt: resuming
[ 1193.369000] tifm_sd tifm_sd0:0: resuming
[ 1193.386000] ac97 0-0:AD1981B: resuming
[ 1193.386000] sonypi sonypi: resuming
[ 1193.387000] platform bluetooth: resuming
[ 1193.388000] Restarting tasks ... done.
[ 1193.409000] Enabling non-boot CPUs ...
[ 1193.523000] ata1.00: ata_hpa_resize 1: sectors = 78140160, hpa_sectors = 78140160
[ 1193.828000] ata2.00: configured for UDMA/33
[ 1193.828000] ata2: EH complete
[ 1194.022000] input: PS/2 Mouse as /class/input/input8
[ 1194.038000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input9
[ 1194.798000] ata1.00: limited to UDMA/33 due to 40-wire cable
[ 1194.869000] ata1.00: ata_hpa_resize 1: sectors = 78140160, hpa_sectors = 78140160
[ 1194.869000] ata1.00: configured for UDMA/33
[ 1194.869000] ata1: EH complete
[ 1194.883000] SCSI device sda: 78140160 512-byte hdwr sectors (40008 MB)
[ 1194.901000] sda: Write Protect is off
[ 1194.901000] sda: Mode Sense: 00 3a 00 00
[ 1194.908000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1196.387000] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI
[ 1196.387000] e100: Copyright(c) 1999-2006 Intel Corporation
[ 1196.389000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKE] -> GSI 9 (level, low) -> IRQ 9
[ 1196.418000] e100: eth0: e100_probe: addr 0xe0205000, irq 9, MAC addr 00:01:4A:06:D4:18
[ 1196.558000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[ 1196.559000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[ 1196.568000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1196.593000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[ 1196.594000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[ 1196.594000] ACPI: PCI Interrupt 0000:02:0b.0[A] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[ 1196.594000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[ 1196.949000] ipw2200: Detected geography ZZD (13 802.11bg channels, 0 802.11a channels)
[ 1197.387000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 1198.366000] input: Lid Switch as /class/input/input10
[ 1198.397000] ACPI: Lid Switch [LID0]
[ 1198.454000] input: Power Button (CM) as /class/input/input11
[ 1198.487000] ACPI: Power Button (CM) [PWRB]
[ 1199.579000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[ 1199.579000] ACPI: Processor [CPU0] (supports 8 throttling states)
[ 1199.588000] ACPI: Thermal Zone [ATF0] (40 C)
[ 1199.668000] ACPI: AC Adapter [ACAD] (on-line)
[ 1199.695000] ACPI: Battery Slot [BAT1] (battery present)
[ 1200.223000] CCMP: replay detected: STA=00:17:3f:5e:5b:4b previous PN 000000000000 received PN 000000000000
[ 1207.793000] eth1: no IPv6 routers present
[ 1222.579000] eth1: no IPv6 routers present
[ 1814.789000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1819.999000] ACPI: PCI interrupt for device 0000:02:08.0 disabled
[ 1820.377000] ACPI: PCI interrupt for device 0000:02:0b.0 disabled
[ 1827.640000] PM: Preparing system for mem sleep
[ 1827.640000] Disabling non-boot CPUs ...
[ 1827.640000] Stopping tasks ... done.
[ 1828.042000] Suspending console(s)
[ 1828.042000] platform bluetooth: suspend
[ 1828.042000] sonypi sonypi: suspend
[ 1828.043000] ac97 0-0:AD1981B: suspend
[ 1828.043000] tifm_sd tifm_sd0:0: suspend
[ 1828.043000] platform iTCO_wdt: suspend
[ 1828.043000] sr 1:0:0:0: suspend
[ 1828.043000] sd 0:0:0:0: suspend
[ 1829.512000]  usbdev3.1_ep81: PM: suspend 0->2, parent 3-0:1.0 already 2
[ 1829.512000] hub 3-0:1.0: PM: suspend 2-->2
[ 1829.512000] hub 3-0:1.0: PM: suspend 2->2, parent usb3 already 2
[ 1829.512000]  usbdev3.1_ep00: PM: suspend 0->2, parent usb3 already 2
[ 1829.512000] usb usb3: PM: suspend 2-->2
[ 1829.512000]  usbdev2.1_ep81: PM: suspend 0->2, parent 2-0:1.0 already 2
[ 1829.512000] hub 2-0:1.0: PM: suspend 2-->2
[ 1829.512000] hub 2-0:1.0: PM: suspend 2->2, parent usb2 already 2
[ 1829.512000]  usbdev2.1_ep00: PM: suspend 0->2, parent usb2 already 2
[ 1829.512000] usb usb2: PM: suspend 2-->2
[ 1829.512000]  usbdev1.1_ep81: PM: suspend 0->2, parent 1-0:1.0 already 2
[ 1829.512000] hub 1-0:1.0: PM: suspend 2-->2
[ 1829.512000] hub 1-0:1.0: PM: suspend 2->2, parent usb1 already 2
[ 1829.512000]  usbdev1.1_ep00: PM: suspend 0->2, parent usb1 already 2
[ 1829.512000] usb usb1: PM: suspend 2-->2
[ 1829.512000] platform vesafb.0: suspend
[ 1829.512000] platform eisa.0: suspend
[ 1829.512000] i8042 i8042: suspend
[ 1830.114000] serial8250 serial8250: suspend
[ 1830.114000] platform pcspkr: suspend
[ 1830.114000] i8042 aux 00:08: suspend
[ 1830.114000] i8042 kbd 00:07: suspend
[ 1830.114000] pnp 00:06: suspend
[ 1830.114000] pnp 00:05: suspend
[ 1830.114000] system 00:04: suspend
[ 1830.114000] pnp 00:03: suspend
[ 1830.114000] pnp 00:02: suspend
[ 1830.114000] pnp 00:01: suspend
[ 1830.114000] pnp 00:00: suspend
[ 1830.114000] pci 0000:02:0b.0: suspend
[ 1830.114000] pci 0000:02:08.0: suspend
[ 1830.114000] tifm_7xx1 0000:02:04.3: suspend
[ 1830.114000] ACPI: PCI interrupt for device 0000:02:04.3 disabled
[ 1830.125000] ohci1394 0000:02:04.2: suspend
[ 1830.125000] ohci1394 does not fully support suspend and resume yet
[ 1830.125000] ieee1394: hpsb_bus_reset called while bus reset already in progress
[ 1830.136000] yenta_cardbus 0000:02:04.0: suspend
[ 1830.136000] pci 0000:00:1f.6: suspend
[ 1830.136000] Intel ICH 0000:00:1f.5: suspend
[ 1830.136000] ACPI: PCI interrupt for device 0000:00:1f.5 disabled
[ 1830.136000] pci 0000:00:1f.3: suspend
[ 1830.136000] ata_piix 0000:00:1f.1: suspend
[ 1830.139000] ACPI: Unable to derive IRQ for device 0000:00:1f.1
[ 1830.139000] pci_set_power_state(): 0000:00:1f.1: state=3, current state=5
[ 1830.139000] pci 0000:00:1f.0: suspend
[ 1830.139000] pci 0000:00:1e.0: suspend
[ 1830.139000] ehci_hcd 0000:00:1d.7: suspend, may wakeup
[ 1830.139000] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
[ 1830.150000] uhci_hcd 0000:00:1d.1: suspend
[ 1830.150000] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
[ 1830.150000] uhci_hcd 0000:00:1d.0: suspend
[ 1830.150000] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
[ 1830.150000] pci 0000:00:02.1: suspend
[ 1830.150000] pci 0000:00:02.0: suspend
[ 1830.150000] pci 0000:00:00.3: suspend
[ 1830.150000] pci 0000:00:00.1: suspend
[ 1830.150000] agpgart-intel 0000:00:00.0: suspend
[ 1830.150000] acpi acpi: suspend
[ 1830.150000] PM: Entering mem sleep
[ 1830.150000] platform bluetooth: LATE suspend
[ 1830.150000] sonypi sonypi: LATE suspend
[ 1830.150000] platform iTCO_wdt: LATE suspend
[ 1830.150000] platform vesafb.0: LATE suspend
[ 1830.150000] platform eisa.0: LATE suspend
[ 1830.150000] i8042 i8042: LATE suspend
[ 1830.150000] serial8250 serial8250: LATE suspend
[ 1830.150000] platform pcspkr: LATE suspend
[ 1830.150000] pci 0000:02:0b.0: LATE suspend
[ 1830.150000] pci 0000:02:08.0: LATE suspend
[ 1830.150000] tifm_7xx1 0000:02:04.3: LATE suspend
[ 1830.150000] ohci1394 0000:02:04.2: LATE suspend
[ 1830.150000] yenta_cardbus 0000:02:04.0: LATE suspend
[ 1830.150000] pci 0000:00:1f.6: LATE suspend
[ 1830.150000] Intel ICH 0000:00:1f.5: LATE suspend
[ 1830.150000] pci 0000:00:1f.3: LATE suspend
[ 1830.150000] pci 0000:00:1f.0: LATE suspend
[ 1830.150000] pci 0000:00:1e.0: LATE suspend
[ 1830.150000] pci 0000:00:02.1: LATE suspend
[ 1830.150000] pci 0000:00:02.0: LATE suspend
[ 1830.150000] pci 0000:00:00.3: LATE suspend
[ 1830.150000] pci 0000:00:00.1: LATE suspend
[ 1830.150000] agpgart-intel 0000:00:00.0: LATE suspend
[ 1830.150000] Back to C!
[45243.150000] agpgart-intel 0000:00:00.0: EARLY resume
[45243.150000] pci 0000:00:00.1: EARLY resume
[45243.150000] pci 0000:00:00.3: EARLY resume
[45243.150000] pci 0000:00:02.0: EARLY resume
[45243.150000] pci 0000:00:02.1: EARLY resume
[45243.150000] uhci_hcd 0000:00:1d.0: EARLY resume
[45243.150000] uhci_hcd 0000:00:1d.1: EARLY resume
[45243.150000] ehci_hcd 0000:00:1d.7: EARLY resume
[45243.150000] pci 0000:00:1e.0: EARLY resume
[45243.150000] pci 0000:00:1f.0: EARLY resume
[45243.150000] ata_piix 0000:00:1f.1: EARLY resume
[45243.150000] pci 0000:00:1f.3: EARLY resume
[45243.150000] Intel ICH 0000:00:1f.5: EARLY resume
[45243.150000] pci 0000:00:1f.6: EARLY resume
[45243.150000] yenta_cardbus 0000:02:04.0: EARLY resume
[45243.150000] ohci1394 0000:02:04.2: EARLY resume
[45243.150000] tifm_7xx1 0000:02:04.3: EARLY resume
[45243.150000] pci 0000:02:08.0: EARLY resume
[45243.150000] pci 0000:02:0b.0: EARLY resume
[45243.150000] platform pcspkr: EARLY resume
[45243.150000] serial8250 serial8250: EARLY resume
[45243.150000] i8042 i8042: EARLY resume
[45243.150000] platform eisa.0: EARLY resume
[45243.150000] platform vesafb.0: EARLY resume
[45243.150000] platform iTCO_wdt: EARLY resume
[45243.150000] sonypi sonypi: EARLY resume
[45243.150000] platform bluetooth: EARLY resume
[45243.165000] PM: Finishing wakeup.
[45243.165000] acpi acpi: resuming
[45243.166000] agpgart-intel 0000:00:00.0: resuming
[45243.166000] PM: Writing back config space on device 0000:00:02.0 at offset f (was 100, writing 109)
[45243.176000] pci 0000:00:00.1: resuming
[45243.176000] pci 0000:00:00.3: resuming
[45243.176000] pci 0000:00:02.0: resuming
[45243.176000] pci 0000:00:02.1: resuming
[45243.176000] PM: Writing back config space on device 0000:00:02.1 at offset 5 (was 0, writing e0080000)
[45243.176000] PM: Writing back config space on device 0000:00:02.1 at offset 4 (was 8, writing f0000008)
[45243.176000] PM: Writing back config space on device 0000:00:02.1 at offset 1 (was 900000, writing 900003)
[45243.176000] uhci_hcd 0000:00:1d.0: resuming
[45243.176000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 9 (level, low) -> IRQ 9
[45243.176000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[45243.176000] usb usb1: root hub lost power or was reset
[45243.176000] uhci_hcd 0000:00:1d.1: resuming
[45243.176000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[45243.176000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[45243.176000] usb usb2: root hub lost power or was reset
[45243.177000] ehci_hcd 0000:00:1d.7: resuming
[45243.188000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 9 (level, low) -> IRQ 9
[45243.188000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[45243.188000] pci 0000:00:1e.0: resuming
[45243.188000] PM: Writing back config space on device 0000:00:1e.0 at offset f (was 0, writing 40000)
[45243.188000] PM: Writing back config space on device 0000:00:1e.0 at offset 9 (was fff0, writing 23f02000)
[45243.188000] PM: Writing back config space on device 0000:00:1e.0 at offset 8 (was fff0, writing e020e020)
[45243.188000] PM: Writing back config space on device 0000:00:1e.0 at offset 7 (was 228000f0, writing 2803030)
[45243.188000] PM: Writing back config space on device 0000:00:1e.0 at offset 1 (was 80800001, writing 80800007)
[45243.188000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[45243.188000] pci 0000:00:1f.0: resuming
[45243.188000] ata_piix 0000:00:1f.1: resuming
[45243.188000] PM: Writing back config space on device 0000:00:1f.1 at offset f (was 100, writing 1ff)
[45243.188000] PM: Writing back config space on device 0000:00:1f.1 at offset 9 (was 0, writing 24000000)
[45243.188000] PM: Writing back config space on device 0000:00:1f.1 at offset 1 (was 2800003, writing 2800007)
[45243.188000] ACPI: Unable to derive IRQ for device 0000:00:1f.1
[45243.188000] ACPI: PCI Interrupt 0000:00:1f.1[A]: no GSI
[45243.188000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[45243.189000] pci 0000:00:1f.3: resuming
[45243.189000] Intel ICH 0000:00:1f.5: resuming
[45243.189000] PM: Writing back config space on device 0000:00:1f.5 at offset f (was 200, writing 209)
[45243.189000] PM: Writing back config space on device 0000:00:1f.5 at offset 7 (was 0, writing e0100800)
[45243.189000] PM: Writing back config space on device 0000:00:1f.5 at offset 6 (was 0, writing e0100c00)
[45243.189000] PM: Writing back config space on device 0000:00:1f.5 at offset 5 (was 1301, writing 18c1)
[45243.189000] PM: Writing back config space on device 0000:00:1f.5 at offset 4 (was 1201, writing 1c01)
[45243.189000] PM: Writing back config space on device 0000:00:1f.5 at offset 1 (was 2900005, writing 2900003)
[45243.189000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[45243.189000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[45244.192000] pci 0000:00:1f.6: resuming
[45244.192000] PM: Writing back config space on device 0000:00:1f.6 at offset f (was 200, writing 2ff)
[45244.192000] PM: Writing back config space on device 0000:00:1f.6 at offset 5 (was 1501, writing 2001)
[45244.192000] PM: Writing back config space on device 0000:00:1f.6 at offset 4 (was 1401, writing 2401)
[45244.192000] PM: Writing back config space on device 0000:00:1f.6 at offset 1 (was 2900005, writing 2900001)
[45244.192000] yenta_cardbus 0000:02:04.0: resuming
[45244.192000] PM: Writing back config space on device 0000:02:04.0 at offset f (was 34001ff, writing 5c00109)
[45244.192000] PM: Writing back config space on device 0000:02:04.0 at offset e (was 0, writing 38fc)
[45244.192000] PM: Writing back config space on device 0000:02:04.0 at offset d (was 0, writing 3800)
[45244.192000] PM: Writing back config space on device 0000:02:04.0 at offset c (was 0, writing 34fc)
[45244.192000] PM: Writing back config space on device 0000:02:04.0 at offset b (was 0, writing 3400)
[45244.192000] PM: Writing back config space on device 0000:02:04.0 at offset a (was 0, writing 2bfff000)
[45244.192000] PM: Writing back config space on device 0000:02:04.0 at offset 9 (was 0, writing 28000000)
[45244.192000] PM: Writing back config space on device 0000:02:04.0 at offset 8 (was 0, writing 23fff000)
[45244.192000] PM: Writing back config space on device 0000:02:04.0 at offset 7 (was 0, writing 20000000)
[45244.192000] PM: Writing back config space on device 0000:02:04.0 at offset 6 (was 0, writing b0060302)
[45244.192000] PM: Writing back config space on device 0000:02:04.0 at offset 4 (was 0, writing e0208000)
[45244.192000] PM: Writing back config space on device 0000:02:04.0 at offset 3 (was 820000, writing 82a820)
[45244.192000] PM: Writing back config space on device 0000:02:04.0 at offset 1 (was 2100000, writing 2100007)
[45244.192000] ohci1394 0000:02:04.2: resuming
[45244.203000] PM: Writing back config space on device 0000:02:04.2 at offset f (was 4030300, writing 40303ff)
[45244.203000] PM: Writing back config space on device 0000:02:04.2 at offset 5 (was 0, writing e0200000)
[45244.203000] PM: Writing back config space on device 0000:02:04.2 at offset 4 (was 0, writing e0207000)
[45244.203000] PM: Writing back config space on device 0000:02:04.2 at offset 3 (was 800000, writing 804010)
[45244.203000] PM: Writing back config space on device 0000:02:04.2 at offset 1 (was 2100000, writing 2100016)
[45244.253000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[9]  MMIO=[e0207000-e02077ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[45244.253000] tifm_7xx1 0000:02:04.3: resuming
[45244.264000] PM: Writing back config space on device 0000:02:04.3 at offset 4 (was 0, writing e0204000)
[45244.264000] PM: Writing back config space on device 0000:02:04.3 at offset 3 (was 800000, writing 804010)
[45244.264000] PM: Writing back config space on device 0000:02:04.3 at offset 1 (was 2100000, writing 2100006)
[45244.264000] ACPI: PCI Interrupt 0000:02:04.3[B] -> Link [LNKF] -> GSI 5 (level, low) -> IRQ 5
[45244.286000] pci 0000:02:08.0: resuming
[45244.286000] pci 0000:02:0b.0: resuming
[45244.286000] PM: Writing back config space on device 0000:02:0b.0 at offset f (was 18030100, writing 18030109)
[45244.286000] PM: Writing back config space on device 0000:02:0b.0 at offset 4 (was 0, writing e0206000)
[45244.286000] PM: Writing back config space on device 0000:02:0b.0 at offset 3 (was 0, writing 4010)
[45244.286000] PM: Writing back config space on device 0000:02:0b.0 at offset 1 (was 2900000, writing 2900002)
[45244.286000] pnp 00:00: resuming
[45244.286000] pnp 00:01: resuming
[45244.286000] pnp 00:02: resuming
[45244.286000] pnp 00:03: resuming
[45244.286000] system 00:04: resuming
[45244.286000] pnp 00:05: resuming
[45244.286000] pnp 00:06: resuming
[45244.286000] i8042 kbd 00:07: resuming
[45244.286000] pnp: Device 00:07 does not support activation.
[45244.286000] i8042 aux 00:08: resuming
[45244.286000] pnp: Device 00:08 does not support activation.
[45244.286000] platform pcspkr: resuming
[45244.286000] serial8250 serial8250: resuming
[45244.286000] i8042 i8042: resuming
[45244.287000] atkbd serio0: resuming
[45244.321000] platform eisa.0: resuming
[45244.321000] psmouse serio1: resuming
[45244.340000] platform vesafb.0: resuming
[45244.340000] usb usb1: resuming
[45244.372000] usb usb2: resuming
[45244.404000]  usbdev3.1_ep00: PM: resume from 0, parent usb3 still 2
[45244.404000]  usbdev3.1_ep81: PM: resume from 0, parent 3-0:1.0 still 2
[45244.404000] sd 0:0:0:0: resuming
[45244.404000] ata1: soft resetting port
[45244.404000] sr 1:0:0:0: resuming
[45244.404000] ata2: soft resetting port
[45244.404000] platform iTCO_wdt: resuming
[45244.404000] tifm_sd tifm_sd0:0: resuming
[45244.421000] ac97 0-0:AD1981B: resuming
[45244.421000] sonypi sonypi: resuming
[45244.422000] platform bluetooth: resuming
[45244.423000] Restarting tasks ... done.
[45244.457000] Enabling non-boot CPUs ...
[45244.559000] ata1.00: ata_hpa_resize 1: sectors = 78140160, hpa_sectors = 78140160
[45244.860000] ata2.00: configured for UDMA/33
[45244.860000] ata2: EH complete
[45245.069000] input: PS/2 Mouse as /class/input/input12
[45245.085000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input13
[45245.829000] ata1.00: ata_hpa_resize 1: sectors = 78140160, hpa_sectors = 78140160
[45245.829000] ata1.00: configured for UDMA/33
[45245.829000] ata1: EH complete
[45245.865000] SCSI device sda: 78140160 512-byte hdwr sectors (40008 MB)
[45245.875000] sda: Write Protect is off
[45245.875000] sda: Mode Sense: 00 3a 00 00
[45245.876000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[45249.684000] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI
[45249.684000] e100: Copyright(c) 1999-2006 Intel Corporation
[45249.684000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKE] -> GSI 9 (level, low) -> IRQ 9
[45249.708000] e100: eth0: e100_probe: addr 0xe0205000, irq 9, MAC addr 00:01:4A:06:D4:18
[45250.032000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[45250.033000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[45250.340000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[45250.340000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[45250.342000] ACPI: PCI Interrupt 0000:02:0b.0[A] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[45250.342000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[45251.093000] ipw2200: Detected geography ZZD (13 802.11bg channels, 0 802.11a channels)
[45251.217000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[45252.857000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[45253.752000] input: Lid Switch as /class/input/input14
[45253.753000] ACPI: Lid Switch [LID0]
[45253.754000] input: Power Button (CM) as /class/input/input15
[45253.755000] ACPI: Power Button (CM) [PWRB]
[45255.741000] CCMP: replay detected: STA=00:17:3f:5e:5b:4b previous PN 000000000000 received PN 000000000000
[45256.140000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[45256.140000] ACPI: Processor [CPU0] (supports 8 throttling states)
[45256.260000] ACPI: Thermal Zone [ATF0] (36 C)
[45256.518000] ACPI: AC Adapter [ACAD] (on-line)
[45256.620000] ACPI: Battery Slot [BAT1] (battery present)
[45263.589000] eth1: no IPv6 routers present
[45277.015000] eth1: no IPv6 routers present
[48328.838000] tifm_7xx1: ms card detected in socket 1

---

### Post by teguh.umar on 2007-11-09
I also have same problem with My NEC versa E3100, the internal card reader can read SD/MMC card but not Prostick Duo, have any idea

---

### Post by wieman01 on 2007-11-09
As far as I know, Duo's are not supported by Linux at the moment. It is recognized by the kernel as such, but you won't be able to use it.

I have an old Vaio as well, but it has never worked for me.

---

### Post by teguh.umar on 2007-11-12
:popcorn:  it might be not the answer of our problem, but at least prostick duo is able to read and write with ubuntu.here we go... I just test with putting my "All in one memory Card Reader" and put my prostick duo in it, voila....:) It appear at my desktop, and I can read and write it.. :guitar:

Note : Sory for my bad english

---

