---
title: "no sound just popping noises"
date: 2011-05-12
forum: Hardware
---

### Post by schizo83 on 2011-05-12
Hi all,

I can find information on no sound and on popping noises but nothing on having no sound but having irregular popping noises at the same time. It just started today and I have no idea why.

I have check volume control and the likes. Reinstalled the ALSA stuff. Disabled and re-enabled the sound hardware. I unplugged the webcam, which also has a microphone in it. Nothing gave me any improvement.

There is one deterministic way I know to recreate the popping sound, in 'sound preferences'->'output' switch between 'analog output' and 'analog headphones'.

I used the ALSA tool to gather a bunch of information which is available at: [http://www.alsa-project.org/db/?f=ddb4c23211a1b553ea9828eb37cce16570ac5951](http://www.alsa-project.org/db/?f=ddb4c23211a1b553ea9828eb37cce16570ac5951)

Any support is greatly appreciated.

---

### Post by LinXNut on 2011-05-12
Hi! 

Could you please post your lspci?

Use this code:

```
lspci -v | less
```

This will show the kernel driver, and other items as well in use for your ATI.

---

### Post by schizo83 on 2011-05-13
Here you go. Strange thing happened. Next time I booted everything worked fine, I had sound and there were no popping noises. The time after that, still fine, and now it's the same deal again. No sound, just popping.

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
	Subsystem: Advanced Micro Devices [AMD] RS880 Host Bridge
	Flags: bus master, 66MHz, medium devsel, latency 0
	Capabilities: <access denied>

00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fa000000-fe6fffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fe700000-fe7fffff
	Prefetchable memory behind bridge: 00000000f8f00000-00000000f8ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: fe800000-fe8fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 4) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000d000-0000efff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] (rev 40) (prog-if 01 [AHCI 1.0])
	Subsystem: Micro-Star International Co., Ltd. Device 7623
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 45
	I/O ports at a000 [size=8]
	I/O ports at 9000 [size=4]
	I/O ports at 8000 [size=8]
	I/O ports at 7000 [size=4]
	I/O ports at 6000 [size=16]
	Memory at f9fffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Micro-Star International Co., Ltd. Device 7623
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at f9ffe000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Micro-Star International Co., Ltd. Device 7623
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at f9fff800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Micro-Star International Co., Ltd. Device 7623
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at f9ffd000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Micro-Star International Co., Ltd. Device 7623
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at f9fff400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
	Flags: 66MHz, medium devsel
	Kernel driver in use: piix4_smbus
	Kernel modules: sp5100_tco, i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller (rev 40) (prog-if 8a [Master SecP PriP])
	Subsystem: Micro-Star International Co., Ltd. Device 7623
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ff00 [size=16]
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
	Subsystem: Micro-Star International Co., Ltd. Device 7623
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
	Subsystem: Micro-Star International Co., Ltd. Device 7623
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=64
	Memory behind bridge: fe900000-fe9fffff

00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller (prog-if 10 [OHCI])
	Subsystem: Micro-Star International Co., Ltd. Device 7623
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at f9ffc000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Micro-Star International Co., Ltd. Device 7623
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at f9ff7000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Micro-Star International Co., Ltd. Device 7623
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at f9fff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
	Flags: fast devsel
	Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k10temp
	Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
	Flags: fast devsel

01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Device 823c
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at b800 [size=128]
	[virtual] Expansion ROM at fe6e0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nouveau, nvidiafb

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
	Subsystem: Micro-Star International Co., Ltd. Device 7623
	Flags: bus master, fast devsel, latency 0, IRQ 44
	I/O ports at c800 [size=256]
	Memory at f8fff000 (64-bit, prefetchable) [size=4K]
	Memory at f8ff8000 (64-bit, prefetchable) [size=16K]
	Expansion ROM at fe7e0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

03:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03) (prog-if 30 [XHCI])
	Subsystem: Micro-Star International Co., Ltd. Device 7623
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at fe8fa000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: xhci_hcd
	Kernel modules: xhci-hcd

04:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller (prog-if 85 [Master SecO PriO])
	Subsystem: Micro-Star International Co., Ltd. Device 7623
	Flags: bus master, fast devsel, latency 0, IRQ 17
	I/O ports at e800 [size=8]
	I/O ports at e400 [size=4]
	I/O ports at e000 [size=8]
	I/O ports at d800 [size=4]
	I/O ports at d400 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_jmicron
	Kernel modules: pata_jmicron

05:02.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
	Subsystem: Atheros Communications Inc. Device 3071
	Flags: bus master, 66MHz, medium devsel, latency 168, IRQ 20
	Memory at fe9f0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

```

---

### Post by schizo83 on 2011-05-13
I have rebooted three times, nothing changed. Turned of my computer for half a minute and booted it, and now it works...

I run windows 7 on this very same machine and never had a problem there so I do not suppose it would be a hardware issue. It seems to be a non-deterministic boot issue...

---

### Post by schizo83 on 2011-05-19
The problem reoccurred a day later but now it is gone again. 

Annoying, not knowing what is causing it and when it will be back again.
Anyone any idea?

---

