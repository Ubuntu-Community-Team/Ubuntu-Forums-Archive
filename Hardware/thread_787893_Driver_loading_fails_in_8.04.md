---
title: "Driver loading fails in 8.04"
date: 2008-05-09
forum: Hardware
---

### Post by Scienceman123 on 2008-05-09
Upon startup, it says that when it is "Loading Hardware Drivers", it fails. When it gets to the login screen, my keyboard, USB mouse, and touchpad also fail to work. However, I can switch using ALT+CTRL+F1/F2/etc. and login there. I am running 8.04 upgraded from a working 6.06 via alternative CD mounted from an ISO on a Toshiba Satellite A105-S2051 with a 1.69GHz Celeron M processor, and 2 GB of RAM.

---

### Post by Scienceman123 on 2008-05-09
Bump.

---

### Post by prshah on 2008-05-09
> **Scienceman123 said:**
> Upon startup, it says that when it is "Loading Hardware Drivers", it fails. When it gets to the login screen, my keyboard, USB mouse, and touchpad also fail to work. 

Have you tried reconfiguring your keyboard/mouse/et al```
sudo dpkg-reconfigure xserver-xorg
```?

Info from the files "/var/log/messages" and "/var/log/Xorg.0.log" will give us clues to why these problems are occurring... can you post them here?

You can use lynx (a text only browser) if you are not able to log in.

---

### Post by Scienceman123 on 2008-06-16
Okay, finally got the files.

Contents of /var/log/messages:

```
Jun 11 03:28:03 brian-laptop syslogd 1.5.0#1ubuntu1: restart.
Jun 11 03:33:45 brian-laptop kernel: [17180641.896000]     ACPI-0307: *** Error: No installed handler for fixed event [00000000]
Jun 11 03:56:27 brian-laptop -- MARK --
Jun 11 04:00:27 brian-laptop UBUNTUZILLA: Retrieving the version of the latest release of Firefox from the Mozilla website...
Jun 11 04:00:27 brian-laptop UBUNTUZILLA: Traceback (most recent call last):
Jun 11 04:00:27 brian-laptop UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 1051, in <module>
Jun 11 04:00:27 brian-laptop UBUNTUZILLA:     bs.start()
Jun 11 04:00:27 brian-laptop UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 209, in start
Jun 11 04:00:27 brian-laptop UBUNTUZILLA:     fi.start()
Jun 11 04:00:27 brian-laptop UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 246, in start
Jun 11 04:00:27 brian-laptop UBUNTUZILLA:     self.checkforupdateGui()
Jun 11 04:00:27 brian-laptop UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 544, in checkforupdateGui
Jun 11 04:00:27 brian-laptop UBUNTUZILLA:     self.getLatestVersion()
Jun 11 04:00:27 brian-laptop UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 652, in getLatestVersion
Jun 11 04:00:27 brian-laptop UBUNTUZILLA:     self.releaseVersion = self.util.getSystemOutput(executionstring="wget -c --tries=20 --read-timeout=60 --waitretry=10 -q -O - http://www.mozilla.com |grep 'product=' -m 1 |sed -e 's/.*<li>.*firefox-//' -e 's/&amp.*//'", numlines=1, errormessage="Failed to retrieve the latest version of "+ self.options.package.capitalize())
Jun 11 04:00:27 brian-laptop UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 124, in getSystemOutput
Jun 11 04:00:27 brian-laptop UBUNTUZILLA:     return result[0]
Jun 11 04:00:27 brian-laptop UBUNTUZILLA: IndexError: list index out of range
Jun 11 04:16:27 brian-laptop -- MARK --
Jun 11 04:36:27 brian-laptop -- MARK --
Jun 11 04:56:27 brian-laptop -- MARK --
Jun 11 05:16:28 brian-laptop -- MARK --
Jun 11 05:36:28 brian-laptop -- MARK --
Jun 11 05:56:28 brian-laptop -- MARK --
Jun 11 06:16:28 brian-laptop -- MARK --
Jun 11 06:36:28 brian-laptop -- MARK --
Jun 11 06:56:29 brian-laptop -- MARK --
Jun 11 07:04:22 brian-laptop kernel: [17193278.276000]     ACPI-0307: *** Error: No installed handler for fixed event [00000000]
Jun 16 11:11:36 brian-laptop syslogd 1.5.0#1ubuntu1: restart.
Jun 16 11:11:36 brian-laptop kernel: Inspecting /boot/System.map-2.6.15-51-386
Jun 16 11:11:36 brian-laptop kernel: Loaded 23076 symbols from /boot/System.map-2.6.15-51-386.
Jun 16 11:11:36 brian-laptop kernel: Symbols match kernel version 2.6.15.
Jun 16 11:11:36 brian-laptop kernel: Loaded 17827 symbols from 89 modules.
Jun 16 11:11:36 brian-laptop kernel: [17179569.184000] Linux version 2.6.15-51-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue Feb 12 16:52:52 UTC 2008
Jun 16 11:11:36 brian-laptop kernel: [17179569.184000] BIOS-provided physical RAM map:
Jun 16 11:11:36 brian-laptop kernel: [17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Jun 16 11:11:36 brian-laptop kernel: [17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Jun 16 11:11:36 brian-laptop kernel: [17179569.184000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Jun 16 11:11:36 brian-laptop kernel: [17179569.184000]  BIOS-e820: 0000000000100000 - 0000000077ea0000 (usable)
Jun 16 11:11:36 brian-laptop kernel: [17179569.184000]  BIOS-e820: 0000000077ea0000 - 0000000077eb0000 (ACPI data)
Jun 16 11:11:36 brian-laptop kernel: [17179569.184000]  BIOS-e820: 0000000077eb0000 - 0000000077f00000 (ACPI NVS)
Jun 16 11:11:36 brian-laptop kernel: [17179569.184000]  BIOS-e820: 0000000077f00000 - 0000000078000000 (reserved)
Jun 16 11:11:36 brian-laptop kernel: [17179569.184000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Jun 16 11:11:36 brian-laptop kernel: [17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Jun 16 11:11:36 brian-laptop kernel: [17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jun 16 11:11:36 brian-laptop kernel: [17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
Jun 16 11:11:36 brian-laptop kernel: [17179569.184000] 1022MB HIGHMEM available.
Jun 16 11:11:36 brian-laptop kernel: [17179569.184000] 896MB LOWMEM available.
Jun 16 11:11:36 brian-laptop kernel: [17179569.184000] found SMP MP-table at 000f7710
Jun 16 11:11:36 brian-laptop kernel: [17179569.184000] DMI present.
Jun 16 11:11:36 brian-laptop kernel: [17179569.184000] ATI board detected. Disabling timer routing over 8254.
Jun 16 11:11:36 brian-laptop kernel: [17179569.184000] ACPI: PM-Timer IO Port: 0x8008
Jun 16 11:11:36 brian-laptop kernel: [17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jun 16 11:11:36 brian-laptop kernel: [17179569.184000] Processor #0 6:13 APIC version 20
Jun 16 11:11:36 brian-laptop kernel: [17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jun 16 11:11:36 brian-laptop kernel: [17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Jun 16 11:11:36 brian-laptop kernel: [17179569.184000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
Jun 16 11:11:36 brian-laptop kernel: [17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Jun 16 11:11:36 brian-laptop kernel: [17179569.184000] ACPI: BIOS IRQ0 pin2 override ignored.
Jun 16 11:11:36 brian-laptop kernel: [17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
Jun 16 11:11:36 brian-laptop kernel: [17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jun 16 11:11:36 brian-laptop kernel: [17179569.184000] Using ACPI (MADT) for SMP configuration information
Jun 16 11:11:36 brian-laptop kernel: [17179569.184000] Allocating PCI resources starting at 80000000 (gap: 78000000:68000000)
Jun 16 11:11:36 brian-laptop kernel: [17179569.184000] Built 1 zonelists
Jun 16 11:11:36 brian-laptop kernel: [17179569.184000] Kernel command line: root=UUID=69acedc4-b024-4c0d-982d-4a8541611784 ro quiet splash
Jun 16 11:11:36 brian-laptop kernel: [17179569.184000] Initializing CPU#0
Jun 16 11:11:36 brian-laptop kernel: [17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
Jun 16 11:11:36 brian-laptop kernel: [17179569.184000] Detected 1692.243 MHz processor.
Jun 16 11:11:36 brian-laptop kernel: [17179569.184000] Using pmtmr for high-res timesource
Jun 16 11:11:36 brian-laptop kernel: [17179569.184000] Console: colour VGA+ 80x25
Jun 16 11:11:36 brian-laptop kernel: [17179569.612000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jun 16 11:11:36 brian-laptop kernel: [17179569.612000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jun 16 11:11:36 brian-laptop kernel: [17179569.704000] Memory: 1937240k/1964672k available (1977k kernel code, 26152k reserved, 605k data, 288k init, 1047168k highmem)
Jun 16 11:11:36 brian-laptop kernel: [17179569.704000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Jun 16 11:11:36 brian-laptop kernel: [17179569.784000] Calibrating delay using timer specific routine.. 3389.73 BogoMIPS (lpj=6779475)
Jun 16 11:11:36 brian-laptop kernel: [17179569.784000] Security Framework v1.0.0 initialized
Jun 16 11:11:36 brian-laptop kernel: [17179569.784000] SELinux:  Disabled at boot.
Jun 16 11:11:36 brian-laptop kernel: [17179569.784000] Mount-cache hash table entries: 512
Jun 16 11:11:36 brian-laptop kernel: [17179569.784000] CPU: L1 I cache: 32K, L1 D cache: 32K
Jun 16 11:11:36 brian-laptop kernel: [17179569.784000] CPU: L2 cache: 1024K
Jun 16 11:11:36 brian-laptop kernel: [17179569.784000] mtrr: v2.0 (20020519)
Jun 16 11:11:36 brian-laptop kernel: [17179569.784000] CPU: Intel(R) Celeron(R) M processor         1.70GHz stepping 08
Jun 16 11:11:36 brian-laptop kernel: [17179569.784000] Enabling fast FPU save and restore... done.
Jun 16 11:11:36 brian-laptop kernel: [17179569.784000] Enabling unmasked SIMD FPU exception support... done.
Jun 16 11:11:36 brian-laptop kernel: [17179569.784000] Checking 'hlt' instruction... OK.
Jun 16 11:11:36 brian-laptop kernel: [17179569.800000] checking if image is initramfs... it is
Jun 16 11:11:36 brian-laptop kernel: [17179570.428000] Freeing initrd memory: 6668k freed
Jun 16 11:11:36 brian-laptop kernel: [17179570.444000] ACPI: Looking for DSDT ... not found!
Jun 16 11:11:36 brian-laptop kernel: [17179570.460000] ENABLING IO-APIC IRQs
Jun 16 11:11:36 brian-laptop kernel: [17179570.460000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
Jun 16 11:11:36 brian-laptop kernel: [17179570.604000] NET: Registered protocol family 16
Jun 16 11:11:36 brian-laptop kernel: [17179570.604000] EISA bus registered
Jun 16 11:11:36 brian-laptop kernel: [17179570.604000] ACPI: bus type pci registered
Jun 16 11:11:36 brian-laptop kernel: [17179570.604000] PCI: PCI BIOS revision 2.10 entry at 0xfd82c, last bus=4
Jun 16 11:11:36 brian-laptop kernel: [17179570.604000] PCI: Using MMCONFIG
Jun 16 11:11:36 brian-laptop kernel: [17179570.604000] ACPI: Subsystem revision 20051216
Jun 16 11:11:36 brian-laptop kernel: [17179570.620000] ACPI: Interpreter enabled
Jun 16 11:11:36 brian-laptop kernel: [17179570.620000] ACPI: Using IOAPIC for interrupt routing
Jun 16 11:11:36 brian-laptop kernel: [17179570.620000] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jun 16 11:11:36 brian-laptop kernel: [17179570.620000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:14.1
Jun 16 11:11:36 brian-laptop kernel: [17179570.620000] PCI: Transparent bridge - 0000:00:14.4
Jun 16 11:11:36 brian-laptop kernel: [17179570.624000] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
Jun 16 11:11:36 brian-laptop kernel: [17179570.624000] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
Jun 16 11:11:36 brian-laptop kernel: [17179570.624000] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
Jun 16 11:11:36 brian-laptop kernel: [17179570.624000] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
Jun 16 11:11:36 brian-laptop kernel: [17179570.624000] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
Jun 16 11:11:36 brian-laptop kernel: [17179570.624000] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
Jun 16 11:11:36 brian-laptop kernel: [17179570.624000] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
Jun 16 11:11:36 brian-laptop kernel: [17179570.624000] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
Jun 16 11:11:36 brian-laptop kernel: [17179570.628000] ACPI: Embedded Controller [EC0] (gpe 7) interrupt mode.
Jun 16 11:11:36 brian-laptop kernel: [17179570.628000] ACPI: Power Resource [PFA1] (off)
Jun 16 11:11:36 brian-laptop kernel: [17179570.628000] Linux Plug and Play Support v0.97 (c) Adam Belay
Jun 16 11:11:36 brian-laptop kernel: [17179570.628000] pnp: PnP ACPI init
Jun 16 11:11:36 brian-laptop kernel: [17179570.644000] pnp: PnP ACPI: found 9 devices
Jun 16 11:11:36 brian-laptop kernel: [17179570.644000] PnPBIOS: Disabled by ACPI PNP
Jun 16 11:11:36 brian-laptop kernel: [17179570.644000] PCI: Using ACPI for IRQ routing
Jun 16 11:11:36 brian-laptop kernel: [17179570.644000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jun 16 11:11:36 brian-laptop kernel: [17179570.656000] pnp: 00:07: ioport range 0x1080-0x1080 has been reserved
Jun 16 11:11:36 brian-laptop kernel: [17179570.656000] pnp: 00:07: ioport range 0x220-0x22f has been reserved
Jun 16 11:11:36 brian-laptop kernel: [17179570.656000] pnp: 00:07: ioport range 0x400-0x401 has been reserved
Jun 16 11:11:36 brian-laptop kernel: [17179570.656000] pnp: 00:07: ioport range 0x40b-0x40b has been reserved
Jun 16 11:11:36 brian-laptop kernel: [17179570.656000] PCI: Bridge: 0000:00:01.0
Jun 16 11:11:36 brian-laptop kernel: [17179570.656000]   IO window: 9000-9fff
Jun 16 11:11:36 brian-laptop kernel: [17179570.656000]   MEM window: c0100000-c01fffff
Jun 16 11:11:36 brian-laptop kernel: [17179570.656000]   PREFETCH window: d0000000-dfffffff
Jun 16 11:11:36 brian-laptop kernel: [17179570.656000] PCI: Bus 3, cardbus bridge: 0000:02:06.0
Jun 16 11:11:36 brian-laptop kernel: [17179570.656000]   IO window: 0000a400-0000a4ff
Jun 16 11:11:36 brian-laptop kernel: [17179570.656000]   IO window: 0000a800-0000a8ff
Jun 16 11:11:36 brian-laptop kernel: [17179570.656000]   PREFETCH window: 80000000-81ffffff
Jun 16 11:11:36 brian-laptop kernel: [17179570.656000]   MEM window: 84000000-85ffffff
Jun 16 11:11:36 brian-laptop kernel: [17179570.656000] PCI: Bridge: 0000:00:14.4
Jun 16 11:11:36 brian-laptop kernel: [17179570.656000]   IO window: a000-afff
Jun 16 11:11:36 brian-laptop kernel: [17179570.656000]   MEM window: c0200000-c02fffff
Jun 16 11:11:36 brian-laptop kernel: [17179570.656000]   PREFETCH window: 80000000-81ffffff
Jun 16 11:11:36 brian-laptop kernel: [17179570.656000] PCI: Enabling device 0000:02:06.0 (0004 -> 0007)
Jun 16 11:11:36 brian-laptop kernel: [17179570.656000] ACPI: PCI Interrupt 0000:02:06.0[A] -> GSI 23 (level, low) -> IRQ 185
Jun 16 11:11:36 brian-laptop kernel: [17179570.656000] audit: initializing netlink socket (disabled)
Jun 16 11:11:36 brian-laptop kernel: [17179570.656000] audit(1213614662.656:1): initialized
Jun 16 11:11:36 brian-laptop kernel: [17179570.656000] highmem bounce pool size: 64 pages
Jun 16 11:11:36 brian-laptop kernel: [17179570.656000] VFS: Disk quotas dquot_6.5.1
Jun 16 11:11:36 brian-laptop kernel: [17179570.656000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jun 16 11:11:36 brian-laptop kernel: [17179570.656000] Initializing Cryptographic API
Jun 16 11:11:36 brian-laptop kernel: [17179570.656000] io scheduler noop registered
Jun 16 11:11:36 brian-laptop kernel: [17179570.656000] io scheduler anticipatory registered
Jun 16 11:11:36 brian-laptop kernel: [17179570.656000] io scheduler deadline registered
Jun 16 11:11:36 brian-laptop kernel: [17179570.656000] io scheduler cfq registered
Jun 16 11:11:36 brian-laptop kernel: [17179570.656000] isapnp: Scanning for PnP cards...
Jun 16 11:11:36 brian-laptop kernel: [17179571.012000] isapnp: No Plug & Play device found
Jun 16 11:11:36 brian-laptop kernel: [17179571.028000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
Jun 16 11:11:36 brian-laptop kernel: [17179571.036000] serio: i8042 AUX port at 0x60,0x64 irq 12
Jun 16 11:11:36 brian-laptop kernel: [17179571.036000] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun 16 11:11:36 brian-laptop kernel: [17179571.036000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
Jun 16 11:11:36 brian-laptop kernel: [17179571.040000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jun 16 11:11:36 brian-laptop kernel: [17179571.040000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jun 16 11:11:36 brian-laptop kernel: [17179571.040000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jun 16 11:11:36 brian-laptop kernel: [17179571.040000] mice: PS/2 mouse device common for all mice
Jun 16 11:11:36 brian-laptop kernel: [17179571.040000] EISA: Probing bus 0 at eisa.0
Jun 16 11:11:36 brian-laptop kernel: [17179571.040000] Cannot allocate resource for EISA slot 1
Jun 16 11:11:36 brian-laptop kernel: [17179571.040000] Cannot allocate resource for EISA slot 8
Jun 16 11:11:36 brian-laptop kernel: [17179571.040000] EISA: Detected 0 cards.
Jun 16 11:11:36 brian-laptop kernel: [17179571.040000] NET: Registered protocol family 2
Jun 16 11:11:36 brian-laptop kernel: [17179571.076000] IP route cache hash table entries: 65536 (order: 6, 262144 bytes)
Jun 16 11:11:36 brian-laptop kernel: [17179571.076000] TCP established hash table entries: 262144 (order: 8, 1048576 bytes)
Jun 16 11:11:36 brian-laptop kernel: [17179571.076000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
Jun 16 11:11:36 brian-laptop kernel: [17179571.080000] TCP: Hash tables configured (established 262144 bind 65536)
Jun 16 11:11:36 brian-laptop kernel: [17179571.080000] TCP reno registered
Jun 16 11:11:36 brian-laptop kernel: [17179571.080000] TCP bic registered
Jun 16 11:11:36 brian-laptop kernel: [17179571.080000] NET: Registered protocol family 1
Jun 16 11:11:36 brian-laptop kernel: [17179571.080000] NET: Registered protocol family 8
Jun 16 11:11:36 brian-laptop kernel: [17179571.080000] NET: Registered protocol family 20
Jun 16 11:11:36 brian-laptop kernel: [17179571.080000] Using IPI Shortcut mode
Jun 16 11:11:36 brian-laptop kernel: [17179571.080000] ACPI wakeup devices: 
Jun 16 11:11:36 brian-laptop kernel: [17179571.080000]  LID OHC1 OHC2 EHCI  P2P LANC AUDO MODM 
Jun 16 11:11:36 brian-laptop kernel: [17179571.080000] ACPI: (supports S0 S3 S4 S5)
Jun 16 11:11:36 brian-laptop kernel: [17179571.080000] Freeing unused kernel memory: 288k freed
Jun 16 11:11:36 brian-laptop kernel: [17179571.084000] input: AT Translated Set 2 keyboard as /class/input/input0
Jun 16 11:11:36 brian-laptop kernel: [17179571.124000] vga16fb: mapped to 0xc00a0000
Jun 16 11:11:36 brian-laptop kernel: [17179571.228000] Console: switching to colour frame buffer device 80x25
Jun 16 11:11:36 brian-laptop kernel: [17179571.228000] fb0: VGA16 VGA frame buffer device
Jun 16 11:11:36 brian-laptop kernel: [17179572.404000] Capability LSM initialized
Jun 16 11:11:36 brian-laptop kernel: [17179572.432000] ACPI: Fan [FAN1] (off)
Jun 16 11:11:36 brian-laptop kernel: [17179572.436000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Jun 16 11:11:36 brian-laptop kernel: [17179572.436000] ACPI: Processor [CPU0] (supports 8 throttling states)
Jun 16 11:11:36 brian-laptop kernel: [17179572.644000] ACPI: Thermal Zone [TZCR] (50 C)
Jun 16 11:11:36 brian-laptop kernel: [17179573.072000] SCSI subsystem initialized
Jun 16 11:11:36 brian-laptop kernel: [17179573.072000] ACPI: bus type scsi registered
Jun 16 11:11:36 brian-laptop kernel: [17179573.072000] PCI: Enabling device 0000:00:12.0 (0005 -> 0007)
Jun 16 11:11:36 brian-laptop kernel: [17179573.072000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 193
Jun 16 11:11:36 brian-laptop kernel: [17179573.072000] ata1: SATA max UDMA/100 cmd 0xF8870080 ctl 0xF887008A bmdma 0xF8870000 irq 193
Jun 16 11:11:36 brian-laptop kernel: [17179573.072000] ata2: SATA max UDMA/100 cmd 0xF88700C0 ctl 0xF88700CA bmdma 0xF8870008 irq 193
Jun 16 11:11:36 brian-laptop kernel: [17179573.440000] ata1: dev 0 ATA-7, max UDMA/100, 156301488 sectors: LBA48
Jun 16 11:11:36 brian-laptop kernel: [17179573.472000] ata1: dev 0 configured for UDMA/100
Jun 16 11:11:36 brian-laptop kernel: [17179573.504000] scsi0 : sata_sil
Jun 16 11:11:36 brian-laptop kernel: [17179573.708000] ata2: no device found (phy stat 00000000)
Jun 16 11:11:36 brian-laptop kernel: [17179573.708000] scsi1 : sata_sil
Jun 16 11:11:36 brian-laptop kernel: [17179573.708000]   Vendor: ATA       Model: HTS541080G9SA00   Rev: MB4O
Jun 16 11:11:36 brian-laptop kernel: [17179573.708000]   Type:   Direct-Access                      ANSI SCSI revision: 05
Jun 16 11:11:36 brian-laptop kernel: [17179573.712000] Driver 'sd' needs updating - please use bus_type methods
Jun 16 11:11:36 brian-laptop kernel: [17179573.712000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
Jun 16 11:11:36 brian-laptop kernel: [17179573.712000] SCSI device sda: drive cache: write back
Jun 16 11:11:36 brian-laptop kernel: [17179573.716000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
Jun 16 11:11:36 brian-laptop kernel: [17179573.716000] SCSI device sda: drive cache: write back
Jun 16 11:11:36 brian-laptop kernel: [17179573.716000]  sda: sda1 sda2 sda3 sda4
Jun 16 11:11:36 brian-laptop kernel: [17179573.764000] sd 0:0:0:0: Attached scsi disk sda
Jun 16 11:11:36 brian-laptop kernel: [17179574.088000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
Jun 16 11:11:36 brian-laptop kernel: [17179574.088000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 201
Jun 16 11:11:36 brian-laptop kernel: [17179574.088000] ATIIXP: chipset revision 128
Jun 16 11:11:36 brian-laptop kernel: [17179574.088000] ATIIXP: not 100% native mode: will probe irqs later
Jun 16 11:11:36 brian-laptop kernel: [17179574.088000]     ide0: BM-DMA at 0x8460-0x8467, BIOS settings: hda:pio, hdb:pio
Jun 16 11:11:36 brian-laptop kernel: [17179574.088000]     ide1: BM-DMA at 0x8468-0x846f, BIOS settings: hdc:DMA, hdd:pio
Jun 16 11:11:36 brian-laptop kernel: [17179575.392000] hdc: DVD/CDRW UJDA770, ATAPI CD/DVD-ROM drive
Jun 16 11:11:36 brian-laptop kernel: [17179575.728000] ide1 at 0x170-0x177,0x376 on irq 15
Jun 16 11:11:36 brian-laptop kernel: [17179575.736000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Jun 16 11:11:36 brian-laptop kernel: [17179575.736000] Uniform CD-ROM driver Revision: 3.20
Jun 16 11:11:36 brian-laptop kernel: [17179575.848000] usbcore: registered new driver usbfs
Jun 16 11:11:36 brian-laptop kernel: [17179575.848000] usbcore: registered new driver hub
Jun 16 11:11:36 brian-laptop kernel: [17179575.848000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 209
Jun 16 11:11:36 brian-laptop kernel: [17179575.848000] ohci_hcd 0000:00:13.0: OHCI Host Controller
Jun 16 11:11:36 brian-laptop kernel: [17179576.188000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
Jun 16 11:11:36 brian-laptop kernel: [17179576.188000] ohci_hcd 0000:00:13.0: irq 209, io mem 0xc0005000
Jun 16 11:11:36 brian-laptop kernel: [17179576.244000] hub 1-0:1.0: USB hub found
Jun 16 11:11:36 brian-laptop kernel: [17179576.244000] hub 1-0:1.0: 4 ports detected
Jun 16 11:11:36 brian-laptop kernel: [17179576.348000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 209
Jun 16 11:11:36 brian-laptop kernel: [17179576.348000] ohci_hcd 0000:00:13.1: OHCI Host Controller
Jun 16 11:11:36 brian-laptop kernel: [17179576.688000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
Jun 16 11:11:36 brian-laptop kernel: [17179576.688000] ohci_hcd 0000:00:13.1: irq 209, io mem 0xc0006000
Jun 16 11:11:36 brian-laptop kernel: [17179576.744000] hub 2-0:1.0: USB hub found
Jun 16 11:11:36 brian-laptop kernel: [17179576.744000] hub 2-0:1.0: 4 ports detected
Jun 16 11:11:36 brian-laptop kernel: [17179576.848000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 209
Jun 16 11:11:36 brian-laptop kernel: [17179576.848000] ehci_hcd 0000:00:13.2: EHCI Host Controller
Jun 16 11:11:36 brian-laptop kernel: [17179576.848000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
Jun 16 11:11:36 brian-laptop kernel: [17179576.848000] ehci_hcd 0000:00:13.2: irq 209, io mem 0xc0007000
Jun 16 11:11:36 brian-laptop kernel: [17179576.848000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jun 16 11:11:36 brian-laptop kernel: [17179576.848000] hub 3-0:1.0: USB hub found
Jun 16 11:11:36 brian-laptop kernel: [17179576.848000] hub 3-0:1.0: 8 ports detected
Jun 16 11:11:36 brian-laptop kernel: [17179577.564000] Attempting manual resume
Jun 16 11:11:36 brian-laptop kernel: [17179577.576000] EXT3-fs: INFO: recovery required on readonly filesystem.
Jun 16 11:11:36 brian-laptop kernel: [17179577.576000] EXT3-fs: write access will be enabled during recovery.
Jun 16 11:11:36 brian-laptop kernel: [17179582.972000] EXT3-fs: recovery complete.
Jun 16 11:11:36 brian-laptop kernel: [17179582.972000] kjournald starting.  Commit interval 5 seconds
Jun 16 11:11:36 brian-laptop kernel: [17179582.976000] EXT3-fs: mounted filesystem with ordered data mode.
Jun 16 11:11:36 brian-laptop kernel: [17179594.348000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun 16 11:11:36 brian-laptop kernel: [17179594.384000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jun 16 11:11:36 brian-laptop kernel: [17179594.736000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jun 16 11:11:36 brian-laptop kernel: [17179594.800000] Linux agpgart interface v0.101 (c) Dave Jones
Jun 16 11:11:36 brian-laptop kernel: [17179594.900000] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 201
Jun 16 11:11:36 brian-laptop kernel: [17179595.108000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0
Jun 16 11:11:36 brian-laptop kernel: [17179595.108000] synaptics: Toshiba Satellite A105 detected, limiting rate to 40pps.
Jun 16 11:11:36 brian-laptop kernel: [17179595.116000] input: PC Speaker as /class/input/input1
Jun 16 11:11:36 brian-laptop kernel: [17179595.144000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
Jun 16 11:11:36 brian-laptop kernel: [17179595.184000] ath_hal: module license 'Proprietary' taints kernel.
Jun 16 11:11:36 brian-laptop kernel: [17179595.184000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
Jun 16 11:11:36 brian-laptop kernel: [17179595.288000] wlan: 0.8.6.0 (EXPERIMENTAL)
Jun 16 11:11:36 brian-laptop kernel: [17179595.300000] Real Time Clock Driver v1.12
Jun 16 11:11:36 brian-laptop kernel: [17179595.340000] ath_rate_sample: 1.2
Jun 16 11:11:36 brian-laptop kernel: [17179595.344000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
Jun 16 11:11:36 brian-laptop kernel: [17179595.360000] 8139too Fast Ethernet driver 0.9.27
Jun 16 11:11:36 brian-laptop kernel: [17179595.628000] hda_codec: Unknown model for ALC861, trying auto-probe from BIOS...
Jun 16 11:11:36 brian-laptop kernel: [17179595.852000] ACPI: PCI Interrupt 0000:02:06.0[A] -> GSI 23 (level, low) -> IRQ 185
Jun 16 11:11:36 brian-laptop kernel: [17179595.852000] Yenta: CardBus bridge found at 0000:02:06.0 [1179:ff10]
Jun 16 11:11:36 brian-laptop kernel: [17179595.852000] Yenta: Enabling burst memory read transactions
Jun 16 11:11:36 brian-laptop kernel: [17179595.852000] Yenta: Using CSCINT to route CSC interrupts to PCI
Jun 16 11:11:36 brian-laptop kernel: [17179595.852000] Yenta: Routing CardBus interrupts to PCI
Jun 16 11:11:36 brian-laptop kernel: [17179595.852000] Yenta TI: socket 0000:02:06.0, mfunc 0x01111122, devctl 0x44
Jun 16 11:11:36 brian-laptop kernel: [17179595.852000] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 20 (level, low) -> IRQ 217
Jun 16 11:11:36 brian-laptop kernel: [17179596.136000] Yenta: ISA IRQ mask 0x0ef8, PCI irq 185
Jun 16 11:11:36 brian-laptop kernel: [17179596.136000] Socket status: 30000006
Jun 16 11:11:36 brian-laptop kernel: [17179596.136000] Yenta: Raising subordinate bus# of parent bus (#02) from #04 to #06
Jun 16 11:11:36 brian-laptop kernel: [17179596.136000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
Jun 16 11:11:36 brian-laptop kernel: [17179596.136000] cs: IO port probe 0xa000-0xafff: clean.
Jun 16 11:11:36 brian-laptop kernel: [17179596.136000] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xc02fffff
Jun 16 11:11:36 brian-laptop kernel: [17179596.136000] pcmcia: parent PCI bridge Memory window: 0x80000000 - 0x81ffffff
Jun 16 11:11:36 brian-laptop kernel: [17179596.436000] Build date: Feb  4 2008
Jun 16 11:11:36 brian-laptop kernel: [17179596.436000] Debugging version (IEEE80211)
Jun 16 11:11:36 brian-laptop kernel: [17179596.436000] ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
Jun 16 11:11:36 brian-laptop kernel: [17179596.436000] ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Jun 16 11:11:36 brian-laptop kernel: [17179596.436000] ath0: H/W encryption support: WEP AES AES_CCM TKIP
Jun 16 11:11:36 brian-laptop kernel: [17179596.436000] ath0: mac 7.8 phy 4.5 radio 5.6
Jun 16 11:11:36 brian-laptop kernel: [17179596.436000] ath0: Use hw queue 1 for WME_AC_BE traffic
Jun 16 11:11:36 brian-laptop kernel: [17179596.436000] ath0: Use hw queue 0 for WME_AC_BK traffic
Jun 16 11:11:36 brian-laptop kernel: [17179596.436000] ath0: Use hw queue 2 for WME_AC_VI traffic
Jun 16 11:11:36 brian-laptop kernel: [17179596.436000] ath0: Use hw queue 3 for WME_AC_VO traffic
Jun 16 11:11:36 brian-laptop kernel: [17179596.436000] ath0: Use hw queue 8 for CAB traffic
Jun 16 11:11:36 brian-laptop kernel: [17179596.436000] ath0: Use hw queue 9 for beacons
Jun 16 11:11:36 brian-laptop kernel: [17179596.436000] Debugging version (ATH)
Jun 16 11:11:36 brian-laptop kernel: [17179596.436000] ath0: Atheros 5212: mem=0xc0200000, irq=217
Jun 16 11:11:36 brian-laptop kernel: [17179596.460000] ACPI: PCI Interrupt 0000:02:07.0[A] -> GSI 20 (level, low) -> IRQ 217
Jun 16 11:11:36 brian-laptop kernel: [17179596.460000] eth0: RealTek RTL8139 at 0xf88f6000, 00:a0:d1:3c:bc:b1, IRQ 217
Jun 16 11:11:36 brian-laptop kernel: [17179596.472000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
Jun 16 11:11:36 brian-laptop kernel: [17179596.496000] eth0: link up, 100Mbps, full-duplex, lpa 0xC3E1
Jun 16 11:11:36 brian-laptop kernel: [17179596.796000] cs: IO port probe 0x100-0x3af: excluding 0x1f0-0x1f7
Jun 16 11:11:36 brian-laptop kernel: [17179596.800000] cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x4d0-0x4d7
Jun 16 11:11:36 brian-laptop kernel: [17179596.800000] cs: IO port probe 0x820-0x8ff: excluding 0x878-0x87f
Jun 16 11:11:36 brian-laptop kernel: [17179596.800000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
Jun 16 11:11:36 brian-laptop kernel: [17179596.804000] cs: IO port probe 0xa00-0xaff: clean.
Jun 16 11:11:36 brian-laptop kernel: [17179597.976000] NET: Registered protocol family 17
Jun 16 11:11:36 brian-laptop kernel: [17179597.988000] lp: driver loaded but no devices found
Jun 16 11:11:36 brian-laptop kernel: [17179598.036000] fuse init (API version 7.3)
Jun 16 11:11:36 brian-laptop kernel: [17179598.240000] Adding 2000084k swap on /dev/sda3.  Priority:-1 extents:1 across:2000084k
Jun 16 11:11:36 brian-laptop kernel: [17179598.540000] EXT3 FS on sda4, internal journal
Jun 16 11:11:36 brian-laptop kernel: [17179599.320000] ip_tables: (C) 2000-2002 Netfilter core team
Jun 16 11:11:36 brian-laptop kernel: [17179600.040000] NET: Registered protocol family 10
Jun 16 11:11:36 brian-laptop kernel: [17179600.040000] lo: Disabled Privacy Extensions
Jun 16 11:11:36 brian-laptop kernel: [17179600.040000] IPv6 over IPv4 tunneling driver
Jun 16 11:11:36 brian-laptop kernel: [17179603.724000] ACPI: Battery Slot [BAT0] (battery present)
Jun 16 11:11:36 brian-laptop kernel: [17179604.120000] ACPI: AC Adapter [ADP0] (on-line)
Jun 16 11:11:36 brian-laptop kernel: [17179604.184000] ACPI: Power Button (FF) [PWRF]
Jun 16 11:11:36 brian-laptop kernel: [17179604.184000] ACPI: Power Button (CM) [PWRB]
Jun 16 11:11:36 brian-laptop kernel: [17179604.184000] ACPI: Lid Switch [LID]
Jun 16 11:11:36 brian-laptop kernel: [17179604.340000] pcc_acpi: loading...
Jun 16 11:11:39 brian-laptop kernel: [17179607.756000] ppdev: user-space parallel port driver
Jun 16 11:11:39 brian-laptop kernel: [17179607.980000] apm: BIOS not found.
Jun 16 11:11:39 brian-laptop dhcdbd: Started up.
Jun 16 11:11:47 brian-laptop kernel: [17179615.612000] hda-intel: Invalid position buffer, using LPIB read method instead.
Jun 16 11:12:39 brian-laptop kernel: [17179668.092000]     ACPI-0307: *** Error: No installed handler for fixed event [00000000]
Jun 16 11:18:32 brian-laptop exiting on signal 15
```

