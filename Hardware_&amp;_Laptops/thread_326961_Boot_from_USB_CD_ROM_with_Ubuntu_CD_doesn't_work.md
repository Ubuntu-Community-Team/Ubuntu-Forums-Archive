---
title: "Boot from USB CD ROM with Ubuntu CD doesn't work"
date: 2006-12-28
forum: Hardware &amp; Laptops
---

### Post by markusheinzer on 2006-12-28
Hello
I try to boot my Windows XP laptop with the Ubuntu 6.10 Boot/Installation CD. My laptop only has a USB-CD-ROM-Drive. When I boot from the CD I can see the Ubuntu Logo Picture and then I can choose out of several options ("start and install...."). But whichever I choose, after some Messages ("Starting Linux Kernel" etc.) I get a black screen and the following error messages:

```
BusyBox v1.1.3 (Debian 1:1.1.3 -2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs) [17179602.976000] usb 4-2: device not accepting address 3, error -110
[17179613.512000] usb 4-2: device not accepting address 4, error -110
[17179624.048000] usb 4-2: device not accepting address 5, error -110

```

And after all it stops doing anything.

Does anybody have an idea how to work around this?

Thank you
Markus

---

### Post by teaker1s on 2006-12-29
try alternate iso not live desktop install

---

### Post by markusheinzer on 2006-12-30
Thank you for answering. I tried this right now. I get other error messages. 
any other possibility?

M.

---

### Post by logos34 on 2006-12-30
> I get other error messages.

What messages?  Be specific.  Please post the output.

---

### Post by markusheinzer on 2007-01-01
I'm sorry. I was already somehow giving it up.

My error messages are the following:

```
PCI: Cannot allocate resource region 0 device 0000:00:06.0
PCI: Cannot allocate resource region 1 device 0000:00:06.0
PCI: Cannot allocate resource region 2 device 0000:00:06.0
ACPI: Unable to set IRQ for PCI Interrupt Link [ALKD]. Try pci=noacpi or acpi=off.
ACPI: Unable to set IRQ for PCI Interrupt Link [ALKD]. Try pci=noacpi or acpi=off.
ACPI: Unable to set IRQ for PCI Interrupt Link [ALKD]. Try pci=noacpi or acpi=off.
ACPI: Unable to set IRQ for PCI Interrupt Link [ALKD]. Try pci=noacpi or acpi=off.
Starting system log daemon: syslogd, klogd.
```

And then while writing down this on a paper after some moments the process continues anyway. I can choose a language and a keyboard then. This works nice. 

But then while "Detecting hardware to find CD-ROM Drive" it doesn't find a drive (but it is actually running from the USB CD-ROM drive!!): "No common CD-ROM drive was detected." I was not able to choose the type (Matshita DVD-RAM UJ-845S USB) out of the cryptic choice alternatives. And I don't have neither a floppy drive nor a floppy-disc including the driver. 

And then I have an other question: First I tried with the "live desktop install" CD-iso because I just wanted to see Ubuntu before I decide to install it. But on the "alternate" CD-iso I can only choose out of different "installation" types. Is it possible to just have a look at Ubuntu with this "alternate" CD as well?

Thank you very much.

Markus

---

### Post by logos34 on 2007-01-01
> Is it possible to just have a look at Ubuntu with this "alternate" CD as well?

No, the alternate cd is a text-based installer.  

Those error messages are trying to tell you what the problem is: there's an IRQ/interrupt issue with acpi (Advanced Configuration & Power Interface) on your pci bus.  Try this: reboot and when the splash screen appears hit F6 to show 'boot options'.  To the end of that line add "noacpi".  If that doesn't work try "pci=noacpi" or "acpi=off".  Alternativly, try "noapic nolapic".  (More on options [here]("https://help.ubuntu.com/community/BootOptions").)

