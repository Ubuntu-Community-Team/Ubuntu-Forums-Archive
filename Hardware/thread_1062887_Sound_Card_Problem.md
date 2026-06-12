---
title: "Sound Card Problem"
date: 2009-02-07
forum: Hardware
---

### Post by raunhar on 2009-02-07
Ubuntu 8.10
Dual boot with Win XP
Sound Card Realtek HD Audio

I installed Ubuntu 8.10 around 1 week back.
Till about 1 hr ago all the hardware was fine, but the sound has stopped. 
When I shut down the system, the beep sound comes, but while Ubuntu is running no sound. tried to check sound by running a music CD, but unsuccessful.

The sound card works well when I use Win XP

How to rectify the problem.

I was running Childplay (Games) when the sound stopped.

I had used this command just few minutes before the problem occurred.
gksu gedit /etc/rc.local
iwconfig wlan0 rate 5.5 fixed  (added this line before exit0)
This was done because the RTL 8187B wireless Lan was not working properly.

I did some checking with some commands (ubuntuforums). The result is as: File attached also
sudo lshw -c multimedia
  *-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel



~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
	Subsystem: QUANTA Computer Inc Device 0761
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
	Subsystem: QUANTA Computer Inc Device 0761
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0600000 (64-bit, non-prefetchable) [size=1M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Capabilities: <access denied>
	Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
	Subsystem: QUANTA Computer Inc Device 0761
	Flags: bus master, fast devsel, latency 0
	Memory at f0700000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: QUANTA Computer Inc Device 0761
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: QUANTA Computer Inc Device 0761
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: QUANTA Computer Inc Device 0761
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at f0c04000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: QUANTA Computer Inc Device 0761
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f0a00000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: f0800000-f08fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=07, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=09, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: f0400000-f05fffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f03fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: QUANTA Computer Inc Device 0761
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: QUANTA Computer Inc Device 0761
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1880 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: QUANTA Computer Inc Device 0761
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 18a0 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: QUANTA Computer Inc Device 0761
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f0c04400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0b, subordinate=0f, sec-latency=32
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: f0900000-f09fffff
	Prefetchable memory behind bridge: 0000000050000000-0000000053ffffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
	Subsystem: QUANTA Computer Inc Device 0761
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03) (prog-if 80 [Master])
	Subsystem: QUANTA Computer Inc Device 0761
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 18e0 [size=16]
	I/O ports at 18d0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: QUANTA Computer Inc Device 0761
	Flags: medium devsel, IRQ 10
	Memory at 54000000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 1c00 [size=32]
	Kernel modules: i2c-i801

04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
	Subsystem: QUANTA Computer Inc Device 0761
	Flags: bus master, fast devsel, latency 0, IRQ 219
	Memory at f0800000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at 2000 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sky2
	Kernel modules: sky2

0b:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
	Subsystem: QUANTA Computer Inc Device 0761
	Flags: bus master, medium devsel, latency 168, IRQ 20
	Memory at f0900000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=0b, secondary=0c, subordinate=0f, sec-latency=176
	Memory window 0: 50000000-53fff000 (prefetchable)
	Memory window 1: 58000000-5bfff000
	I/O window 0: 00004000-000040ff
	I/O window 1: 00004400-000044ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

0b:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10)
	Subsystem: QUANTA Computer Inc Device 0761
	Flags: bus master, medium devsel, latency 32, IRQ 21
	Memory at f0902000 (32-bit, non-prefetchable) [size=2K]
	Memory at f0904000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

0b:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
	Subsystem: QUANTA Computer Inc Device 0761
	Flags: bus master, medium devsel, latency 57, IRQ 20
	Memory at f0901000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: tifm_7xx1
	Kernel modules: tifm_7xx1

0b:09.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller (prog-if 01)
	Subsystem: QUANTA Computer Inc Device 0761
	Flags: bus master, medium devsel, latency 57, IRQ 20
	Memory at f0902800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci


$ sudo modprobe snd-
FATAL: Module snd_ not found.

---

