---
title: "Suspend wont work for me."
date: 2007-07-17
forum: Hardware &amp; Laptops
---

### Post by StueyB on 2007-07-17
Hi Everyone,

I have a little problem with suspend/resume on my Vaio C2S. Basically, if I try and do a suspend, it drops out of X and gives me a whole lot of error messeges about waiting for resources to become freed (typically USB devices, although there are none connected)

It then appears to go into suspended mode. If I hit the power button to bring it back, it doesn't resume. It just loads the first part of the ubuntu splash screen. The only way back from this is to do a cold reboot.

Looking in the kern.log I found the following entry, every time this happens:
Jul 16 17:46:41 stuart-laptop kernel: [    5.788000] Attempting manual resume
Jul 16 17:46:41 stuart-laptop kernel: [    5.788000] swsusp: Resume From Partition 8:5
Jul 16 17:46:41 stuart-laptop kernel: [    5.788000] PM: Checking swsusp image.
Jul 16 17:46:41 stuart-laptop kernel: [    5.788000] PM: Resume from disk failed.
Jul 16 17:46:41 stuart-laptop kernel: [    5.804000] EXT3-fs: INFO: recovery required on readonly filesystem.
Jul 16 17:46:41 stuart-laptop kernel: [    5.804000] EXT3-fs: write access will be enabled during recovery.
Jul 16 17:46:41 stuart-laptop kernel: [    8.684000] kjournald starting.  Commit interval 5 seconds
Jul 16 17:46:41 stuart-laptop kernel: [    8.684000] EXT3-fs: sda2: orphan cleanup on readonly fs
Jul 16 17:46:41 stuart-laptop kernel: [    8.684000] ext3_orphan_cleanup: deleting unreferenced inode 4046941
Jul 16 17:46:41 stuart-laptop kernel: [    8.684000] ext3_orphan_cleanup: deleting unreferenced inode 4046940
Jul 16 17:46:41 stuart-laptop kernel: [    8.684000] ext3_orphan_cleanup: deleting unreferenced inode 4046939
Jul 16 17:46:41 stuart-laptop kernel: [    8.684000] ext3_orphan_cleanup: deleting unreferenced inode 4046938
Jul 16 17:46:41 stuart-laptop kernel: [    8.684000] ext3_orphan_cleanup: deleting unreferenced inode 4046923
Jul 16 17:46:41 stuart-laptop kernel: [    8.684000] ext3_orphan_cleanup: deleting unreferenced inode 4046922
Jul 16 17:46:41 stuart-laptop kernel: [    8.684000] ext3_orphan_cleanup: deleting unreferenced inode 4046920
Jul 16 17:46:41 stuart-laptop kernel: [    8.684000] ext3_orphan_cleanup: deleting unreferenced inode 4046919
Jul 16 17:46:41 stuart-laptop kernel: [    8.684000] ext3_orphan_cleanup: deleting unreferenced inode 4046918
Jul 16 17:46:41 stuart-laptop kernel: [    8.684000] ext3_orphan_cleanup: deleting unreferenced inode 4046917
Jul 16 17:46:41 stuart-laptop kernel: [    8.688000] ext3_orphan_cleanup: deleting unreferenced inode 4046916
Jul 16 17:46:41 stuart-laptop kernel: [    8.688000] ext3_orphan_cleanup: deleting unreferenced inode 4046914
Jul 16 17:46:41 stuart-laptop kernel: [    8.688000] ext3_orphan_cleanup: deleting unreferenced inode 4046913
Jul 16 17:46:41 stuart-laptop kernel: [    8.688000] ext3_orphan_cleanup: deleting unreferenced inode 4046912
Jul 16 17:46:41 stuart-laptop kernel: [    8.688000] ext3_orphan_cleanup: deleting unreferenced inode 4046911
Jul 16 17:46:41 stuart-laptop kernel: [    8.688000] ext3_orphan_cleanup: deleting unreferenced inode 4046910
Jul 16 17:46:41 stuart-laptop kernel: [    8.688000] EXT3-fs: sda2: 16 orphan inodes deleted
Jul 16 17:46:41 stuart-laptop kernel: [    8.688000] EXT3-fs: recovery complete.
Jul 16 17:46:41 stuart-laptop kernel: [    8.704000] EXT3-fs: mounted filesystem with ordered data mode.
Jul 16 17:46:41 stuart-laptop kernel: [   10.120000] usb-storage: device scan complete