If none of that works and/or you run into another snag with hardware detection of your usb cd-rom, you could try copying the contents of the alternative installation CD to a [usb flash drive]("https://help.ubuntu.com/community/Installation/FromUSBStick") and see if you have any success with that method.  Or consider picking up cheap internal (or usb) floppy drive and go the [installation-with-floppy]("https://help.ubuntu.com/community/Installation/WithFloppies") route. 

Post back if you have any more problems.

---

### Post by markusheinzer on 2007-01-02
wow. it worked with "pci=noacpi". Everything fine but when the system starts I can see very shortly (on a black screen) the three first lines of my last post ("PCI: Cannot allocate..."). Maybe this is not a problem?
greetings and thank you very much.
Markus

---

### Post by logos34 on 2007-01-02
what about the usb cdrom?  Does it detect it ok now, no error messages?

---

### Post by logos34 on 2007-01-02
enter these commands in a terminal and post the output.  

> sudo lspci -v

> dmesg

When you disabled acpi it caused come other problem (hopefully with some function you can do without)

---

### Post by markusheinzer on 2007-01-02
yes, it has detected the cd-rom perfectly.

the output for the first command is this:

```
00:00.0 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
        Subsystem: Mitac Unknown device 8965
        Flags: bus master, 66MHz, medium devsel, latency 8
        Memory at a0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: [80] AGP version 3.5
        Capabilities: [50] Power Management version 2

00:00.1 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.2 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.3 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.4 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.7 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000c000-0000dfff
        Memory behind bridge: c0000000-cfffffff
        Prefetchable memory behind bridge: 90000000-9fffffff
        Capabilities: [70] Power Management version 2

00:06.0 Ethernet controller: Winbond Electronics Corp Unknown device 0033
        Subsystem: Winbond Electronics Corp Unknown device 0033
        Flags: medium devsel
        I/O ports at 1800 [disabled] [size=256]
        I/O ports at 1080 [disabled] [size=128]
        Memory at 20000000 (32-bit, non-prefetchable) [disabled] [size=512]
        Capabilities: [dc] Power Management version 2

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
        Subsystem: Mitac Unknown device 8965
        Flags: bus master, medium devsel, latency 22, IRQ 11
        I/O ports at 1200 [size=32]
        Capabilities: [80] Power Management version 2

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
        Subsystem: Mitac Unknown device 8965
        Flags: bus master, medium devsel, latency 22, IRQ 7
        I/O ports at 1220 [size=32]
        Capabilities: [80] Power Management version 2

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
        Subsystem: Mitac Unknown device 8965
        Flags: bus master, medium devsel, latency 22, IRQ 5
        I/O ports at 1240 [size=32]
        Capabilities: [80] Power Management version 2

00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82) (prog-if 20 [EHCI])
        Subsystem: Mitac Unknown device 8965
        Flags: bus master, medium devsel, latency 22, IRQ 10
        Memory at 20000200 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
        Subsystem: Mitac Unknown device 8965
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: [c0] Power Management version 2

00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: Mitac Unknown device 8965
        Flags: bus master, stepping, medium devsel, latency 64
        I/O ports at 1100 [size=16]
        Capabilities: [c0] Power Management version 2

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
        Subsystem: Mitac Unknown device 8965
        Flags: medium devsel, IRQ 5
        I/O ports at e000 [size=256]
        Capabilities: [c0] Power Management version 2

00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
        Subsystem: Mitac Unknown device 8965
        Flags: medium devsel, IRQ 5
        I/O ports at e100 [size=256]
        Capabilities: [d0] Power Management version 2

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
        Subsystem: Mitac Unknown device 8965
        Flags: bus master, stepping, medium devsel, latency 128, IRQ 11
        I/O ports at e200 [size=256]
        Memory at d0000000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [40] Power Management version 2

01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 02) (prog-if 00 [VGA])
        Subsystem: Mitac Unknown device 8965
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
        Memory at 90000000 (32-bit, prefetchable) [size=64M]
        Memory at c0000000 (32-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at 94000000 [disabled] [size=64K]
        Capabilities: [60] Power Management version 2
        Capabilities: [70] AGP version 2.0
```

