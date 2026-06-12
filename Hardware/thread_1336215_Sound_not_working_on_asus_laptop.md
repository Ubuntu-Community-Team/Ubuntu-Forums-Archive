---
title: "Sound not working on asus laptop"
date: 2009-11-24
forum: Hardware
---

### Post by skerdziuzzz on 2009-11-24
Hello,
Ubuntu doesn't play any sounds when booted, although the startup sound plays, and wine also has sound.
No devices seem to show up on sound options. Everything works on windows, and I remember it worked for me on 9.04 or 8.10

---

### Post by pi4r0n on 2009-11-24
Have you even tried to look on this forum for any solutions ?? or just posted another **sound issue** post over here ??

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

For the future give more information card model config files etc...

Ta

pi4r0n

---

### Post by skerdziuzzz on 2009-11-24
Everything seems to be in order, only I have no sound in ubuntu. My sound card is some generic laptop card, and I have no idea how to look the model up in ubuntu. All that google says is Integrated Intel® High Definition Audio chip, which I guess is pretty common. As I said, sound works in wine for some reason. Those links you gave do help much, since I have been using ubuntu for two weeks.

---

### Post by pi4r0n on 2009-11-24
Type this in console and give info

1. **aplay -l**
2. **lspci -v**
3. **sudo nano /etc/modules**
4. **cat /proc/asound/cards**

then tell me you Desktop or Laptop model

Ta

pi4r0n

---

### Post by skerdziuzzz on 2009-11-25
1.
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0





2.
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
	Subsystem: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: f4000000-f7ffffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 8263
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at b880 [size=32]
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 8263
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at bc00 [size=32]
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 8263
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at f3fffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 8263
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at f3ff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Memory behind bridge: fbe00000-fbefffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: f8000000-fbdfffff
	Prefetchable memory behind bridge: 00000000dc000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 8263
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at b400 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 8263
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at b480 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 8263
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at b800 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 8263
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f3fff800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=32
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fbf00000-fbffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d00fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 8263
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. Device 8263
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]
	Kernel driver in use: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01)
	Subsystem: ASUSTeK Computer Inc. Device 8263
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 28
	I/O ports at b080 [size=8]
	I/O ports at b000 [size=4]
	I/O ports at ac00 [size=8]
	I/O ports at a880 [size=4]
	I/O ports at a800 [size=32]
	Memory at f3fff000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 8263
	Flags: medium devsel, IRQ 3
	Memory at d0100000 (32-bit, non-prefetchable) [disabled] [size=256]
	I/O ports at 0400 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8600M GS] (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 826c
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f7000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at f4000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at cc00 [size=128]
	[virtual] Expansion ROM at f6000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
	Subsystem: Intel Corporation Device 1000
	Flags: bus master, fast devsel, latency 0, IRQ 29
	Memory at fbeff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: iwl3945
	Kernel modules: iwl3945

06:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 8264
	Flags: bus master, medium devsel, latency 64, IRQ 16
	Memory at fbffe800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

06:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
	Subsystem: ASUSTeK Computer Inc. Device 8264
	Flags: bus master, medium devsel, latency 64, IRQ 17
	Memory at fbfff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

06:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
	Subsystem: ASUSTeK Computer Inc. Device 8264
	Flags: bus master, medium devsel, latency 64, IRQ 4
	Memory at fbfff400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ricoh-mmc
	Kernel modules: ricoh_mmc

06:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
	Subsystem: ASUSTeK Computer Inc. Device 8264
	Flags: bus master, medium devsel, latency 64, IRQ 4
	Memory at fbfff800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

06:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) (prog-if ff)
	!!! Unknown header type 7f

06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
	Subsystem: ASUSTeK Computer Inc. Device 1345
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	I/O ports at e800 [size=256]
	Memory at fbffe400 (32-bit, non-prefetchable) [size=256]
	Expansion ROM at d0000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169







3.
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc





4.
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf3ff8000 irq 21



My laptop model is asus s96s.

As I said it worked for me on 9.04 so it could be a 9.10 bug. But I'm obviously not the expert here.

---

### Post by pi4r0n on 2009-11-26
OK you can do 2 things

1. Try this [link]("http://ubuntuforums.org/showthread.php?t=755479")
2. If still does not work then [this one]("http://ubuntuforums.org/showthread.php?t=805532")

---

### Post by skerdziuzzz on 2009-11-26
But I don't need surround sound! My card is 2.0, or at least I don't use 5.1. I mean, I don't have sound at all. Anyway thanks for trying :)

---

### Post by skerdziuzzz on 2009-11-26
Thats what I get in my sound options screen
[IMG]http://img527.imageshack.us/img527/3134/nuotraukagarsonustatyma.png[/IMG]

---

### Post by skerdziuzzz on 2009-11-27
This forum really sucks.

---

