---
title: "unable to access floppy drive in ubuntu 11.04"
date: 2011-07-18
forum: Hardware
---

### Post by pythonscript on 2011-07-18
I have an old pieced-together desktop running 11.04 x86. The system has a floppy drive, which is hooked up and shows up in Nautilus. However, when I insert a disk and click open on the side panel in Nautilus, nothing happens. Is the hardware somehow not being recognised? This is the output of lspci -v, if that helps. 

Thank you!

```

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 735 Host (rev 01)
    Flags: bus master, medium devsel, latency 32
    Memory at d0000000 (32-bit, non-prefetchable) [size=64M]
    Capabilities: [c0] AGP version 2.0
    Kernel driver in use: agpgart-sis
    Kernel modules: sis-agp

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    I/O behind bridge: 00008000-00008fff
    Memory behind bridge: cfd00000-cfdfffff
    Prefetchable memory behind bridge: afb00000-cfbfffff
    Kernel modules: shpchp

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
    Flags: bus master, medium devsel, latency 0
    Kernel modules: i2c-sis630

00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
    Flags: medium devsel
    I/O ports at 0c00 [size=32]
    Kernel modules: i2c-sis96x

00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07) (prog-if 10 [OHCI])
    Subsystem: Silicon Integrated Systems [SiS] USB 1.1 Controller
    Flags: bus master, medium devsel, latency 64, IRQ 12
    Memory at cfffd000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07) (prog-if 10 [OHCI])
    Subsystem: Silicon Integrated Systems [SiS] USB 1.1 Controller
    Flags: bus master, medium devsel, latency 64, IRQ 5
    Memory at cfffe000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0) (prog-if 80 [Master])
    Subsystem: Silicon Integrated Systems [SiS] SiS5513 EIDE Controller (A,B step)
    Flags: bus master, fast devsel, latency 128
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
    I/O ports at ff00 [size=16]
    Kernel driver in use: pata_sis

00:03.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
    Subsystem: Silicon Integrated Systems [SiS] SiS900 10/100 Ethernet Adapter onboard [Asus P4SC-EA]
    Flags: bus master, medium devsel, latency 64, IRQ 10
    I/O ports at d400 [size=256]
    Memory at cfffc000 (32-bit, non-prefetchable) [size=4K]
    Expansion ROM at cffa0000 [disabled] [size=128K]
    Capabilities: [40] Power Management version 2
    Kernel driver in use: sis900
    Kernel modules: sis900

00:0b.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
    Subsystem: Creative Labs SB0090 Audigy Player/OEM
    Flags: bus master, medium devsel, latency 64, IRQ 11
    I/O ports at d000 [size=32]
    Capabilities: [dc] Power Management version 2
    Kernel driver in use: EMU10K1_Audigy
    Kernel modules: snd-emu10k1

00:0b.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (prog-if 10 [OHCI])
    Subsystem: Creative Labs SB Audigy FireWire Port
    Flags: bus master, medium devsel, latency 64, IRQ 10
    Memory at cfffb800 (32-bit, non-prefetchable) [size=2K]
    Memory at cfff4000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci

00:0d.0 Mass storage controller: Promise Technology, Inc. PDC40775 (SATA 300 TX2plus) (rev 02)
    Subsystem: Promise Technology, Inc. PDC40775 (SATA 300 TX2plus)
    Flags: bus master, 66MHz, medium devsel, latency 72, IRQ 10
    I/O ports at dc00 [size=128]
    I/O ports at d800 [size=256]
    Memory at cffff000 (32-bit, non-prefetchable) [size=4K]
    Memory at cffc0000 (32-bit, non-prefetchable) [size=128K]
    Expansion ROM at cffe0000 [disabled] [size=32K]
    Capabilities: [60] Power Management version 2
    Kernel driver in use: sata_promise
    Kernel modules: sata_promise

00:0f.0 Ethernet controller: Intel Corporation 82541PI Gigabit Ethernet Controller (rev 05)
    Subsystem: Intel Corporation PRO/1000 GT Desktop Adapter
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 12
    Memory at cff80000 (32-bit, non-prefetchable) [size=128K]
    Memory at cff60000 (32-bit, non-prefetchable) [size=128K]
    I/O ports at cc00 [size=64]
    Expansion ROM at cff40000 [disabled] [size=128K]
    Capabilities: [dc] Power Management version 2
    Capabilities: [e4] PCI-X non-bridge device
    Kernel driver in use: e1000
    Kernel modules: e1000

00:11.0 Serial controller: 3Com Corp, Modem Division 56K FaxModem Model 5610 (rev 01) (prog-if 02 [16550])
    Subsystem: 3Com Corp, Modem Division USR 56K Internal V92 FAX Modem (Model 5610)
    Flags: medium devsel, IRQ 11
    I/O ports at c800 [size=8]
    Capabilities: [dc] Power Management version 2
    Kernel driver in use: serial

00:13.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50) (prog-if 00 [UHCI])
    Subsystem: First International Computer, Inc. VA-502 Mainboard
    Flags: bus master, medium devsel, latency 64, IRQ 11
    I/O ports at c000 [size=32]
    Capabilities: [80] Power Management version 2
    Kernel driver in use: uhci_hcd

00:13.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50) (prog-if 00 [UHCI])
    Subsystem: First International Computer, Inc. VA-502 Mainboard
    Flags: bus master, medium devsel, latency 64, IRQ 11
    I/O ports at c400 [size=32]
    Capabilities: [80] Power Management version 2
    Kernel driver in use: uhci_hcd

00:13.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51) (prog-if 20 [EHCI])
    Subsystem: First International Computer, Inc. Device 1234
    Flags: bus master, medium devsel, latency 64, IRQ 10
    Memory at cfffb700 (32-bit, non-prefetchable) [size=256]
    Capabilities: [80] Power Management version 2
    Kernel driver in use: ehci_hcd

01:00.0 VGA compatible controller: ATI Technologies Inc RV515 PRO [Radeon X1300/X1550 Series] (prog-if 00 [VGA controller])
    Subsystem: ATI Technologies Inc Device 030b
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    Memory at cfdf0000 (64-bit, non-prefetchable) [size=64K]
    I/O ports at 8800 [size=256]
    Expansion ROM at cfdc0000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] AGP version 2.0
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit+
    Kernel driver in use: radeon
    Kernel modules: radeon

01:00.1 Display controller: ATI Technologies Inc RV515 PRO [Radeon X1300/X1550 Series] (Secondary)
    Subsystem: ATI Technologies Inc Device 030a
    Flags: bus master, 66MHz, medium devsel, latency 64
    Memory at cfde0000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [50] Power Management version 2


```

