---
title: "[SOLVED] Sound Problems/Distortion in Intrepid"
date: 2008-11-07
forum: Hardware
---

### Post by seanlano on 2008-11-07
I have a Thinkpad R61i, and I recently updated it from 8.04.1 (via a clean install) and am now noticing sound playback problems. When Ubuntu starts, the logon sound is distorted for the lower frequencies, and the same happens when I play music. I have tried using all of the available "Sound playback" devices (i.e. OSS, ALSA, PulseAudio and also HDA Intel CONEXANT Analog in both OSS and ALSA varieties) and all of them result in all sounds being distorted. I read something about it maybe being a problem with the internal speaker, but it was already blacklisted and I also get these problems through headphones. The playback also seems to lag a bit when it distorts. Any ideas on how to fix this?

---

### Post by seanlano on 2008-11-12
anyone have any ideas?

---

### Post by MattBD on 2008-11-12
I've experienced the same problem in Ubuntu Intrepid on my Philips X58, but this was fine in Hardy. I'm going to have another go at it this weekend as I got fed up with it and went back to Hardy, but I'm eager to use Intrepid.

You might want to try this thread for ideas:
[http://ph.ubuntuforums.com/showthread.php?t=945401](http://ph.ubuntuforums.com/showthread.php?t=945401)

Also, you might want to run the following commands in the terminal and post the results here as they will give people more to work with:
```
lspci -v
```
```
aplay -l
```

---

### Post by seanlano on 2008-11-13
OK, thanks for that. Good to know I'm not alone, and also good to know that the problem isn't just on a Thinkpad. 

The command: 
```
sudo lspci -v
```
Got me this:
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
	Subsystem: Lenovo Device 20b3
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
	Subsystem: Lenovo Device 20b5
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f8100000 (64-bit, non-prefetchable) [size=1M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [d0] Power Management version 3
	Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
	Subsystem: Lenovo Device 20b5
	Flags: bus master, fast devsel, latency 0
	Memory at f8200000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: [d0] Power Management version 3

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: Lenovo Device 20aa
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: Lenovo Device 20aa
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: Lenovo Device 20ab
	Flags: bus master, medium devsel, latency 0, IRQ 22
	Memory at fe304800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Lenovo Device 20ac
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fe100000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: fc000000-fdffffff
	Prefetchable memory behind bridge: 00000000f8000000-00000000f80fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Lenovo Device 20ad
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: dc100000-df6fffff
	Prefetchable memory behind bridge: 00000000dfe00000-00000000dfefffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Lenovo Device 20ad
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Memory behind bridge: fe000000-fe0fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Lenovo Device 20ad
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=0c, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: d8000000-d9ffffff
	Prefetchable memory behind bridge: 00000000dfb00000-00000000dfbfffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Lenovo Device 20ad
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0d, subordinate=14, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: d4000000-d5ffffff
	Prefetchable memory behind bridge: 00000000df800000-00000000df8fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Lenovo Device 20ad
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: Lenovo Device 20aa
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: Lenovo Device 20aa
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 1880 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: Lenovo Device 20aa
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 18a0 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: Lenovo Device 20ab
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at fe304c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=15, subordinate=18, sec-latency=32
	I/O behind bridge: 00006000-00009fff
	Memory behind bridge: f8300000-fbffffff
	Prefetchable memory behind bridge: 00000000f4000000-00000000f7ffffff
	Capabilities: [50] Subsystem: Lenovo Device 20ae

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
	Subsystem: Lenovo Device 20a5
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel modules: iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Lenovo Device 20a6
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01)
	Subsystem: Lenovo Device 20a7
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 218
	I/O ports at 1c00 [size=8]
	I/O ports at 18d4 [size=4]
	I/O ports at 18d8 [size=8]
	I/O ports at 18d0 [size=4]
	I/O ports at 18e0 [size=32]
	Memory at fe304000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/2 Enable+
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] SATA HBA <?>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: Lenovo Device 20a9
	Flags: medium devsel, IRQ 11
	Memory at fe305000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 1c20 [size=32]
	Kernel modules: i2c-i801

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
	Subsystem: Intel Corporation Device 1010
	Flags: bus master, fast devsel, latency 0, IRQ 216
	Memory at df6ff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [c8] Power Management version 2
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [e0] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Device Serial Number 3b-4f-d6-ff-ff-bf-1c-00
	Kernel driver in use: iwl3945
	Kernel modules: iwl3945

04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
	Subsystem: Lenovo Device 20d5
	Flags: bus master, fast devsel, latency 0, IRQ 217
	Memory at fe000000 (64-bit, non-prefetchable) [size=64K]
	Expansion ROM at <ignored> [disabled]
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Vital Product Data <?>
	Capabilities: [58] Vendor Specific Information <?>
	Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [d0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [13c] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 23-c2-90-fe-ff-25-1c-00
	Capabilities: [16c] Power Budgeting <?>
	Kernel driver in use: tg3
	Kernel modules: tg3

15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
	Subsystem: Lenovo Device 20c6
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at f8300000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=15, secondary=16, subordinate=17, sec-latency=176
	Memory window 0: f4000000-f7fff000 (prefetchable)
	Memory window 1: 88000000-8bfff000
	I/O window 0: 00006000-000060ff
	I/O window 1: 00006400-000064ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04) (prog-if 10)
	Subsystem: Lenovo Device 20c7
	Flags: bus master, medium devsel, latency 64, IRQ 17
	Memory at f8301000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [dc] Power Management version 2
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
	Subsystem: Lenovo Device 20c8
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at f8301800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff) (prog-if ff)
	!!! Unknown header type 7f
	Kernel driver in use: ricoh-mmc
	Kernel modules: ricoh_mmc