Contents of /var/log/Xorg.0.log:

```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux brian-laptop 2.6.15-51-386 #1 PREEMPT Tue Feb 12 16:52:52 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jun 16 11:11:38 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(**) |-->Input Device "Synaptics Touchpad"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1002,5a31 card 1179,ff10 rev 01 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1002,5a3f card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:12:0: chip 1002,4379 card 1179,ff10 rev 80 class 01,01,8f hdr 00
(II) PCI: 00:13:0: chip 1002,4374 card 1179,ff10 rev 80 class 0c,03,10 hdr 80
(II) PCI: 00:13:1: chip 1002,4375 card 1179,ff10 rev 80 class 0c,03,10 hdr 00
(II) PCI: 00:13:2: chip 1002,4373 card 1179,ff10 rev 80 class 0c,03,20 hdr 00
(II) PCI: 00:14:0: chip 1002,4372 card 1179,ff10 rev 81 class 0c,05,00 hdr 80
(II) PCI: 00:14:1: chip 1002,4376 card 1179,ff10 rev 80 class 01,01,8a hdr 00
(II) PCI: 00:14:2: chip 1002,437b card 1179,ff10 rev 01 class 04,03,00 hdr 00
(II) PCI: 00:14:3: chip 1002,4377 card 1179,ff10 rev 80 class 06,01,00 hdr 80
(II) PCI: 00:14:4: chip 1002,4371 card 0000,0000 rev 80 class 06,04,01 hdr 81
(II) PCI: 01:05:0: chip 1002,5a62 card 1179,ff10 rev 00 class 03,00,00 hdr 00
(II) PCI: 02:04:0: chip 168c,001a card 144f,7094 rev 01 class 02,00,00 hdr 00
(II) PCI: 02:06:0: chip 1524,1410 card a400,0000 rev 01 class 06,07,00 hdr 02
(II) PCI: 02:07:0: chip 10ec,8139 card 1179,ff10 rev 10 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xc0100000 - 0xc01fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:20:3), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:20:4), (0,2,6), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xc0200000 - 0xc02fffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x80000000 - 0x81ffffff (0x2000000) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 3: bridge is at (2:6:0), (2,3,6), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[1] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0x80000000 - 0x81ffffff (0x2000000) MX[B]
(--) PCI:*(1:5:0) ATI Technologies Inc RC410 [Radeon Xpress 200M] rev 0, Mem @ 0xd0000000/28, 0xc0100000/16, I/O @ 0x9000/8
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xc0211000 - 0xc02110ff (0x100) MX[B]
	[1] -1	0	0xc0200000 - 0xc020ffff (0x10000) MX[B]
	[2] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[3] -1	0	0xc0004400 - 0xc00047ff (0x400) MX[B]
	[4] -1	0	0xc0007000 - 0xc0007fff (0x1000) MX[B]
	[5] -1	0	0xc0006000 - 0xc0006fff (0x1000) MX[B]
	[6] -1	0	0xc0005000 - 0xc0005fff (0x1000) MX[B]
	[7] -1	0	0xc0004000 - 0xc00041ff (0x200) MX[B]
	[8] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[10] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[11] -1	0	0x00008460 - 0x0000846f (0x10) IX[B]
	[12] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[13] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[14] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x00008450 - 0x0000845f (0x10) IX[B]
	[17] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[18] -1	0	0x00008410 - 0x00008413 (0x4) IX[B]
	[19] -1	0	0x00008420 - 0x00008427 (0x8) IX[B]
	[20] -1	0	0x00008430 - 0x00008433 (0x4) IX[B]
	[21] -1	0	0x00008440 - 0x00008447 (0x8) IX[B]
	[22] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xc0211000 - 0xc02110ff (0x100) MX[B]
	[1] -1	0	0xc0200000 - 0xc020ffff (0x10000) MX[B]
	[2] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[3] -1	0	0xc0004400 - 0xc00047ff (0x400) MX[B]
	[4] -1	0	0xc0007000 - 0xc0007fff (0x1000) MX[B]
	[5] -1	0	0xc0006000 - 0xc0006fff (0x1000) MX[B]
	[6] -1	0	0xc0005000 - 0xc0005fff (0x1000) MX[B]
	[7] -1	0	0xc0004000 - 0xc00041ff (0x200) MX[B]
	[8] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[10] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[11] -1	0	0x00008460 - 0x0000846f (0x10) IX[B]
	[12] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[13] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[14] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x00008450 - 0x0000845f (0x10) IX[B]
	[17] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[18] -1	0	0x00008410 - 0x00008413 (0x4) IX[B]
	[19] -1	0	0x00008420 - 0x00008427 (0x8) IX[B]
	[20] -1	0	0x00008430 - 0x00008433 (0x4) IX[B]
	[21] -1	0	0x00008440 - 0x00008447 (0x8) IX[B]
	[22] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc0211000 - 0xc02110ff (0x100) MX[B]
	[5] -1	0	0xc0200000 - 0xc020ffff (0x10000) MX[B]
	[6] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[7] -1	0	0xc0004400 - 0xc00047ff (0x400) MX[B]
	[8] -1	0	0xc0007000 - 0xc0007fff (0x1000) MX[B]
	[9] -1	0	0xc0006000 - 0xc0006fff (0x1000) MX[B]
	[10] -1	0	0xc0005000 - 0xc0005fff (0x1000) MX[B]
	[11] -1	0	0xc0004000 - 0xc00041ff (0x200) MX[B]
	[12] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[17] -1	0	0x00008460 - 0x0000846f (0x10) IX[B]
	[18] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[19] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[20] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x00008450 - 0x0000845f (0x10) IX[B]
	[23] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[24] -1	0	0x00008410 - 0x00008413 (0x4) IX[B]
	[25] -1	0	0x00008420 - 0x00008427 (0x8) IX[B]
	[26] -1	0	0x00008430 - 0x00008433 (0x4) IX[B]
	[27] -1	0	0x00008440 - 0x00008447 (0x8) IX[B]
	[28] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) Matched ati from file name ati.ids in autoconfig
(==) Matched ati for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 6.8.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 4.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(WW) Warning, couldn't open module mouse
(II) UnloadModule: "mouse"
(EE) Failed to load module "mouse" (module does not exist, 0)
(II) LoadModule: "kbd"
(WW) Warning, couldn't open module kbd
(II) UnloadModule: "kbd"
(EE) Failed to load module "kbd" (module does not exist, 0)
(II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI Radeon X550XTX (RV370) 5657 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI  Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600, ATI RV610,
	ATI Radeon HD 2400 XT, ATI Radeon HD 2400 Pro,
	ATI ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000, ATI RV610,
	ATI ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI ATI RADEON E2400, ATI RV610,
	ATI RV670, ATI Radeon HD3870, ATI Radeon HD3850, ATI RV670,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI ATI Radeon HD 2600 XT AGP, ATI ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini ATI Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI ATI Radeon HD 2600 LE
(II) Primary Device is: PCI 01:05:0
(--) Assigning device section with no busID to primary device
(--) Chipset ATI Radeon XPRESS 200M 5A62 (PCIE) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc0211000 - 0xc02110ff (0x100) MX[B]
	[5] -1	0	0xc0200000 - 0xc020ffff (0x10000) MX[B]
	[6] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[7] -1	0	0xc0004400 - 0xc00047ff (0x400) MX[B]
	[8] -1	0	0xc0007000 - 0xc0007fff (0x1000) MX[B]
	[9] -1	0	0xc0006000 - 0xc0006fff (0x1000) MX[B]
	[10] -1	0	0xc0005000 - 0xc0005fff (0x1000) MX[B]
	[11] -1	0	0xc0004000 - 0xc00041ff (0x200) MX[B]
	[12] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[17] -1	0	0x00008460 - 0x0000846f (0x10) IX[B]
	[18] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[19] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[20] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x00008450 - 0x0000845f (0x10) IX[B]
	[23] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[24] -1	0	0x00008410 - 0x00008413 (0x4) IX[B]
	[25] -1	0	0x00008420 - 0x00008427 (0x8) IX[B]
	[26] -1	0	0x00008430 - 0x00008433 (0x4) IX[B]
	[27] -1	0	0x00008440 - 0x00008447 (0x8) IX[B]
	[28] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc0211000 - 0xc02110ff (0x100) MX[B]
	[5] -1	0	0xc0200000 - 0xc020ffff (0x10000) MX[B]
	[6] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[7] -1	0	0xc0004400 - 0xc00047ff (0x400) MX[B]
	[8] -1	0	0xc0007000 - 0xc0007fff (0x1000) MX[B]
	[9] -1	0	0xc0006000 - 0xc0006fff (0x1000) MX[B]
	[10] -1	0	0xc0005000 - 0xc0005fff (0x1000) MX[B]
	[11] -1	0	0xc0004000 - 0xc00041ff (0x200) MX[B]
	[12] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[20] -1	0	0x00008460 - 0x0000846f (0x10) IX[B]
	[21] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[22] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[23] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x00008450 - 0x0000845f (0x10) IX[B]
	[26] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[27] -1	0	0x00008410 - 0x00008413 (0x4) IX[B]
	[28] -1	0	0x00008420 - 0x00008427 (0x8) IX[B]
	[29] -1	0	0x00008430 - 0x00008433 (0x4) IX[B]
	[30] -1	0	0x00008440 - 0x00008447 (0x8) IX[B]
	[31] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): MMIO registers at 0x00000000c0100000: size 64KB
(II) RADEON(0): PCI bus 1 card 5 func 0
(II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) RADEON(0): Depth 24, (==) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon XPRESS 200M 5A62 (PCIE)" (ChipID = 0x5a62)
(--) RADEON(0): Linear framebuffer at 0x00000000d0000000
(II) RADEON(0): PCI card detected
(II) RADEON(0): Legacy BIOS detected
(II) RADEON(0): Direct rendering not officially supported on RN50/RC410/R600
(II) RADEON(0): Detected total video RAM=131072K, accessible=262144K (PCI BAR=262144K)
(--) RADEON(0): Mapped VideoRAM: 131072 kByte (256 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) RADEON(0): Max desktop size set to 2560x1200
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 1432, min_out_pll: 20000, max_out_pll: 40000, min_in_pll: 100, max_in_pll: 1350, xclk: 26600, sclk: 266.000000, mclk: 300.000000
(II) RADEON(0): PLL parameters: rf=1432 rd=6 min=20000 max=40000; xclk=26600
(WW) RADEON(0): LCD DDC Info Table found!
(II) RADEON(0): Bios Connector table: 
(II) RADEON(0): Port0: DDCType-0x68, DACType-2, TMDSType-1, ConnectorType-1
(II) RADEON(0): Port4: DDCType-0x1a0, DACType-0, TMDSType-0, ConnectorType-7
(II) RADEON(0): Port5: DDCType-0x0, DACType-2, TMDSType-0, ConnectorType-5
(II) RADEON(0): Output VGA-0 using monitor section Configured Monitor
(II) RADEON(0): I2C bus "VGA-0" initialized.
(II) RADEON(0): Output LVDS has no monitor section
(II) RADEON(0): Panel ID string: LPL                     
(II) RADEON(0): Panel Size from BIOS: 1280x800
(II) RADEON(0): BIOS provided dividers will be used.
(WW) RADEON(0): LVDS Info:
XRes: 1280, YRes: 800, DotClock: 71250
HBlank: 160, HOverPlus: 48, HSyncWidth: 32
VBlank: 23, VOverPlus: 2, VSyncWidth: 6
(II) RADEON(0): I2C bus "LVDS" initialized.
(II) RADEON(0): Output S-video has no monitor section
(II) RADEON(0): Default TV standard: NTSC
(II) RADEON(0): TV standards supported by chip: NTSC PAL NTSC-J 
(II) RADEON(0): Port0:
 Monitor   -- AUTO
 Connector -- VGA
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- None
 DDC Type  -- 0x68
(II) RADEON(0): Port1:
 Monitor   -- AUTO
 Connector -- LVDS
 DAC Type  -- None
 TMDS Type -- None
 DDC Type  -- 0x1a0
(II) RADEON(0): Port2:
 Monitor   -- AUTO
 Connector -- STV
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- None
 DDC Type  -- 0x0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
finished output detect: 0
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "LVDS:ddc2" removed.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
finished output detect: 1
finished output detect: 2
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "LVDS:ddc2" removed.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1280x800
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Output VGA-0 disconnected
(II) RADEON(0): Output LVDS connected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Output LVDS using initial mode 1280x800
after xf86InitialConfiguration
(==) RADEON(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(==) RADEON(0): Assuming overlay scaler buffer width is 1536
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xc0100000 - 0xc010ffff (0x10000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xc0211000 - 0xc02110ff (0x100) MX[B]
	[7] -1	0	0xc0200000 - 0xc020ffff (0x10000) MX[B]
	[8] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[9] -1	0	0xc0004400 - 0xc00047ff (0x400) MX[B]
	[10] -1	0	0xc0007000 - 0xc0007fff (0x1000) MX[B]
	[11] -1	0	0xc0006000 - 0xc0006fff (0x1000) MX[B]
	[12] -1	0	0xc0005000 - 0xc0005fff (0x1000) MX[B]
	[13] -1	0	0xc0004000 - 0xc00041ff (0x200) MX[B]
	[14] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[19] 0	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[23] -1	0	0x00008460 - 0x0000846f (0x10) IX[B]
	[24] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[25] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[26] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x00008450 - 0x0000845f (0x10) IX[B]
	[29] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[30] -1	0	0x00008410 - 0x00008413 (0x4) IX[B]
	[31] -1	0	0x00008420 - 0x00008427 (0x8) IX[B]
	[32] -1	0	0x00008430 - 0x00008433 (0x4) IX[B]
	[33] -1	0	0x00008440 - 0x00008447 (0x8) IX[B]
	[34] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) RADEON(0): RADEONScreenInit d0000000 0 0
(==) RADEON(0): Write-combining range (0xd0000000,0x8000000)
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
disable montype: 2
(II) RADEON(0): Dynamic Clock Scaling Disabled
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x08000000
(II) RADEON(0):   MC_FB_LOCATION   : 0x7fff7800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): Memory manager initialized to (0,0) (1280,8191)
(II) RADEON(0): Reserved area from (0,1200) to (1280,1202)
(II) RADEON(0): Largest offscreen area available: 1280 x 6989
disable montype: 2
init memmap
init common
init crtc1
init pll1
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x7fff7800 0x7fff7800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
restore LVDS
enable montype: 2
(WW) RADEON(0): No crtc mode list for crtc 1,continuing with desired mode
disable montype: 2
(==) RADEON(0): Backing store disabled
(WW) RADEON(0): Direct rendering disabled
(II) RADEON(0): Render acceleration unsupported on Radeon 9500/9700 and newer.
(II) RADEON(0): Render acceleration disabled
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) RADEON(0): Acceleration enabled
(II) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor 0 (scanline 1202)
(II) RADEON(0): Using hardware cursor 1 (scanline 1205)
(II) RADEON(0): Largest offscreen area available: 1280 x 6982
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(WW) RADEON(0): Option "UseFBDev" is not used
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) AIGLX: Screen 0 is not DRI capable
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 338 x 211
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
Synaptics Touchpad no synaptics event device found (checked 10 nodes)
Synaptics Touchpad The /dev/input/event* device nodes seem to be missing
(**) Option "Device" "/dev/psaux"
(**) Option "HorizEdgeScroll" "0"
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"
(EE) No Input driver matching `mouse'
(EE) No Input driver matching `kbd'
enable montype: 2
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "LVDS:ddc2" removed.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1280x800
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
disable montype: 2
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x7fff7800 0x7fff7800
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
finished PLL2
finished PLL1
Entering Restore TV
Restore TV PLL
Restore TVHV
Restore TV Restarts
Restore Timing Tables
Restore TV standard
Leaving Restore TV

```