This is running 7.04 standard, with all updates applied, and kernel version 2.6.20-16-generic

lspci -v output:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Sony Corporation Unknown device 820f
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
	Subsystem: Sony Corporation Unknown device 820f
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at d0100000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Memory at b0000000 (32-bit, prefetchable) [size=256M]
	Memory at d0200000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Sony Corporation Unknown device 820f
	Flags: bus master, fast devsel, latency 0
	Memory at d0180000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Sony Corporation Unknown device 820f
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d0240000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: c8000000-c9ffffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000c1ffffff
	Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: ca000000-cbffffff
	Prefetchable memory behind bridge: 00000000c2000000-00000000c3ffffff
	Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=07, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: cc000000-cdffffff
	Prefetchable memory behind bridge: 00000000c4000000-00000000c5ffffff
	Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=09, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: ce000000-cfffffff
	Prefetchable memory behind bridge: 00000000c6000000-00000000c7ffffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Sony Corporation Unknown device 820f
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Sony Corporation Unknown device 820f
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Sony Corporation Unknown device 820f
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1860 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Sony Corporation Unknown device 820f
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
	Subsystem: Sony Corporation Unknown device 820f
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at d0444000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0e, sec-latency=32
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: d0000000-d00fffff
	Prefetchable memory behind bridge: 0000000088000000-000000008bffffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
	Subsystem: Sony Corporation Unknown device 820f
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Sony Corporation Unknown device 820f
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Sony Corporation Unknown device 820f
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 21
	I/O ports at 18d0 [size=8]
	I/O ports at 18c4 [size=4]
	I/O ports at 18c8 [size=8]
	I/O ports at 18c0 [size=4]
	I/O ports at 18b0 [size=16]
	Memory at d0444400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
	Subsystem: Sony Corporation Unknown device 820f
	Flags: medium devsel, IRQ 10
	I/O ports at 18e0 [size=32]

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 16)
	Subsystem: Sony Corporation Unknown device 820f
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at c8000000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at 2000 [size=256]
	Capabilities: <access denied>

06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
	Subsystem: Intel Corporation Unknown device 1051
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at cc000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

0a:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
	Subsystem: Sony Corporation Unknown device 820f
	Flags: bus master, medium devsel, latency 168, IRQ 17
	Memory at d0006000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=0a, secondary=0b, subordinate=0e, sec-latency=176
	Memory window 0: 88000000-8bfff000 (prefetchable)
	Memory window 1: 8c000000-8ffff000
	I/O window 0: 00006000-000060ff
	I/O window 1: 00006400-000064ff
	16-bit legacy interface ports at 0001

0a:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
	Subsystem: Sony Corporation Unknown device 820f
	Flags: bus master, medium devsel, latency 64, IRQ 17
	Memory at d0005000 (32-bit, non-prefetchable) [size=2K]
	Memory at d0000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

0a:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
	Subsystem: Sony Corporation Unknown device 820f
	Flags: bus master, medium devsel, latency 64, IRQ 16
	Memory at d0004000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

---

### Post by wastedfluid on 2007-07-17
Hi.

Take a look at 

[link]http://ubuntuforums.org/showthread.php?t=471855[/link]

Should fix your problem.  Worked for me on an Acer 5110.. usually, it's one method, or the other - one will work.

Good luck!

---

### Post by IntuitiveNipple on 2007-07-17
From the look of your log snippet, it isn't strictly speaking using suspend/resume, it is using *swsusp* that is part of the Suspend2 package to do a suspend-to-disk, better known as hibernate.

The reason it fails appears to be that whilst the disk-image is being written to disk something goes wrong and the disk is corrupted before power-off. All those disk recovery messages show that.

Have you tried removing Suspend2 and using the real kernel **suspend-to-ram** or [n]hibernate[/b] that are controlled by the config file /etc/default/acpi-support and activated from /etc/acpi/sleep.sh via the log-off menu ?

---

### Post by StueyB on 2007-07-21
HI Guys,

Sorry for the delay but I will check it out now.

Thanks

Stuart

---