15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
	Subsystem: Lenovo Device 20ca
	Flags: medium devsel, IRQ 11
	Memory at f8302000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2

15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)
	Subsystem: Lenovo Device 20cb
	Flags: medium devsel, IRQ 11
	Memory at f8302400 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2

```

and:
```
sudo aplay -l
```
got me this:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by kentcb on 2008-11-14
You're definitely not alone. I have exactly the same laptop with exactly the same problem. Worked fine in Hardy, but sound in Intrepid is distorted no matter whether I use the laptop speakers or HQ headphones.

Here's my output from lspci -v:

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
	Subsystem: Lenovo Device 20b3
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
	Subsystem: Lenovo Device 20b5
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f8100000 (64-bit, non-prefetchable) [size=1M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [d0] Power Management version 3
	Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
	Subsystem: Lenovo Device 20b5
	Flags: bus master, fast devsel, latency 0
	Memory at f8200000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: [d0] Power Management version 3

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: Lenovo Device 20aa
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: Lenovo Device 20aa
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: Lenovo Device 20ab
	Flags: bus master, medium devsel, latency 0, IRQ 22
	Memory at fe304800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Lenovo Device 20ac
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fe100000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: fc000000-fdffffff
	Prefetchable memory behind bridge: 00000000f8000000-00000000f80fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Lenovo Device 20ad
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: dc100000-dfcfffff
	Prefetchable memory behind bridge: 00000000dfe00000-00000000dfefffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Lenovo Device 20ad
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Memory behind bridge: fe000000-fe0fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Lenovo Device 20ad
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: Lenovo Device 20aa
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: Lenovo Device 20aa
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 1880 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: Lenovo Device 20aa
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 18a0 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: Lenovo Device 20ab
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at fe304c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=15, subordinate=18, sec-latency=32
	I/O behind bridge: 00004000-00007fff
	Memory behind bridge: f8300000-fbffffff
	Prefetchable memory behind bridge: 00000000f4000000-00000000f7ffffff
	Capabilities: [50] Subsystem: Lenovo Device 20ae

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
	Subsystem: Lenovo Device 20a5
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel modules: iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Lenovo Device 20a6
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01)
	Subsystem: Lenovo Device 20a7
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 220
	I/O ports at 1c00 [size=8]
	I/O ports at 18d4 [size=4]
	I/O ports at 18d8 [size=8]
	I/O ports at 18d0 [size=4]
	I/O ports at 18e0 [size=32]
	Memory at fe304000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/2 Enable+
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] SATA HBA <?>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: Lenovo Device 20a9
	Flags: medium devsel, IRQ 11
	Memory at fe305000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 1c20 [size=32]
	Kernel modules: i2c-i801

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
	Subsystem: Intel Corporation Device 1011
	Flags: bus master, fast devsel, latency 0, IRQ 218
	Memory at dfcff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [c8] Power Management version 2
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [e0] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Device Serial Number bb-47-67-ff-ff-3c-1f-00
	Kernel driver in use: iwl3945
	Kernel modules: iwl3945

04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
	Subsystem: Lenovo Device 20d5
	Flags: bus master, fast devsel, latency 0, IRQ 219
	Memory at fe000000 (64-bit, non-prefetchable) [size=64K]
	Expansion ROM at <ignored> [disabled]
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Vital Product Data <?>
	Capabilities: [58] Vendor Specific Information <?>
	Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [d0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [13c] Virtual Channel <?>
	Capabilities: [160] Device Serial Number a3-ff-91-fe-ff-25-1c-00
	Capabilities: [16c] Power Budgeting <?>
	Kernel driver in use: tg3
	Kernel modules: tg3

15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b6)
	Subsystem: Lenovo Device 20c4
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at f8300000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=15, secondary=16, subordinate=17, sec-latency=176
	Memory window 0: f4000000-f7fff000 (prefetchable)
	Memory window 1: 50000000-53fff000
	I/O window 0: 00004000-000040ff
	I/O window 1: 00004400-000044ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

```

And from aplay -l:

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Any help much appreciated.

---

### Post by kentcb on 2008-11-14
Also, I found [this thread]("http://ubuntuforums.org/showthread.php?t=967033&highlight=r61i") that seems to suggest a simple change to PCM level will solve the problem. However, if I run alsamixer I see no PCM level - only Playback and Capture.

---

### Post by newoga on 2008-11-18
I am also having sound distortion issues on my Acer TM6292. What is weird is the sound seemed to work fine after my initial upgrade from Hardy (I did an upgrade as opposed to fresh install this past Saturday). It was just these past couple days in which I have been having issues. Did you all do an upgrade as well or a fresh install?