---

### Post by Scienceman123 on 2008-06-17
Bump.

---

### Post by prshah on 2008-06-17
> **Scienceman123 said:**
> ```

(II) LoadModule: "mouse"
(WW) Warning, couldn't open module mouse
(II) UnloadModule: "mouse"
(EE) Failed to load module "mouse" (module does not exist, 0)
(II) LoadModule: "kbd"
(WW) Warning, couldn't open module kbd
(II) UnloadModule: "kbd"
(EE) Failed to load module "kbd" (module does not exist, 0)

```

There's your problem. Did you try the dpkg-reconfigure command in the previous post? If you did, post your /etc/X11/xorg.conf file. If you didn't perhaps you should try that now.

---

### Post by Scienceman123 on 2008-06-17
> **prshah said:**
> There's your problem. Did you try the dpkg-reconfigure command in the previous post? If you did, post your /etc/X11/xorg.conf file. If you didn't perhaps you should try that now.

Yeah, I tried that. Still doesn't work. Here's my xorg.conf:

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

```

Thanks for all you've done.

---

### Post by Scienceman123 on 2008-06-17
Bump

---

### Post by Scienceman123 on 2008-06-18
Bump. Is there a way to replace the drivers? I can access the partition from Windows XP.

---

### Post by prshah on 2008-06-18
> **Scienceman123 said:**
> Yeah, I tried that. Still doesn't work. Here's my xorg.conf:

Looks OK, can you post output of ```
ls -l /usr/lib/xorg/modules/input/
``` that's where all the common X driver modules are stored (kbd, mouse, etc)

If you can't see any mouse/kbd related files there (heck, even if you can) try this command```

sudo apt-get install xserver-xorg-input-all

```

Then restart. (and hope).

---