---

### Post by Joris Donders on 2011-07-18
Would'nt it be better to simply 'downgrade' your system to the LTS Lucid version ? 
I think the new kernel doesn't support that old hardware anymore. 

The kernel of Lucid does support floppy-drives; I've tested that on an old Aspire 1300 laptop.

---

### Post by jerrrys on 2011-07-19
maybe this

[http://ubuntuforums.org/showthread.php?t=1772291](http://ubuntuforums.org/showthread.php?t=1772291)

---

### Post by pythonscript on 2011-07-19
I found the udisk command a few hours after I posted my thread, and it worked perfectly. Thanks for the help!

So it's in this thread too:

```

udisks --mount /dev/fd0

```

Thank you again!

---

### Post by stallinux on 2011-09-13
> **pythonscript said:**
> I found the udisk command a few hours after I posted my thread, and it worked perfectly. Thanks for the help!

So it's in this thread too:

```

udisks --mount /dev/fd0

```Thank you again!

stallinux@mycomputer:~$ udisks --mount /dev/fd0
Mount failed: Error mounting: mount exited with exit code 1: helper failed with:
mount: I could not determine the filesystem type, and none was specified

My question: Who removed the floppy functionality in the later versions of Ubuntu? (And why was he not shot?!). It was working perfectly before. Now, in all the upgraded machines, it fails. I have no access to floppies anymore!! And I have to ask others on W****s computers to help me (much to their enjoyment).

This thread should be unmarked 'solved', because it remains a problem.
'floppy' and 'floppy0'  are visible in /media, but unaccessible. Sometimes it works with manually sudo mounting. Often not.

---

### Post by coffeecat on 2011-09-13
This thread is marked solved because it is solved for the OP.

@stallinux, since the udisks command seems to work for most people, I suggest you start your own support thread. This is more likely to be productive of help for you.

Thread closed.

---

