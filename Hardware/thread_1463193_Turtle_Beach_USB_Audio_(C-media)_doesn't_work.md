---
title: "Turtle Beach USB Audio (C-media) doesn't work"
date: 2010-04-26
forum: Hardware
---

### Post by Toriam on 2010-04-26
Turtle Beach USB Audio (C-media) doesn't work with any applications, including firefox.
I use an external sound card to replace the internal sound on a laptop I have. Internal default sound doesn't work at all. I have had this working under Ubuntu recently, but doen't wrk under Xubuntu. I have installed GNOME alsamixer and alsamixergui, and have them set up just like I did in Ubuntu. I think I have things set up correctly everywhere else. I attached some photos. Interestingly, in the system settings, thee is no option for sound, no testing. I see where people have changed things in command line, but I'm hesitant to do that. I figured I could get it running about the same way I had it going in Ubuntu. Any ideas?

Here's output of several commands I saw others ran:

toriam@BethGateway:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [C-Media USB Audio       ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
toriam@BethGateway:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
	Subsystem: Rioworks Device 203e
	Flags: bus master, fast devsel, latency 0
	Memory at <unassigned> (32-bit, prefetchable)
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
	Subsystem: Rioworks Device 203e
	Flags: bus master, fast devsel, latency 0

00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
	Subsystem: Rioworks Device 203e
	Flags: bus master, fast devsel, latency 0

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
	Subsystem: Rioworks Device 203e
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at e8000000 (32-bit, prefetchable) [size=128M]
	Memory at e0000000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
	Subsystem: Rioworks Device 203e
	Flags: fast devsel
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Memory at e0080000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
	Subsystem: Rioworks Device 203e
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
	Subsystem: Rioworks Device 203e
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
	Subsystem: Rioworks Device 203e
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20)
	Subsystem: Rioworks Device 203e
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at e0100000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=06, sec-latency=216
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: e0200000-e02fffff
	Prefetchable memory behind bridge: 30000000-33ffffff
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Rioworks Device 203e
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]
	Memory at 34000000 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
	Subsystem: Rioworks Device 203e
	Flags: medium devsel, IRQ 10
	I/O ports at 1880 [size=32]
	Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
	Subsystem: Rioworks Device 203e
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 1c00 [size=256]
	I/O ports at 18c0 [size=64]
	Memory at e0100c00 (32-bit, non-prefetchable) [size=512]
	Memory at e0100800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
	Subsystem: Rioworks Device 2030
	Flags: medium devsel, IRQ 17
	I/O ports at 2400 [size=256]
	I/O ports at 2000 [size=128]
	Capabilities: <access denied>
	Kernel modules: snd-intel8x0m

02:07.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
	Subsystem: Rioworks Device 203e
	Flags: bus master, medium devsel, latency 168, IRQ 19
	Memory at e020a000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
	Memory window 0: 30000000-33fff000 (prefetchable)
	Memory window 1: 38000000-3bfff000
	I/O window 0: 00003000-000030ff
	I/O window 1: 00003400-000034ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

02:07.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller (prog-if 10)
	Subsystem: Rioworks Device 203e
	Flags: bus master, medium devsel, latency 32, IRQ 19
	Memory at e0209000 (32-bit, non-prefetchable) [size=2K]
	Memory at e0200000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

02:07.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
	Subsystem: Rioworks Device 203e
	Flags: bus master, medium devsel, latency 57, IRQ 19
	Memory at e0204000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: tifm_7xx1
	Kernel modules: tifm_7xx1

02:08.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
	Subsystem: Rioworks Device 203e
	Flags: bus master, fast devsel, latency 32, IRQ 17
	Memory at e0206000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: b44
	Kernel modules: b44

02:09.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
	Subsystem: Intel Corporation Device 2701
	Flags: bus master, medium devsel, latency 32, IRQ 17
	Memory at e0208000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ipw2200
	Kernel modules: ipw2200

toriam@BethGateway:~$ /proc/asound/cards
bash: /proc/asound/cards: Permission denied
toriam@BethGateway:~$ sudo /proc/asound/cards
[sudo] password for toriam: 
sudo: /proc/asound/cards: command not found
toriam@BethGateway:~$

---

### Post by Toriam on 2010-04-27
bump *OW*

---

### Post by Toriam on 2010-04-27
Hipityhopity hop!!!

---

### Post by Toriam on 2010-05-04
help?

---

