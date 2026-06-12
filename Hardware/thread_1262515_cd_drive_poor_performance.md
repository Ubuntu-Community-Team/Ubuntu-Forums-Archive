---
title: "cd drive poor performance"
date: 2009-09-10
forum: Hardware
---

### Post by jakeford18 on 2009-09-10
I have a Lite-On, 52x32x52 cd burner, but when I burn a cd, it usually only writes at 12.XX, and yes I am using blank cds that support speeds up to 48X. I checked lite-on's website, and while they do provide linux drivers, they're not in .DEB form, I believe the download if .tar.gz. Any help would be much appreciated

---

### Post by Fafler on 2009-09-10
```
sudo hdparm -d /dev/cdrom
```What command/program do you use?

EDIT: You shouldn't need drivers for this kind of device.

---

### Post by jakeford18 on 2009-09-10
my drive works....just very slow, I entered the code you gave in my post this is the message that I got

/dev/cdrom:
 HDIO_GET_DMA failed: Inappropriate ioctl for device

---

### Post by Fafler on 2009-09-10
You probably need to enable DMA transfers. What kind of controller is the card connected to?

```
lspci -v
```

---

### Post by jakeford18 on 2009-09-10
this is the output of lspci -v


00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
    Subsystem: Giga-byte Technology Device 5000
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
    Subsystem: Giga-byte Technology Device d000
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at e2000000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at c000 [size=8]
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    Memory at e2080000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>
    Kernel modules: intelfb

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
    Subsystem: Giga-byte Technology Device a002
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at e20c0000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at b000 [size=32]
    Kernel driver in use: uhci_hcd
    Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at b400 [size=32]
    Kernel driver in use: uhci_hcd
    Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at b800 [size=32]
    Kernel driver in use: uhci_hcd
    Kernel modules: uhci-hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at bc00 [size=32]
    Kernel driver in use: uhci_hcd
    Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20)
    Subsystem: Giga-byte Technology Device 5006
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at e20c4000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd
    Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: e0000000-e1ffffff
    Prefetchable memory behind bridge: 0000000080000000-00000000800fffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
    Subsystem: Giga-byte Technology Device 5001
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: intel-rng, iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
    Subsystem: Giga-byte Technology Device b001
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at f000 [size=16]
    Kernel driver in use: ata_piix
    Kernel modules: ata_generic, pata_acpi, ata_piix

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Giga-byte Technology Device b002
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at d400 [size=8]
    I/O ports at d800 [size=4]
    I/O ports at dc00 [size=8]
    I/O ports at e000 [size=4]
    I/O ports at e400 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix
    Kernel modules: ata_generic, pata_acpi, ata_piix

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
    Subsystem: Giga-byte Technology Device 5001
    Flags: medium devsel, IRQ 11
    I/O ports at 0500 [size=32]
    Kernel modules: i2c-i801

01:05.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
    Subsystem: Giga-byte Technology Device e000
    Flags: bus master, 66MHz, medium devsel, latency 96, IRQ 21
    Memory at e1000000 (32-bit, non-prefetchable) [size=16K]
    I/O ports at a000 [size=256]
    [virtual] Expansion ROM at 80000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: skge
    Kernel modules: skge

---