the output of the second is this:
```
[17179569.184000] Linux version 2.6.17-10-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 22:28:26 UTC 2006 (Ubuntu 2.6.17-10.34-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001dfef000 (usable)
[17179569.184000]  BIOS-e820: 000000001dff0000 - 000000001dffffc0 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001dffffc0 - 000000001e000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 479MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 122863
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 118767 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 OID_00                                ) @ 0x000e6010
[17179569.184000] ACPI: RSDT (v001 INSYDE FACP_000 0x00000100 0000 0x00010200) @ 0x1dffc2a0
[17179569.184000] ACPI: FADT (v001 INSYDE FACP_000 0x00000100 0000 0x00010200) @ 0x1dfffb00
[17179569.184000] ACPI: MADT (v001 INSYDE APIC_000 0x30303030 0000 0x00010200) @ 0x1dfffb90
[17179569.184000] ACPI: DSDT (v001 INSYDE    PN800 0x00001000 INTL 0x02002036) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:9 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 1e000000:e1f80000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash pci=noacpi
[17179569.184000] Found and enabled local APIC!
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 1293.920 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179573.372000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179573.372000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179573.392000] Memory: 477544k/491452k available (1910k kernel code, 13344k reserved, 1069k data, 308k init, 0k highmem)
[17179573.392000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179573.472000] Calibrating delay using timer specific routine.. 2590.97 BogoMIPS (lpj=5181953)
[17179573.472000] Security Framework v1.0.0 initialized
[17179573.472000] SELinux:  Disabled at boot.
[17179573.472000] Mount-cache hash table entries: 512
[17179573.472000] CPU: After generic identify, caps: a7e9fbbf 00000000 00000000 00000000 00000000 00000000 00000000
[17179573.472000] CPU: After vendor identify, caps: a7e9fbbf 00000000 00000000 00000000 00000000 00000000 00000000
[17179573.472000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179573.472000] CPU: L2 cache: 512K
[17179573.472000] CPU: After all inits, caps: a7e9fbbf 00000000 00000000 00000040 00000000 00000000 00000000
[17179573.472000] Checking 'hlt' instruction... OK.
[17179573.488000] SMP alternatives: switching to UP code
[17179573.488000] Freeing SMP alternatives: 16k freed
[17179573.488000] checking if image is initramfs... it is
[17179574.188000] Freeing initrd memory: 5321k freed
[17179574.188000] ACPI: Core revision 20060707
[17179574.188000] ACPI: Looking for DSDT ... not found!
[17179574.192000] ACPI: setting ELCR to 0ea0 (from 0ca0)
[17179574.200000] CPU0: Intel(R) Celeron(R) M processor         1300MHz stepping 05
[17179574.200000] Total of 1 processors activated (2590.97 BogoMIPS).
[17179574.304000] Brought up 1 CPUs
[17179574.304000] migration_cost=0
[17179574.304000] NET: Registered protocol family 16
[17179574.304000] EISA bus registered
[17179574.304000] ACPI: bus type pci registered
[17179574.304000] PCI: PCI BIOS revision 2.10 entry at 0xe9bf4, last bus=1
[17179574.304000] PCI: Using configuration type 1
[17179574.304000] Setting up standard PCI resources
[17179574.308000] ACPI: Interpreter enabled
[17179574.308000] ACPI: Using PIC for interrupt routing
[17179574.312000] ACPI: Embedded Controller [EC0] (gpe 1) interrupt mode.
[17179574.312000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179574.312000] pnp: PnP ACPI init
[17179574.316000] pnp: PnP ACPI: found 9 devices
[17179574.316000] PnPBIOS: Disabled by ACPI PNP
[17179574.316000] PCI: Probing PCI hardware
[17179574.316000] PCI: Probing PCI hardware (bus 00)
[17179574.320000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179574.324000] PCI quirk: region 1000-107f claimed by vt8235 PM
[17179574.324000] PCI quirk: region 1400-140f claimed by vt8235 SMB
[17179574.324000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:11.1
[17179574.324000] Boot video device is 0000:01:00.0
[17179574.340000] PCI: Using IRQ router VIA [1106/3177] at 0000:00:11.0
[17179574.340000] PCI: Cannot allocate resource region 0 of device 0000:00:06.0
[17179574.340000] PCI: Cannot allocate resource region 1 of device 0000:00:06.0
[17179574.340000] PCI: Cannot allocate resource region 2 of device 0000:00:06.0
[17179574.344000] pnp: 00:07: ioport range 0x330-0x331 has been reserved
[17179574.344000] pnp: 00:07: ioport range 0x4d0-0x4d1 has been reserved
[17179574.344000] pnp: 00:07: ioport range 0x1000-0x107f could not be reserved
[17179574.344000] pnp: 00:07: ioport range 0x1400-0x140f has been reserved
[17179574.344000] PCI: Bridge: 0000:00:01.0
[17179574.344000]   IO window: c000-dfff
[17179574.344000]   MEM window: c0000000-cfffffff
[17179574.344000]   PREFETCH window: 90000000-9fffffff
[17179574.344000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179574.344000] NET: Registered protocol family 2
[17179574.384000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179574.384000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179574.384000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179574.384000] TCP: Hash tables configured (established 16384 bind 8192)
[17179574.384000] TCP reno registered
[17179574.384000] audit: initializing netlink socket (disabled)
[17179574.384000] audit(1167744353.384:1): initialized
[17179574.384000] VFS: Disk quotas dquot_6.5.1
[17179574.384000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179574.384000] Initializing Cryptographic API
[17179574.384000] io scheduler noop registered
[17179574.384000] io scheduler anticipatory registered
[17179574.384000] io scheduler deadline registered
[17179574.384000] io scheduler cfq registered (default)
[17179574.384000] isapnp: Scanning for PnP cards...
[17179574.740000] isapnp: No Plug & Play device found
[17179574.796000] Real Time Clock Driver v1.12ac
[17179574.796000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179574.796000] mice: PS/2 mouse device common for all mice
[17179574.796000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179574.796000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179574.796000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179574.796000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179574.812000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179574.816000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179574.816000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179574.816000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179574.820000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179574.820000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.820000] EISA: Probing bus 0 at eisa.0
[17179574.820000] Cannot allocate resource for EISA slot 1
[17179574.820000] EISA: Detected 0 cards.
[17179574.824000] TCP bic registered
[17179574.824000] NET: Registered protocol family 1
[17179574.824000] NET: Registered protocol family 8
[17179574.824000] NET: Registered protocol family 20
[17179574.824000] Using IPI No-Shortcut mode
[17179574.824000] ACPI: (supports S0 S1 S3 S4 S5)
[17179574.824000] Freeing unused kernel memory: 308k freed
[17179574.852000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179575.948000] Capability LSM initialized
[17179575.992000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179575.992000] ACPI: Processor [CPU0] (supports 16 throttling states)
[17179576.000000] ACPI: Thermal Zone [TZ0] (0 C)
[17179576.496000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[17179576.496000] VP_IDE: chipset revision 6
[17179576.496000] VP_IDE: not 100% native mode: will probe irqs later
[17179576.496000] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[17179576.496000]     ide0: BM-DMA at 0x1100-0x1107, BIOS settings: hda:DMA, hdb:pio
[17179576.496000]     ide1: BM-DMA at 0x1108-0x110f, BIOS settings: hdc:pio, hdd:pio
[17179576.496000] Probing IDE interface ide0...
[17179576.912000] hda: SAMSUNG MP0402H, ATA DISK drive
[17179577.808000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179578.248000] Probing IDE interface ide1...
[17179578.824000] hda: max request size: 512KiB
[17179578.824000] hda: 78242976 sectors (40060 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[17179578.824000] hda: cache flushes supported
[17179578.824000]  hda: hda1 hda2 < hda5 >
[17179579.064000] Probing IDE interface ide1...
[17179579.140000] usbcore: registered new driver usbfs
[17179579.140000] usbcore: registered new driver hub
[17179579.148000] USB Universal Host Controller Interface driver v3.0
[17179579.148000] PCI: Found IRQ 11 for device 0000:00:10.0
[17179579.148000] PCI: Sharing IRQ 11 with 0000:00:12.0
[17179579.148000] PCI: Sharing IRQ 11 with 0000:01:00.0
[17179579.148000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[17179579.148000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[17179579.148000] uhci_hcd 0000:00:10.0: irq 11, io base 0x00001200
[17179579.148000] usb usb1: configuration #1 chosen from 1 choice
[17179579.152000] hub 1-0:1.0: USB hub found
[17179579.152000] hub 1-0:1.0: 2 ports detected
[17179579.256000] PCI: Found IRQ 7 for device 0000:00:10.1
[17179579.256000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[17179579.256000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[17179579.256000] uhci_hcd 0000:00:10.1: irq 7, io base 0x00001220
[17179579.256000] usb usb2: configuration #1 chosen from 1 choice
[17179579.256000] hub 2-0:1.0: USB hub found
[17179579.256000] hub 2-0:1.0: 2 ports detected
[17179579.360000] PCI: Found IRQ 5 for device 0000:00:10.2
[17179579.360000] PCI: Sharing IRQ 5 with 0000:00:11.5
[17179579.360000] PCI: Sharing IRQ 5 with 0000:00:11.6
[17179579.360000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[17179579.360000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[17179579.360000] uhci_hcd 0000:00:10.2: irq 5, io base 0x00001240
[17179579.360000] usb usb3: configuration #1 chosen from 1 choice
[17179579.360000] hub 3-0:1.0: USB hub found
[17179579.360000] hub 3-0:1.0: 2 ports detected
[17179579.464000] PCI: Enabling device 0000:00:10.3 (0000 -> 0002)
[17179579.464000] PCI: Found IRQ 10 for device 0000:00:10.3
[17179579.464000] ehci_hcd 0000:00:10.3: EHCI Host Controller
[17179579.464000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[17179579.464000] ehci_hcd 0000:00:10.3: irq 10, io mem 0x20000200
[17179579.464000] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179579.464000] usb usb4: configuration #1 chosen from 1 choice
[17179579.464000] hub 4-0:1.0: USB hub found
[17179579.464000] hub 4-0:1.0: 6 ports detected
[17179579.704000] Attempting manual resume
[17179579.732000] kjournald starting.  Commit interval 5 seconds
[17179579.732000] EXT3-fs: mounted filesystem with ordered data mode.
[17179580.544000] usb 1-2: new low speed USB device using uhci_hcd and address 2
[17179580.720000] usb 1-2: configuration #1 chosen from 1 choice
[17179590.780000] Linux agpgart interface v0.101 (c) Dave Jones
[17179590.868000] agpgart: Detected VIA PM800/PN800/PM880/PN880 chipset
[17179590.876000] agpgart: AGP aperture is 128M @ 0xa0000000
[17179591.152000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179591.216000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179591.524000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[17179591.524000] PCI: Found IRQ 11 for device 0000:00:12.0
[17179591.524000] PCI: Sharing IRQ 11 with 0000:00:10.0
[17179591.524000] PCI: Sharing IRQ 11 with 0000:01:00.0
[17179591.528000] eth0: VIA Rhine II at 0x1e200, 00:40:d0:72:53:b5, IRQ 11.
[17179591.528000] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 40a1.
[17179591.700000] input: PC Speaker as /class/input/input1
[17179591.900000] PCI: Found IRQ 5 for device 0000:00:11.6
[17179591.900000] PCI: Sharing IRQ 5 with 0000:00:10.2
[17179591.900000] PCI: Sharing IRQ 5 with 0000:00:11.5
[17179591.904000] PCI: Setting latency timer of device 0000:00:11.6 to 64
[17179592.216000] irda_init()
[17179592.216000] NET: Registered protocol family 23
[17179592.296000] usbcore: registered new driver hiddev
[17179592.320000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
[17179592.320000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:10.0-2
[17179592.320000] usbcore: registered new driver usbhid
[17179592.320000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179592.412000] PCI: Found IRQ 5 for device 0000:00:11.5
[17179592.412000] PCI: Sharing IRQ 5 with 0000:00:10.2
[17179592.412000] PCI: Sharing IRQ 5 with 0000:00:11.6
[17179592.412000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[17179592.604000] ts: Compaq touchscreen protocol output
[17179592.660000] eth0: link up, 100Mbps, half-duplex, lpa 0x40A1
[17179592.680000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0xa56eb1, caps: 0x804713/0x0
[17179592.732000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[17179593.472000] lp: driver loaded but no devices found
[17179593.508000] Adding 1413680k swap on /dev/disk/by-uuid/24039f0e-b315-4733-bdfe-e614de241f0d.  Priority:-1 extents:1 across:1413680k
[17179593.580000] EXT3 FS on hda1, internal journal
[17179593.708000] NET: Registered protocol family 17
[17179594.884000] ACPI: AC Adapter [AC] (on-line)
[17179594.960000] ACPI: Battery Slot [BAT0] (battery present)
[17179594.980000] ACPI: Power Button (FF) [PWRF]
[17179594.980000] ACPI: Lid Switch [LID]
[17179594.980000] ACPI: Sleep Button (CM) [SBTN]
[17179594.980000] ACPI: Power Button (CM) [PBTN]
[17179595.120000] ibm_acpi: ec object not found
[17179595.160000] pcc_acpi: loading...
[17179595.288000] ACPI: Video Device [VGA0] (multi-head: yes  rom: no  post: no)
[17179600.400000] [drm] Initialized drm 1.0.1 20051102
[17179600.972000] PCI: Found IRQ 11 for device 0000:01:00.0
[17179600.972000] PCI: Sharing IRQ 11 with 0000:00:10.0
[17179600.972000] PCI: Sharing IRQ 11 with 0000:00:12.0
[17179600.972000] [drm] Initialized via 2.7.4 20051116 on minor 0
[17179601.004000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17179601.004000] agpgart: Device is in legacy mode, falling back to 2.x
[17179601.004000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 0x mode
[17179601.004000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 0x mode
[17179601.464000] apm: BIOS not found.
[17179605.740000] Bluetooth: Core ver 2.8
[17179605.740000] NET: Registered protocol family 31
[17179605.740000] Bluetooth: HCI device and connection manager initialized
[17179605.740000] Bluetooth: HCI socket layer initialized
[17179605.760000] Bluetooth: L2CAP ver 2.8
[17179605.760000] Bluetooth: L2CAP socket layer initialized
[17179605.804000] Bluetooth: RFCOMM socket layer initialized
[17179605.804000] Bluetooth: RFCOMM TTY layer initialized
[17179605.804000] Bluetooth: RFCOMM ver 1.7
[17179609.224000] NET: Registered protocol family 10
[17179609.224000] lo: Disabled Privacy Extensions
[17179609.224000] IPv6 over IPv4 tunneling driver
[17179620.176000] eth0: no IPv6 routers present
[17181811.424000] Linux video capture interface: v1.00
```

