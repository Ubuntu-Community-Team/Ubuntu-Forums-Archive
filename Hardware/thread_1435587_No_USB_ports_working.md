---
title: "No USB ports working"
date: 2010-03-21
forum: Hardware
---

### Post by theone964 on 2010-03-21
I have Ubuntu 9.10 and a compaq presario sr1630wm desktop. I installed Ubuntu to the HD while the HD was in another computer and everything worked fine, but then i unplugged the HD and put it in the Compaq and now USB ports wont work

I have read a couple threads and i think my issue is that i have an SB400 controller.

i ran some commands and they dont all make sense to me but here they are:

```
chirag@chirag-desktop:~$ lspci -v
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
    Subsystem: Hewlett-Packard Company Device 2a26
    Flags: bus master, 66MHz, medium devsel, latency 64
    Kernel modules: ati-agp

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
    Flags: bus master, 66MHz, medium devsel, latency 99
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fde00000-fdefffff
    Prefetchable memory behind bridge: 00000000d8000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Hewlett-Packard Company Device 2a26
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
    I/O ports at ff00 [size=8]
    I/O ports at fe00 [size=4]
    I/O ports at fd00 [size=8]
    I/O ports at fc00 [size=4]
    I/O ports at fb00 [size=16]
    Memory at fe02f000 (32-bit, non-prefetchable) [size=512]
    [virtual] Expansion ROM at 1c000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: sata_sil

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 2a26
    Flags: 66MHz, medium devsel
    Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 2a26
    Flags: 66MHz, medium devsel
    Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 2a26
    Flags: 66MHz, medium devsel
    Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
    Subsystem: Hewlett-Packard Company Device 2a26
    Flags: 66MHz, medium devsel
    I/O ports at 0b00 [size=16]
    Memory at fe02b000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (prog-if 8a [Master SecP PriP])
    Subsystem: Hewlett-Packard Company Device 2a26
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at f900 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_atiixp

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
    Subsystem: Hewlett-Packard Company Device 2a26
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (prog-if 01)
    Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fdd00000-fddfffff
    Prefetchable memory behind bridge: fdc00000-fdcfffff

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 2a27
    Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
    Memory at fe02a000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ATI IXP AC97 controller
    Kernel modules: snd-atiixp

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Flags: fast devsel
    Kernel driver in use: k8temp
    Kernel modules: k8temp

01:05.0 VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series]
    Subsystem: Hewlett-Packard Company Device 2a26
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at d8000000 (32-bit, prefetchable) [size=128M]
    I/O ports at ee00 [size=256]
    Memory at fdef0000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at fde00000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel modules: radeon

02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Hewlett-Packard Company Device 2a26
    Flags: bus master, medium devsel, latency 64, IRQ 17
    I/O ports at dc00 [size=256]
    Memory at fddff000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: 8139too
    Kernel modules: epl, 8139too, 8139cp

02:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80) (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 2a26
    Flags: bus master, stepping, medium devsel, latency 64, IRQ 17
    Memory at fddfe000 (32-bit, non-prefetchable) [size=2K]
    I/O ports at df00 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394
``````
chirag@chirag-desktop:~$ dmesg | grep usb
[    0.285826] usbcore: registered new interface driver usbfs
[    0.285838] usbcore: registered new interface driver hub
[    0.285861] usbcore: registered new device driver usb
```Thank You

I think I have to update my BIOS but I have no idea how to do that since the BIOS on HP/Compaq's website is for Windows
[http://ubuntuforums.org/showthread.php?t=1004166](http://ubuntuforums.org/showthread.php?t=1004166)

[SOLVED] I logged into my windows partition and updated the BIOS. Restarted and everything works fine now.

---

