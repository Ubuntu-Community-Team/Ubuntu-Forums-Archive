---
title: "Acer Aspire 6530 sound input"
date: 2010-03-20
forum: Hardware
---

### Post by extc on 2010-03-20
Hello folks,

No sound input is working on this machine. Output is fine and of good quality. AMD64 bit processor.

$ apport-collect -p alsa-base 359640 was tried but no report. It is complaining of not being authorized, although I logged into launchpad but there is no option to authorize it. Have looked over the forums but have not found a solution. Have tried all the different configurations in the sound preferences on the top bar.

Any help appreciated greatly, thanks.

Jim (On Karmic)

---

### Post by khelben1979 on 2010-03-20
You say that sound input don't work, can you describe more in detail about the problem if it's hardware or software problem? 

Maybe you're looking for [Pulse Audio]("http://en.wikipedia.org/wiki/Pulse_audio") to fix your problem?

---

### Post by extc on 2010-03-20
When we open the sound preferences in the top bar, and speak into the microphone, the level indicator does not move. We have tried recording in a number of applications, like Audacity. But nothing. Seems to be a hardware problem, ie bad drivers. Perhaps pulse-audio needs to be re-installed?

Thanks.

---

### Post by extc on 2010-03-21
lspci -v : (some of it)

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
    Subsystem: Acer Incorporated [ALI] Device 0166
    Flags: bus master, 66MHz, medium devsel, latency 64
    Capabilities: <access denied>

00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: cfe00000-cfefffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
    Memory behind bridge: f0300000-f03fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 4)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: f0200000-f02fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (prog-if 01)
    Subsystem: Acer Incorporated [ALI] Device 0166
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
    I/O ports at 8430 [size=8]
    I/O ports at 8424 [size=4]
    I/O ports at 8428 [size=8]
    I/O ports at 8420 [size=4]
    I/O ports at 8400 [size=16]
    Memory at f0408000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
    Subsystem: Acer Incorporated [ALI] Device 0166
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at f0404000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
    Subsystem: Acer Incorporated [ALI] Device 0166
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at f0405000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
    Subsystem: Acer Incorporated [ALI] Device 0166
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at f0408400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
    Subsystem: Acer Incorporated [ALI] Device 0166
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f0406000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
    Subsystem: Acer Incorporated [ALI] Device 0166
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f0407000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
    Subsystem: Acer Incorporated [ALI] Device 0166
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at f0408800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
    Subsystem: Acer Incorporated [ALI] Device 0166
    Flags: 66MHz, medium devsel
    Capabilities: <access denied>
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (prog-if 8a [Master SecP PriP])
    Subsystem: Acer Incorporated [ALI] Device 0166
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 8410 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: Acer Incorporated [ALI] Device 0166
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at f0400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
    Subsystem: Acer Incorporated [ALI] Device 0166
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=0a, subordinate=0f, sec-latency=64

00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
    Flags: fast devsel
    Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
    Flags: fast devsel
    Capabilities: <access denied>

00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
    Flags: fast devsel

01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650
    Subsystem: Acer Incorporated [ALI] Device 0166
    Flags: bus master, fast devsel, latency 0, IRQ 30
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at cfef0000 (64-bit, non-prefetchable) [size=64K]
    I/O ports at 9000 [size=256]
    [virtual] Expansion ROM at cfe00000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon

01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]
    Subsystem: Acer Incorporated [ALI] Device 0166
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at cfeec000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

---

### Post by khelben1979 on 2010-03-21
Try to mute/unmute the microphone.

---

### Post by extc on 2010-03-21
Tried that. Just a quick reaction when we unmute it. Still no response.

We think this could be a driver problem...

---

### Post by extc on 2010-03-21
I am going to install every sound configuration application in the Ubuntu software center and see what happens when I try to change something. I have tried all the devices and muting/unmuting, rebooting every time. No Joy.

Extc

---

### Post by extc on 2010-03-21
I have installed gnome alsa mixer and we managed to tinker with the settings and get strong microphone input from an external mic. However much we tinker, it only comes out of the speaker! Can record only a little.

Thanks/

---