thank you

---

### Post by logos34 on 2007-01-02
are you getting internet connection?  sound? everything seems like it works ok?

If you remember the error message you got the last time or when you reboot write it down so we can match it up to the column on the left of the lspci -v output (the first time -- 00.06.0 was the ethernet comtroller)

---

### Post by logos34 on 2007-01-02
[cancel]

---

### Post by markusheinzer on 2007-01-05
sorry for not answering sooner.

Yes. everything works very well. I like this ubuntu already very much. internet connection OK, sound OK, everything seems like it works OK.

I will post the Error message when I see it next time.

thanks for your help anyway.

---

### Post by Yoeri on 2007-01-05
I noticed I am not able to boot the Live-CD nor my installed Ubuntu when a memory stick is present in my USB-port...

---

### Post by logos34 on 2007-01-05
> Yes. everything works very well. I like this ubuntu already very much. internet connection OK, sound OK, everything seems like it works OK.

I will post the Error message when I see it next time.

thanks for your help anyway.

Ok, in the meantime, Enjoy!

.........

> I noticed I am not able to boot the Live-CD nor my installed Ubuntu when a memory stick is present in my USB-port...
Yoeri,
you might want to start a new thread.

---

### Post by markusheinzer on 2007-01-10
Me again.
I think that the mentioned Error-Warnings are the same as before (only the first three):

