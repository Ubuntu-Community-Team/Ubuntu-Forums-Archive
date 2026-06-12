---
title: "Karmic 9.10 doesn't recognize my internal microphone"
date: 2010-01-24
forum: Hardware
---

### Post by aj_the_first on 2010-01-24
I am using 9.10 karmic koala on my msi EX625 laptop, and the OS does not recognize the internal microphone.  At first I thought it was just a problem in Skype, but as I started digging further, I realized that there are no functioning capture devices.
I searched all the threads, and I ensured that the mic was not muted or turned down in any other program.  As I boost the mic in mixer, I can see the feedback cause the "input" to go up, and in pulseaudio I can see the same thing.
As far as I can tell, it thinks that the two speaks ARE the microphones, because the computer is showing two, and the speakers audibly give feedback when I turn up the two mic mixers and booster/amp, and the feedback shows in the GUI, and when I just boost the left "mic", the left speaker makes static, and the same on the right.  Also, in pulseaudio device chooser, the internal audio card is in "analog stereo duplex", but all the other digital/analog or full digital other options just shut down the sound and the mic (well,... the feedback stops in the GUI)
So, anyway that I can get the computer/OS to recognize the internal mic?
Thanks,
AJ

---

### Post by Jesdisciple on 2010-01-25
I seem to be having the same problem on an Acer TravelMate 3260.```
$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 0110
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 0110
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d0300000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at d0400000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 0110
	Flags: bus master, fast devsel, latency 0
	Memory at d0380000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 0110
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d0440000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 44000000-440fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: 44100000-441fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 0110
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 0110
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 0110
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 0110
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1880 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20)
	Subsystem: Acer Incorporated [ALI] Device 0110
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at d0644000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0e, sec-latency=56
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: d0200000-d02fffff
	Prefetchable memory behind bridge: 0000000040000000-0000000043ffffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 0110
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
	Subsystem: Acer Incorporated [ALI] Device 0110
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 18b0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 0110
	Flags: medium devsel, IRQ 10
	I/O ports at 18c0 [size=32]
	Kernel modules: i2c-i801

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
	Subsystem: Acer Incorporated [ALI] Device 0110
	Flags: bus master, fast devsel, latency 0, IRQ 27
	Memory at 44000000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at 2000 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sky2
	Kernel modules: sky2

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
	Subsystem: Intel Corporation Device 1000
	Flags: bus master, fast devsel, latency 0, IRQ 28
	Memory at 44100000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: iwl3945
	Kernel modules: iwl3945

0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
	Subsystem: Acer Incorporated [ALI] Device 0110
	Flags: bus master, medium devsel, latency 168, IRQ 20
	Memory at d0204000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=0a, secondary=0b, subordinate=0e, sec-latency=176
	Memory window 0: 40000000-43fff000 (prefetchable)
	Memory window 1: 48000000-4bfff000
	I/O window 0: 00003000-000030ff
	I/O window 1: 00003400-000034ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
	Subsystem: Acer Incorporated [ALI] Device 0110
	Flags: bus master, medium devsel, latency 57, IRQ 20
	Memory at d0205000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: tifm_7xx1
	Kernel modules: tifm_7xx1
```

---

