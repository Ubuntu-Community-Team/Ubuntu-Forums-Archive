---
title: "After 36hours, still no sound"
date: 2009-11-10
forum: Hardware
---

### Post by ProRok on 2009-11-10
Im a linux noob for starters. 
I have spent almost three full waking days learning the ropes of terminal and such, but mainly I've been trying to get my sound working. 

Im running an hp pavilion dv9608nr. 
Ive seen numerous fixes, and all of them have been from posts dated back to 2004 up to 2007, all these guys got it fixed, so Im assuming theres something out there that will eventually work.

I hope the below is useful.

@Prorok:~$ lspci -v
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
    Subsystem: Hewlett-Packard Company Device 30cf
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
    Subsystem: Hewlett-Packard Company Device 30cf
    Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
    Subsystem: Hewlett-Packard Company Device 30cf
    Flags: 66MHz, fast devsel, IRQ 10
    I/O ports at 3080 [size=64]
    I/O ports at 3040 [size=64]
    I/O ports at 3000 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2

00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
    Flags: 66MHz, fast devsel

00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
    Subsystem: Hewlett-Packard Company Device 30cf
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
    Memory at f6200000 (32-bit, non-prefetchable) [size=512K]

00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2) (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 30cf
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
    Memory at f6486000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 30cf
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at f6489000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2) (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 30cf
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
    Memory at f6487000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 30cf
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at f6489400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1) (prog-if 8a [Master SecP PriP])
    Subsystem: Hewlett-Packard Company Device 30cf
    Flags: bus master, 66MHz, fast devsel, latency 0
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    I/O ports at 30c0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_amd

00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
    Subsystem: Hewlett-Packard Company Device 30cf
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
    Memory at f6480000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: snd-hda-intel

00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2) (prog-if 01)
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
    Memory behind bridge: f6100000-f61fffff
    Capabilities: <access denied>

00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2) (prog-if 85 [Master SecO PriO])
    Subsystem: Hewlett-Packard Company Device 30cf
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 26
    I/O ports at 30f0 [size=8]
    I/O ports at 30e4 [size=4]
    I/O ports at 30e8 [size=8]
    I/O ports at 30e0 [size=4]
    I/O ports at 30d0 [size=16]
    Memory at f6484000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
    Subsystem: Hewlett-Packard Company Device 30cf
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 27
    Memory at f6488000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 30f8 [size=8]
    Memory at f6489c00 (32-bit, non-prefetchable) [size=256]
    Memory at f6489800 (32-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: f2000000-f3ffffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: f6000000-f60fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7150M / nForce 630M] (rev a2)
    Subsystem: Hewlett-Packard Company Device 30cf
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
    Memory at f5000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at f4000000 (64-bit, non-prefetchable) [size=16M]
    [virtual] Expansion ROM at 60000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Flags: fast devsel
    Capabilities: <access denied>
    Kernel driver in use: k8temp
    Kernel modules: k8temp

02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 30cf
    Flags: bus master, medium devsel, latency 64, IRQ 5
    Memory at f6100000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
    Subsystem: Hewlett-Packard Company Device 30cf
    Flags: bus master, medium devsel, latency 64, IRQ 7
    Memory at f6100800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
    Subsystem: Hewlett-Packard Company Device 30cf
    Flags: bus master, medium devsel, latency 64, IRQ 11
    Memory at f6100c00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ricoh-mmc
    Kernel modules: ricoh_mmc

02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
    Subsystem: Hewlett-Packard Company Device 30cf
    Flags: bus master, medium devsel, latency 64, IRQ 11
    Memory at f6101000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) (prog-if ff)
    !!! Unknown header type 7f

03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)
    Subsystem: Hewlett-Packard Company Device 1374
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at f6000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

---

### Post by kostkon on 2009-11-10
What version of Ubuntu are you using? Could you paste the output of
```
aplay -l
```

---

### Post by ProRok on 2009-11-10
when i used to type aplay -l itd give me :

card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital Audio [Conexant Digital Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


now it just says

~$ aplay -l
aplay: device_list:223: no soundcards found...

any ideas?

---

### Post by kostkon on 2009-11-10
Did anything happen that caused your card to stop working? Did you upgrade to 9.10, for example?

---

### Post by ProRok on 2009-11-10
well, I had a dual boot with vista and 9.10, but i never used vista, so i decided to go full ubuntu. I formated everything and installed 9.10

---

### Post by kostkon on 2009-11-10
Just to be sure. Could you install the
```
linux-backports-modules-alsa-karmic-generic
```
package and then reboot?

---

