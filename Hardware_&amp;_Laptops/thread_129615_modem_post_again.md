---
title: "modem post again"
date: 2006-02-14
forum: Hardware &amp; Laptops
---

### Post by hollowhead on 2006-02-14
I've had a poke around my system and a read of the PCMCIA howto.  My PCMCIA modem is recognised up to a point.  Cardinfo sees it occupying IRQ3 dev/ttysO and has the status "ready", I can eject and insert it (as sudo) but still cannot connect or uatodetect it in gnome network tools.  It is also not mentioned in DMESG pasted below or /var/log/messages is this due to the hotplug system????  I'm sure this problem is simple to resolve but embarrasingly I cannot work out the answer.  Sorry about the length of post.

dmesg output

cking if image is initramfs... it is
[4294672.014000] Freeing initrd memory: 4670k freed
[4294672.016000] ACPI: Looking for DSDT in initrd... not found!
[4294672.065000]  not found!
[4294672.153000] ENABLING IO-APIC IRQs
[4294672.153000] ..TIMER: vector=0x31 pin1=2 pin2=-1
[4294672.264000] NET: Registered protocol family 16
[4294672.264000] EISA bus registered
[4294672.264000] ACPI: bus type pci registered
[4294672.265000] PCI: PCI BIOS revision 2.10 entry at 0xf0322, last bus=3
[4294672.265000] PCI: Using MMCONFIG
[4294672.265000] mtrr: v2.0 (20020519)
[4294672.265000] ACPI: Subsystem revision 20050729
[4294672.294000] ACPI: Interpreter enabled
[4294672.294000] ACPI: Using IOAPIC for interrupt routing
[4294672.294000] ACPI: PCI Root Bridge [C002] (0000:00)
[4294672.294000] PCI: Probing PCI hardware (bus 00)
[4294672.294000] ACPI: Assume root bridge [\_SB_.C002] segment is 0
[4294672.294000] ACPI: Assume root bridge [\_SB_.C002] bus is 0
[4294672.303000] Boot video device is 0000:00:02.0
[4294672.303000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[4294672.304000] PCI: Transparent bridge - 0000:00:1e.0
[4294672.344000] ACPI: PCI Interrupt Routing Table [\_SB_.C002._PRT]
[4294672.345000] ACPI: PCI Interrupt Routing Table [\_SB_.C002.C068._PRT]
[4294672.346000] ACPI: Embedded Controller [C004] (gpe 16)
[4294672.364000] ACPI: Power Resource [C1C5] (on)
[4294672.368000] ACPI: PCI Interrupt Link [C0D8] (IRQs 10 *11)
[4294672.369000] ACPI: PCI Interrupt Link [C0D9] (IRQs *10 11)
[4294672.369000] ACPI: PCI Interrupt Link [C0DA] (IRQs *10 11)
[4294672.370000] ACPI: PCI Interrupt Link [C0DB] (IRQs *10 11)
[4294672.371000] ACPI: PCI Interrupt Link [C0EE] (IRQs *10 11)
[4294672.371000] ACPI: PCI Interrupt Link [C0EF] (IRQs 10 *11)
[4294672.372000] ACPI: PCI Interrupt Link [C0F0] (IRQs *10 11)
[4294672.372000] ACPI: PCI Interrupt Link [C0F1] (IRQs 10 11) *0, disabled.
[4294672.375000] ACPI: Power Resource [C244] (off)
[4294672.375000] ACPI: Power Resource [C245] (off)
[4294672.375000] ACPI: Power Resource [C246] (off)
[4294672.375000] ACPI: Power Resource [C247] (off)
[4294672.375000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294672.375000] pnp: PnP ACPI init
[4294672.381000] pnp: PnP ACPI: found 12 devices
[4294672.381000] PnPBIOS: Disabled by ACPI PNP
[4294672.381000] PCI: Using ACPI for IRQ routing
[4294672.381000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294672.437000] pnp: 00:09: ioport range 0x4d0-0x4d1 has been reserved
[4294672.437000] pnp: 00:09: ioport range 0x1000-0x107f could not be reserved
[4294672.437000] pnp: 00:09: ioport range 0x1100-0x113f has been reserved
[4294672.437000] pnp: 00:09: ioport range 0x1200-0x121f has been reserved
[4294672.437000] audit: initializing netlink socket (disabled)
[4294672.437000] audit(1139905953.435:0): initialized
[4294672.438000] VFS: Disk quotas dquot_6.5.1
[4294672.438000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294672.438000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294672.438000] devfs: boot_options: 0x0
[4294672.438000] Initializing Cryptographic API
[4294672.438000] isapnp: Scanning for PnP cards...
[4294672.790000] isapnp: No Plug & Play device found
[4294672.808000] PNP: PS/2 Controller [PNP0303:C1C2,PNP0f13:C1C3] at 0x60,0x64 irq 1,12
[4294672.810000] i8042.c: Detected active multiplexing controller, rev 1.1.
[4294672.811000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[4294672.811000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[4294672.811000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[4294672.811000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[4294672.811000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294672.811000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294672.815000] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 22 (level, low) -> IRQ 22
[4294672.815000] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[4294672.815000] io scheduler noop registered
[4294672.815000] io scheduler anticipatory registered
[4294672.815000] io scheduler deadline registered
[4294672.815000] io scheduler cfq registered
[4294672.815000] RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
[4294672.815000] EISA: Probing bus 0 at eisa.0
[4294672.815000] Cannot allocate resource for EISA slot 1
[4294672.815000] Cannot allocate resource for EISA slot 2
[4294672.816000] Cannot allocate resource for EISA slot 7
[4294672.816000] EISA: Detected 0 cards.
[4294672.816000] NET: Registered protocol family 2
[4294672.826000] IP: routing cache hash table of 2048 buckets, 16Kbytes
[4294672.826000] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[4294672.826000] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[4294672.826000] TCP: Hash tables configured (established 8192 bind 8192)
[4294672.826000] NET: Registered protocol family 8
[4294672.826000] NET: Registered protocol family 20
[4294672.826000] ACPI wakeup devices: 
[4294672.826000] C068 C0BB C0C2 C0C3 C0C4 C0C5 
[4294672.826000] ACPI: (supports S0 S3 S4 S4bios S5)
[4294672.826000] Freeing unused kernel memory: 224k freed
[4294672.860000] Capability LSM initialized
[4294672.871000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294672.872000] NET: Registered protocol family 1
[4294672.904000] usbcore: registered new driver usbfs
[4294672.904000] usbcore: registered new driver hub
[4294672.905000] USB Universal Host Controller Interface driver v2.2
[4294672.905000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[4294672.905000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294672.905000] uhci_hcd 0000:00:1d.0: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
[4294672.967000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294672.967000] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00002000
[4294672.967000] hub 1-0:1.0: USB hub found
[4294672.967000] hub 1-0:1.0: 2 ports detected
[4294672.970000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 17
[4294672.970000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294672.970000] uhci_hcd 0000:00:1d.1: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
[4294673.032000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294673.032000] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00002020
[4294673.032000] hub 2-0:1.0: USB hub found
[4294673.032000] hub 2-0:1.0: 2 ports detected
[4294673.035000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[4294673.035000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294673.035000] uhci_hcd 0000:00:1d.2: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
[4294673.097000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294673.097000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00002040
[4294673.097000] hub 3-0:1.0: USB hub found
[4294673.097000] hub 3-0:1.0: 2 ports detected
[4294673.100000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 19
[4294673.100000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[4294673.100000] uhci_hcd 0000:00:1d.3: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
[4294673.136000] usb 1-2: new low speed USB device using uhci_hcd and address 2
[4294673.162000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[4294673.162000] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00002060
[4294673.162000] hub 4-0:1.0: USB hub found
[4294673.162000] hub 4-0:1.0: 2 ports detected
[4294673.196000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[4294673.196000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294673.196000] ehci_hcd 0000:00:1d.7: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
[4294673.196000] ehci_hcd 0000:00:1d.7: debug port 1
[4294673.196000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[4294673.196000] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd0580000
[4294673.200000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[4294673.200000] ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294673.200000] hub 5-0:1.0: USB hub found
[4294673.200000] hub 5-0:1.0: 8 ports detected
[4294673.260000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294673.260000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294673.260000] ACPI: bus type ide registered
[4294673.292000] b44.c:v0.95 (Aug 3, 2004)
[4294673.292000] ACPI: PCI Interrupt 0000:02:0e.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294673.296000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:14:c2:e5:b9:43
[4294673.636000] usb 1-2: new low speed USB device using uhci_hcd and address 3
[4294675.314000] usbcore: registered new driver hiddev
[4294675.364000] input: USB HID v1.10 Mouse [1241:1111] on usb-0000:00:1d.0-2
[4294675.364000] usbcore: registered new driver usbhid
[4294675.364000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294675.397000] ICH6: IDE controller at PCI slot 0000:00:1f.1
[4294675.397000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[4294675.397000] ICH6: chipset revision 3
[4294675.397000] ICH6: not 100% native mode: will probe irqs later
[4294675.397000]     ide0: BM-DMA at 0x2580-0x2587, BIOS settings: hda:DMA, hdb:DMA
[4294675.397000] Probing IDE interface ide0...
[4294675.661000] hda: TOSHIBA MK4025GAS, ATA DISK drive
[4294676.069000] hdb: TSSTcorpCDW/DVD TS-L462C, ATAPI CD/DVD-ROM drive
[4294676.120000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294676.120000] Probing IDE interface ide1...
[4294676.633000] Probing IDE interface ide2...
[4294677.145000] Probing IDE interface ide3...
[4294677.657000] Probing IDE interface ide4...
[4294678.169000] Probing IDE interface ide5...
[4294678.684000] hda: max request size: 128KiB
[4294678.733000] hda: 78140160 sectors (40007 MB), CHS=65535/16/63, UDMA(100)
[4294678.733000] hda: cache flushes supported
[4294678.733000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
[4294678.783000] hdb: ATAPI 24X DVD-ROM CD-R/RW drive, 1536kB Cache
[4294678.783000] Uniform CD-ROM driver Revision: 3.20
[4294679.070000] ACPI: Fan [C248] (off)
[4294679.070000] ACPI: Fan [C249] (off)
[4294679.071000] ACPI: Fan [C24A] (off)
[4294679.071000] ACPI: Fan [C24B] (off)
[4294679.076000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[4294679.076000] ACPI: Processor [C000] (supports 8 throttling states)
[4294679.094000] ACPI: Thermal Zone [TZ1] (21 C)
[4294679.109000] ACPI: Thermal Zone [TZ2] (16 C)
[4294679.118000] ACPI: Thermal Zone [TZ3] (16 C)
[4294679.122000] ACPI: Thermal Zone [TZ4] (41 C)
[4294679.127000] vga16fb: initializing
[4294679.127000] vga16fb: mapped to 0xc00a0000
[4294679.268000] Console: switching to colour frame buffer device 80x30
[4294679.268000] fb0: VGA16 VGA frame buffer device
[4294679.442000] Attempting manual resume
[4294679.467000] swsusp: Suspend partition has wrong signature?
[4294679.510000] kjournald starting.  Commit interval 5 seconds
[4294679.510000] EXT3-fs: mounted filesystem with ordered data mode.
[4294680.894000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294683.921000] Adding 730916k swap on /dev/hda5.  Priority:-1 extents:1
[4294684.149000] EXT3 FS on hda1, internal journal
[4294690.802000] lp: driver loaded but no devices found
[4294690.817000] mice: PS/2 mouse device common for all mice
[4294690.848000] ieee1394: Initialized config rom entry `ip1394'
[4294690.851000] SCSI subsystem initialized
[4294690.853000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[4294691.497000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04793/0x300000
[4294691.497000] serio: Synaptics pass-through port at isa0060/serio4/input0
[4294691.499000] input: SynPS/2 Synaptics TouchPad on isa0060/serio4
[4294693.543000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294694.461000] cdrom: open failed.
[4294696.410000] Linux agpgart interface v0.101 (c) Dave Jones
[4294696.417000] agpgart: Detected an Intel 915GM Chipset.
[4294696.418000] agpgart: Detected 7932K stolen memory.
[4294696.452000] agpgart: AGP aperture is 256M @ 0xc0000000
[4294696.733000] hw_random: RNG not detected
[4294696.905000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 21 (level, low) -> IRQ 21
[4294696.905000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[4294697.715000] intel8x0_measure_ac97_clock: measured 49450 usecs
[4294697.715000] intel8x0: clocking to 48000
[4294698.329000] Linux Kernel Card Services
[4294698.329000]   options:  [pci] [cardbus] [pm]
[4294698.341000] ACPI: PCI Interrupt 0000:02:06.0[A] -> GSI 18 (level, low) -> IRQ 18
[4294698.341000] Yenta: CardBus bridge found at 0000:02:06.0 [103c:099c]
[4294698.461000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 18
[4294698.461000] Socket status: 30000410
[4294698.571000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[4294698.571000] ACPI: PCI Interrupt 0000:02:06.2[C] -> GSI 22 (level, low) -> IRQ 22
[4294698.625000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[d0003000-d00037ff]  Max Packet=[2048]
[4294699.885000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[718b500029050fa6]
[4294700.152000] input: PC Speaker
[4294700.215000] Real Time Clock Driver v1.12
[4294700.873000] ts: Compaq touchscreen protocol output
[4294703.589000] ACPI: AC Adapter [C172] (off-line)
[4294703.659000] ACPI: Battery Slot [C174] (battery present)
[4294703.659000] ACPI: Battery Slot [C173] (battery absent)
[4294703.679000] ACPI: Power Button (FF) [PWRF]
[4294703.680000] ACPI: Sleep Button (CM) [C1E8]
[4294703.680000] ACPI: Lid Switch [C1E9]
[4294703.766000] Using specific hotkey driver
[4294703.797000] ibm_acpi: ec object not found
[4294703.896000] ACPI: Video Device [C055] (multi-head: yes  rom: no  post: no)
[4294712.043000] [drm] Initialized drm 1.0.0 20040925
[4294712.047000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294712.052000] [drm] Initialized i915 1.2.0 20040405 on minor 0: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller
[4294712.052000] mtrr: base(0xc0020000) is not aligned on a size(0x300000) boundary
[4294717.174000] apm: BIOS not found.
[4294717.860000] cs: IO port probe 0x100-0x4ff: clean.
[4294717.863000] cs: IO port probe 0xc00-0xcff: excluding 0xcf8-0xcff
[4294717.864000] cs: IO port probe 0xa00-0xaff: clean.
[4294717.870000] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[4294718.321000] Bluetooth: Core ver 2.7
[4294718.321000] NET: Registered protocol family 31
[4294718.321000] Bluetooth: HCI device and connection manager initialized
[4294718.321000] Bluetooth: HCI socket layer initialized
[4294718.336000] Bluetooth: L2CAP ver 2.7
[4294718.336000] Bluetooth: L2CAP socket layer initialized
[4294718.397000] Bluetooth: RFCOMM ver 1.5
[4294718.397000] Bluetooth: RFCOMM socket layer initialized
[4294718.397000] Bluetooth: RFCOMM TTY layer initialized
[4294719.672000] hdb: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[4294719.672000] hdb: drive_cmd: error=0x04 { AbortedCommand }
[4294719.672000] ide: failed opcode was: 0xef
[4294735.684000] hdb: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[4294735.684000] hdb: drive_cmd: error=0x04 { AbortedCommand }
[4294735.684000] ide: failed opcode was: 0xef
[4294744.401000] NET: Registered protocol family 10
[4294744.401000] Disabled Privacy Extensions on device c02eb280(lo)
[4294744.401000] IPv6 over IPv4 tunneling driver

---

### Post by Greg2 on 2006-02-14
[QUOTE=hollowhead]I've had a poke around my system and a read of the PCMCIA howto.  My PCMCIA modem is recognised up to a point.  Cardinfo sees it occupying IRQ3 dev/ttysO and has the status "ready", I can eject and insert it (as sudo) but still cannot connect or uatodetect it in gnome network tools.  It is also not mentioned in DMESG pasted below or /var/log/messages is this due to the hotplug system????  I'm sure this problem is simple to resolve but embarrasingly I cannot work out the answer.  Sorry about the length of post.

dmesg output

-snip-

[4294672.381000] PCI: Using ACPI for IRQ routing
[4294672.381000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report

 -snip- 
[/QUOTE]
It would appear that the dmesg output is advising you to try ‘pci=routeirq’ as a kernel boot parameter in your grub. So I would suggest that you edit your menu.1st file in grub with pci=routeirq and reboot to see if that helps.

If you still have problems you may want to try some other boot parameters, such as acpi=noirq and irqpoll with your system.

As a side note, I would like to add that this is the 3rd thread you have started with this problem:
[http://ubuntuforums.org/showthread.php?t=129181](http://ubuntuforums.org/showthread.php?t=129181)
and
[http://ubuntuforums.org/showthread.php?t=129184](http://ubuntuforums.org/showthread.php?t=129184)
It was very nice of you to apologize for it the first time, but now you have done it again. I know that it is very frustrating when your system does not work properly... but it is even more frustrating for the next person with the same problem to find a solution when the information is so fragmented because of multiple posting. :)

---

### Post by hollowhead on 2006-02-14
Thanks Greg having read the howto I cannot see it is anything but an irq problem, if your answer is correct then its a dead simple thing to do.  I'm sorry about the multiple posts.  I usually post to the desktop forum for that seems most appropiate to my problems.  I did this then scrolled down the page and saw the laptop forum.  The second post was merely to update those on the laptop forum -I guess I should have replied to my original laptop post to do this rather than a new post -would this be correct?  Finally I would never have picked on the dmesg output as you did I'm too inexperienced.

---

### Post by hollowhead on 2006-02-15
Greg thanks for suggestion but it didn't work.  I had a look at config.opts in the /etc/pcmcia dir but its a bit daunting.  Cardinfo says the card is irq3, the config.opts file has the line #exclude irq3 (single #) are the lines with a double hash comments or is the above also commented out.  If so there would be discrepancy surely?

---

### Post by Greg2 on 2006-02-15
[QUOTE=hollowhead]the config.opts file has the line #exclude irq3 (single #) are the lines with a double hash comments or is the above also commented out.  If so there would be discrepancy surely?[/QUOTE]
If it is ‘#exclude irq 3’ it is not a problem... you are including the resource irq 3.

So the problem is with your modem, or rather lack of modem driver. I can’t find anything about it ever being used successfully with Linux. Here’s a rather old PCMCIA supported device list:
[http://pcmcia-cs.sourceforge.net/ftp/SUPPORTED.CARDS](http://pcmcia-cs.sourceforge.net/ftp/SUPPORTED.CARDS) 
You said in your other post that the modem was supported in RH5.2. Maybe you can find that info, or a link to it and post it here? Then maybe someone else can offer some advice.

---

### Post by hollowhead on 2006-02-22
Greg thanks for your reply.  The delay in reply was due to being on holiday and gathering more info.  I still have my ancient rh5.2 box I plugged the modem card in and connected fine (biggest surprise my ISP had not changed their number in so many years).  The old machine also beeps once when the card is in and no beep when it boots w/o the card.  So I know it was supported.  According to the shutdown messages and other files on this machine the serial_cs module is being used.  This module seems to cover masses of modems. I have included the output of various files below.  I also tried pci=assign-busses in menu.1st, no joy.  This must a simple tweak in a file somewhere.  Ta.  Hollowhead

lsmod w/o card present in nx6110

neil@hollow:~$ lsmod 
Module                  Size  Used by
nls_utf8                2176  1
nls_cp437               5888  1
vfat                   12288  1
fat                    46492  1 vfat
sd_mod                 17424  1
usb_storage            64704  1
ipv6                  217408  6
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
pcmcia                 24584  2
i915                   17920  1
drm                    58004  2 i915
video                  16004  0
sony_acpi               5516  0
pcc_acpi               11392  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
joydev                  9280  0
tsdev                   7616  0
rtc                    11832  0
pcspkr                  3652  0
ohci1394               30644  0
yenta_socket           20872  1
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
tpm_nsc                 6528  0
tpm                     9504  1 tpm_nsc
snd_intel8x0           30016  1
snd_ac97_codec         71804  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
intel_agp              21276  1
agpgart                32328  3 drm,intel_agp
dm_mod                 50364  1
evdev                   9088  1
sr_mod                 15652  0
sbp2                   21256  0
scsi_mod              124872  4 sd_mod,usb_storage,sr_mod,sbp2
ieee1394               90936  2 ohci1394,sbp2
psmouse                25988  0
mousedev               10912  1
parport_pc             31812  0
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
vga16fb                12232  1
vgastate                8320  1 vga16fb
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
ide_cd                 36996  0
cdrom                  33952  2 sr_mod,ide_cd
ide_disk               16128  3
ide_generic             1664  0
usbhid                 30560  0
b44                    19204  0
mii                     5248  1 b44
piix                    9476  1
ide_core              125268  5 usb_storage,ide_cd,ide_disk,ide_generic,piix
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104188  5 usb_storage,usbhid,ehci_hcd,uhci_hcd
unix                   24624  744
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon
vesafb                  8088  0
cfbcopyarea             4480  2 vga16fb,vesafb
cfbimgblt               2944  2 vga16fb,vesafb
cfbfillrect             3840  2 vga16fb,vesafb
softcursor              2432  2 vga16fb,vesafb
capability              5000  0
commoncap               6784  1 capability
lspci output

0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corp. Mobile Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corp. Mobile Graphics Controller (rev 03)0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:01:04.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02)
0000:01:06.0 CardBus bridge: Texas Instruments: Unknown device 8031
0000:01:06.2 FireWire (IEEE 1394): Texas Instruments: Unknown device 8032
0000:01:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

neil@hollow:~$ cardctl ident
Socket 0:
  product info: "RIPICAA", "RC144ACL", "003", "A"
  manfid: 0x0013, 0x0000
  function: 2 (serial)

neil@hollow:~$ cardctl config
Socket 0:
  Vcc 5.0V  Vpp1 0.0V  Vpp2 0.0V
  interface type is "memory and I/O"
  irq 3 [exclusive] [level]
  speaker output is enabled
  function 0:
    config base 0x0200
      option 0x60 status 0x08 pin 0x00 ext 0x00
    io 0x03f8-0x03ff [8bit]

---

### Post by Greg2 on 2006-02-22
[QUOTE=hollowhead] According to the shutdown messages and other files on this machine the serial_cs module is being used.  This module seems to cover masses of modems. [/QUOTE]
OK... you can give that a try with:```
sudo insmod /lib/modules/2.6.12-9-386/kernel/drivers/serial/serial_cs
```if you are using the stock kernel.

If that doesn't work, you can try to:```
sudo rmmod pcmcia
```then try to insmod the serial module with the command above.

Let us know if that works.

---

### Post by hollowhead on 2006-02-27
Tried that Greg didn't work it says the module is already loaded as part of PCMCIA module.  This is true, if l do lsmod with the card in you it tells you the two are loaded together they are listed on the same line.  Rmmod comes up with a similar error.  Unfortunately I am unable to post this output due to my ubstick having conked out and this is the only way I can get stuff to this machine at work since I left my USB floppy at work.  Ta.  Hollowhead

---

### Post by Greg2 on 2006-02-27
[QUOTE=hollowhead]Tried that Greg didn't work it says the module is already loaded as part of PCMCIA module.[/QUOTE]
I thought it would be... but now we’re sure. I’m sorry, but I’m out of ideas. Maybe someone else here will have some input on your problem? :???:

---

### Post by hollowhead on 2006-02-28
Thanks Greg,

It seems to me that the card is recognised, its not a permission thing its either something to do with the hotplug system or a an irq problem.  I've posted to one of Mr Hinds newsgroups but have yet to have a responce yet.

---