I checked the ALSA mixer and I do see PCM level under my "HDA Intel (Alsa)" Device in the Playback Tab however when I adjusted it the distortion did not go away.

Command: 
```
lspci -v
```

Returns:
```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 011b
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 011b
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0000000 (64-bit, non-prefetchable) [size=1M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Capabilities: <access denied>
	Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 011b
	Flags: bus master, fast devsel, latency 0
	Memory at f0100000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 011b
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 011b
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: Acer Incorporated [ALI] Device 011b
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at f0704000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 011b
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f0500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Memory behind bridge: c2000000-c20fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	Memory behind bridge: c2100000-c21fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 011b
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 011b
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1880 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 011b
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 18a0 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: Acer Incorporated [ALI] Device 011b
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f0704400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0e, sec-latency=32
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: f0400000-f04fffff
	Prefetchable memory behind bridge: 00000000c4000000-00000000c7ffffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 011b
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Acer Incorporated [ALI] Device 011b
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Acer Incorporated [ALI] Device 011b
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 1c00 [size=8]
	I/O ports at 18f4 [size=4]
	I/O ports at 18f8 [size=8]
	I/O ports at 18f0 [size=4]
	I/O ports at 18e0 [size=16]
	I/O ports at 18d0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 011b
	Flags: medium devsel, IRQ 10
	Memory at c2200000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 1c20 [size=32]
	Kernel modules: i2c-i801

04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 011b
	Flags: bus master, fast devsel, latency 0, IRQ 220
	Memory at c2000000 (64-bit, non-prefetchable) [size=64K]
	Expansion ROM at <ignored> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: tg3
	Kernel modules: tg3

05:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
	Subsystem: Intel Corporation Device 1100
	Flags: bus master, fast devsel, latency 0, IRQ 219
	Memory at c2100000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

0a:01.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
	Subsystem: Acer Incorporated [ALI] Device 011b
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at f0404000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=0a, secondary=0b, subordinate=0e, sec-latency=176
	Memory window 0: c4000000-c7fff000 (prefetchable)
	Memory window 1: c8000000-cbfff000
	I/O window 0: 00002000-000020ff
	I/O window 1: 00002400-000024ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

0a:02.0 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
	Subsystem: Acer Incorporated [ALI] Device 011b
	Flags: bus master, medium devsel, latency 32, IRQ 11
	Memory at f0405800 (32-bit, non-prefetchable) [size=128]
	Capabilities: <access denied>

0a:02.1 SD Host controller: ENE Technology Inc ENE PCI SmartMedia / xD Card Reader Controller (prog-if 01)
	Subsystem: Acer Incorporated [ALI] Device 011b
	Flags: bus master, medium devsel, latency 32, IRQ 17
	Memory at f0405c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

0a:02.2 FLASH memory: ENE Technology Inc Memory Stick Card Reader Controller
	Subsystem: Acer Incorporated [ALI] Device 011b
	Flags: bus master, medium devsel, latency 32, IRQ 255
	Memory at f0406000 (32-bit, non-prefetchable) [size=128]
	Capabilities: <access denied>

0a:02.3 FLASH memory: ENE Technology Inc ENE PCI Secure Digital / MMC Card Reader Controller
	Subsystem: Acer Incorporated [ALI] Device 011b
	Flags: medium devsel, IRQ 17
	Memory at f0405900 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

0a:09.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10)
	Subsystem: Acer Incorporated [ALI] Device 011b
	Flags: bus master, medium devsel, latency 32, IRQ 20
	Memory at f0405000 (32-bit, non-prefetchable) [size=2K]
	Memory at f0400000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394
```

This:

```
sudo aplay -l

```

Returns:

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

I'm looking into updating ALSA. I used the following command to figure out what version of ALSA I was running:

```
cat /proc/asound/version
```

It returned: 

Advanced Linux Sound Architecture Driver Version 1.0.17.

The latest stable released at the [www.alsa-project.org]("http://www.alsa-project.org") [download section]("http://www.alsa-project.org/main/index.php/Download") is 1.0.18a

---

### Post by seanlano on 2008-11-19
> Also, I found this thread that seems to suggest a simple change to PCM level will solve the problem. However, if I run alsamixer I see no PCM level - only Playback and Capture.

I followed that thread and turned down the PCM level - and it worked! 

**SOLUTION:**

Run: ```
gnome-volume-control
``` (doesn't need sudo) and you should see three (at least I did) controls, master, PCM and input. Try turning down the PCM sliders a bit. NOTE: Don't turn them down too far or your volume will become really quiet - I suggest turning the master most of the way up (say 80%) then playing some music and then adjusting the PCM level to a suitable level (for me about 35%). This fixed my problems, it seems the PCM level is the pre-amp, and having it up too high caused it to clip, even if the master was turned down really low.

---

### Post by seanlano on 2008-11-19
Can others try this and see if it works? If so, I'll mark as solved.

---

### Post by teseglet on 2008-11-21
I had same problem, tried the above solution, reduced PCM about 10% and the problem went away.  Problem solved. Thanks

---