```
PCI: Cannot allocate resource region 0 device 0000:00:06.0
PCI: Cannot allocate resource region 1 device 0000:00:06.0
PCI: Cannot allocate resource region 2 device 0000:00:06.0
```

I'm not perfectly sure since this screen shows up only for a very short time (maybe a second or less).

But I have still not met any problems (concerning PCI or others).
Thank you.

---

### Post by ylg91 on 2007-10-08
**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+question/13986](https://answers.launchpad.net/ubuntu/+question/13986) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **markusheinzer said:**
> Me again.
I think that the mentioned Error-Warnings are the same as before (only the first three):

```
PCI: Cannot allocate resource region 0 device 0000:00:06.0
PCI: Cannot allocate resource region 1 device 0000:00:06.0
PCI: Cannot allocate resource region 2 device 0000:00:06.0
```



Hi ! I have the same laptop , i think the device 0000:00:06.0 is the mini PCI wifi card ... that do not work !
see my post : [http://ubuntuforums.org/showthread.php?t=559876&highlight=ipw2200%3A+Error+allocating+IRQ](http://ubuntuforums.org/showthread.php?t=559876&highlight=ipw2200%3A+Error+allocating+IRQ)

i have tried 3 wifi cards , always had the same IRQ error.
i have also look in the DSDT : there is no error/warning.

is there anyy chance  ?

---

### Post by markusheinzer on 2007-10-08
OK. now I know why I don't get my Wireless working...
I still boot with the noacpi-option.

---

### Post by ylg91 on 2007-10-08
My bios is M1.13 and you ?
I have test to boot without options ,  USB do not work and the screen freeze sometimes !

may be this lines are important ???

> [    7.143759] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0, disabled.
[    7.143883] ACPI: PCI Interrupt Link [ALKB] (IRQs 23) *11
[    7.144015] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *5, disabled.
[    7.144086] ACPI Error (uteval-0293): Return object type is incorrect [\_SB_.PCI0.ALKD._CRS] (Node dcaae678), AE_TYPE
[    7.144094] ACPI Error (uteval-0299): Type returned from _CRS was incorrect: Integer, expected Btypes: 4 [20070126]
[    7.144099] ACPI Exception (pci_link-0277): AE_TYPE, Evaluating _CRS [20070126]
[    7.144103] ACPI: PCI Interrupt Link [ALKD] (IRQs 21) *0
...
[   19.124000] ACPI: PCI Interrupt 0000:00:06.0[A]: no GSI


---

### Post by ylg91 on 2007-10-08
Can you download my custom DSDT : [http://acpi.sourceforge.net/dsdt/view.php?id=934](http://acpi.sourceforge.net/dsdt/view.php?id=934)

It worked for me .

Apply with 

sudo cp dsdt.aml /etc/initramfs-tools/DSDT.aml
sudo dpkg-reconfigure linux-image-$(uname -r)

---

