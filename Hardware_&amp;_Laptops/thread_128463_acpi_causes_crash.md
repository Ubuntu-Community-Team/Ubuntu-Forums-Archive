---
title: "acpi causes crash"
date: 2006-02-11
forum: Hardware &amp; Laptops
---

### Post by waldick on 2006-02-11
hi,
i have an HP zx5078ci, p4, 512meg ram,...anyway, with acpi enabled the machine crashes when the acpi tries to change the cpu freq...machine works fine with acpi off, but then the battery life is not very good...and of course no battery meter.

i can't seem to figure this out so any help is appreciated..

j

---

### Post by waldick on 2006-02-12
anyone ?

---

### Post by chele on 2006-02-12
Do you have a warranty on the computer?

---

### Post by chele on 2006-02-12
If you enter your machine in the [GNU/Linux device driver check page]("http://kmuto.jp/debian/hcl/") does it show up as fully supported?

---

### Post by K.Mandla on 2006-02-13
If you're willing to live without acpi, you can add

```
acpi=off
```

to your kernel boot line and it should turn it off at each startup. I've done this with old laptops and it has strange (but good) side effects too.

---

### Post by Greg2 on 2006-02-13
[QUOTE=waldick]with acpi enabled the machine crashes when the acpi tries to change the cpu freq...machine works fine with acpi off, but then the battery life is not very good...and of course no battery meter.[/QUOTE]
There are many kernel boot parameters available. In your case you may want to ‘try’ editing the memu.1st file in grub with:```
acpi=strict acpi=noirq irqpoll routeirq
```
Please let us know it that works for your system?

---

### Post by waldick on 2006-02-14
ok, i'm back now...

i had acpi=off in the grub menu.lst...

i added the suggested :

acpi=strict acpi=noirq irqpoll routeirq

so far so good, i'll report back after i've run the machine a while....

thank you...

j

---

### Post by waldick on 2006-02-14
well, it doesn't crash, but my messages log tell me this:
```
Feb 14 22:30:07 localhost kernel: [4294788.881000] acpi-cpufreq: Transition failed
Feb 14 22:30:13 localhost kernel: [4294795.071000] acpi-cpufreq: Transition failed
Feb 14 22:30:28 localhost kernel: [4294809.972000] acpi-cpufreq: Transition failed
Feb 14 22:31:26 localhost kernel: [4294867.445000] acpi-cpufreq: Transition failed
Feb 14 22:31:49 localhost kernel: [4294890.656000] acpi-cpufreq: Transition failed
Feb 14 22:34:55 localhost kernel: [4295076.703000] acpi-cpufreq: Transition failed
Feb 14 22:35:27 localhost kernel: [4295108.828000] acpi-cpufreq: Transition failed
Feb 14 22:37:43 localhost kernel: [4295244.931000] acpi-cpufreq: Transition failed
Feb 14 22:37:54 localhost kernel: [4295255.432000] acpi-cpufreq: Transition failed
Feb 14 22:41:39 localhost kernel: [4295480.872000] acpi-cpufreq: Transition failed
Feb 14 22:45:45 localhost kernel: [4295726.834000] acpi-cpufreq: Transition failed
```

so i still have a porblem, and here is the first part of my messages log:
```
Feb 14 21:50:58 localhost syslogd 1.4.1#17ubuntu3: restart.
Feb 14 22:10:58 localhost -- MARK --
Feb 14 22:17:04 localhost gconfd (juergen-7581): Exiting
Feb 14 22:17:04 localhost kernel: [ 2029.379235] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
Feb 14 22:17:04 localhost kernel: [ 2029.379254] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
Feb 14 22:17:04 localhost kernel: [ 2029.379268] agpgart: Putting AGP V3 device at 0000:01:05.0 into 4x mode
Feb 14 22:17:04 localhost kernel: [ 2029.384357] [drm] Loading R200 Microcode
Feb 14 22:17:21 localhost ivman: Ivman started in system mode
Feb 14 22:17:28 localhost gconfd (juergen-9256): starting (version 2.12.0), pid 9256 user 'juergen'
Feb 14 22:17:29 localhost gconfd (juergen-9259): starting (version 2.12.0), pid 9259 user 'juergen'
Feb 14 22:17:29 localhost gconfd (juergen-9259): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb 14 22:17:29 localhost gconfd (juergen-9259): Resolved address "xml:readonly:/usr/share/gconf/local.mandatory" to a read-only configuration source at position 1
Feb 14 22:17:29 localhost gconfd (juergen-9259): Resolved address "xml:readwrite:/home/juergen/.gconf" to a writable configuration source at position 2
Feb 14 22:17:29 localhost gconfd (juergen-9259): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
Feb 14 22:17:29 localhost gconfd (juergen-9259): Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4
Feb 14 22:17:29 localhost gconfd (juergen-9259): Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Feb 14 22:17:29 localhost gconfd (juergen-9259): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
Feb 14 22:17:29 localhost gconfd (juergen-9259): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
Feb 14 22:17:29 localhost gconfd (juergen-9256): Failed to get lock for daemon, exiting: Failed to lock '/tmp/gconfd-juergen/lock/ior': probably another process has the lock, or your operating system has NFS file locking misconfigured (Resource temporarily unavailable)
Feb 14 22:27:24 localhost shutdown[9813]: shutting down for system reboot
Feb 14 22:27:26 localhost gconfd (juergen-9259): Received signal 15, shutting down cleanly
Feb 14 22:27:26 localhost gconfd (juergen-9259): Exiting
Feb 14 22:27:35 localhost kernel: [ 2658.373133] apm: BIOS not found.
Feb 14 22:27:44 localhost kernel: Kernel logging (proc) stopped.
Feb 14 22:27:44 localhost kernel: Kernel log daemon terminating.
Feb 14 22:27:44 localhost exiting on signal 15
Feb 14 22:29:09 localhost syslogd 1.4.1#17ubuntu3: restart.
Feb 14 22:29:09 localhost kernel: Inspecting /boot/System.map-2.6.12-10-386
Feb 14 22:29:09 localhost kernel: Loaded 29010 symbols from /boot/System.map-2.6.12-10-386.
Feb 14 22:29:09 localhost kernel: Symbols match kernel version 2.6.12.
Feb 14 22:29:09 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Feb 14 22:29:09 localhost kernel: 94671.289000] Memory: 510340k/523712k available (1416k kernel code, 12740k reserved, 762k data, 224k init, 0k highmem)
Feb 14 22:29:09 localhost kernel: [4294671.289000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Feb 14 22:29:09 localhost kernel: [4294671.312000] Security Framework v1.0.0 initialized
Feb 14 22:29:09 localhost kernel: [4294671.312000] SELinux:  Disabled at boot.
Feb 14 22:29:09 localhost kernel: [4294671.312000] Mount-cache hash table entries: 512
Feb 14 22:29:09 localhost kernel: [4294671.312000] CPU: Trace cache: 12K uops, L1 D cache: 8K
Feb 14 22:29:09 localhost kernel: [4294671.312000] CPU: L2 cache: 512K
Feb 14 22:29:09 localhost kernel: [4294671.312000] CPU: Intel Mobile Intel(R) Pentium(R) 4     CPU 3.06GHz stepping 09
Feb 14 22:29:09 localhost kernel: [4294671.312000] Enabling fast FPU save and restore... done.
Feb 14 22:29:09 localhost kernel: [4294671.312000] Enabling unmasked SIMD FPU exception support... done.
Feb 14 22:29:09 localhost kernel: [4294671.312000] Checking 'hlt' instruction... OK.
Feb 14 22:29:09 localhost kernel: [4294671.316000] Checking for popad bug... OK.
Feb 14 22:29:09 localhost kernel: [4294671.316000] checking if image is initramfs... it is
Feb 14 22:29:09 localhost kernel: [4294671.689000] Freeing initrd memory: 5175k freed
Feb 14 22:29:09 localhost kernel: [4294671.689000] ACPI: Looking for DSDT in initrd... not found!
Feb 14 22:29:09 localhost kernel: [4294671.728000]  not found!
Feb 14 22:29:09 localhost kernel: [4294671.733000] ACPI: setting ELCR to 0e20 (from 0c20)
Feb 14 22:29:09 localhost kernel: [4294672.562000] ENABLING IO-APIC IRQs
Feb 14 22:29:09 localhost kernel: [4294672.562000] ..TIMER: vector=0x31 pin1=2 pin2=0
Feb 14 22:29:09 localhost kernel: [4294672.674000] NET: Registered protocol family 16
Feb 14 22:29:09 localhost kernel: [4294672.674000] EISA bus registered
Feb 14 22:29:09 localhost kernel: [4294672.674000] ACPI: bus type pci registered
Feb 14 22:29:09 localhost kernel: [4294672.674000] PCI: PCI BIOS revision 2.10 entry at 0xfd968, last bus=2
Feb 14 22:29:09 localhost kernel: [4294672.674000] PCI: Using configuration type 1
Feb 14 22:29:09 localhost kernel: [4294672.674000] mtrr: v2.0 (20020519)
Feb 14 22:29:09 localhost kernel: [4294672.674000] ACPI: Subsystem revision 20050729
Feb 14 22:29:09 localhost kernel: [4294672.700000] ACPI: Interpreter enabled
Feb 14 22:29:09 localhost kernel: [4294672.700000] ACPI: Using PIC for interrupt routing
Feb 14 22:29:09 localhost kernel: [4294672.700000] ACPI: PCI Root Bridge [PCI0] (0000:00)
Feb 14 22:29:09 localhost kernel: [4294672.700000] PCI: Probing PCI hardware (bus 00)
Feb 14 22:29:09 localhost kernel: [4294672.700000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
Feb 14 22:29:09 localhost kernel: [4294672.700000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
Feb 14 22:29:09 localhost kernel: [4294672.725000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:14.1
Feb 14 22:29:09 localhost kernel: [4294672.725000] PCI: Transparent bridge - 0000:00:14.4
Feb 14 22:29:09 localhost kernel: [4294672.736000] burst-mode-ec-10-Aug
Feb 14 22:29:09 localhost kernel: [4294672.736000] ACPI: Embedded Controller [EC0] (gpe 6)
Feb 14 22:29:09 localhost kernel: [4294672.781000] Linux Plug and Play Support v0.97 (c) Adam Belay
Feb 14 22:29:09 localhost kernel: [4294672.781000] pnp: PnP ACPI init
Feb 14 22:29:09 localhost kernel: [4294672.806000] pnp: PnP ACPI: found 9 devices
Feb 14 22:29:09 localhost kernel: [4294672.806000] PnPBIOS: Disabled by ACPI PNP
Feb 14 22:29:09 localhost kernel: [4294672.806000] PCI: Probing PCI hardware
Feb 14 22:29:09 localhost kernel: [4294672.806000] PCI: Using IRQ router default [1002/434c] at 0000:00:14.3
Feb 14 22:29:09 localhost kernel: [4294672.806000] PCI->APIC IRQ transform: 0000:00:13.0[A] -> IRQ 19
Feb 14 22:29:09 localhost kernel: [4294672.806000] PCI->APIC IRQ transform: 0000:00:13.1[A] -> IRQ 19
Feb 14 22:29:09 localhost kernel: [4294672.806000] PCI->APIC IRQ transform: 0000:00:14.1[A] -> IRQ 17
Feb 14 22:29:09 localhost kernel: [4294672.806000] PCI->APIC IRQ transform: 0000:00:14.5[B] -> IRQ 17
Feb 14 22:29:09 localhost kernel: [4294672.806000] PCI->APIC IRQ transform: 0000:00:14.6[B] -> IRQ 17
Feb 14 22:29:09 localhost kernel: [4294672.806000] PCI->APIC IRQ transform: 0000:01:05.0[A] -> IRQ 16
Feb 14 22:29:09 localhost kernel: [4294672.806000] PCI->APIC IRQ transform: 0000:02:00.0[A] -> IRQ 16
Feb 14 22:29:09 localhost kernel: [4294672.806000] PCI->APIC IRQ transform: 0000:02:02.0[A] -> IRQ 18
Feb 14 22:29:09 localhost kernel: [4294672.806000] PCI->APIC IRQ transform: 0000:02:03.0[A] -> IRQ 19
Feb 14 22:29:09 localhost kernel: [4294672.806000] PCI: using PPB 0000:00:14.4[A] to get irq 17
Feb 14 22:29:09 localhost kernel: [4294672.806000] PCI->APIC IRQ transform: 0000:02:04.0[A] -> IRQ 17
Feb 14 22:29:09 localhost kernel: [4294672.806000] PCI: using PPB 0000:00:14.4[B] to get irq 17
Feb 14 22:29:09 localhost kernel: [4294672.806000] PCI->APIC IRQ transform: 0000:02:04.1[B] -> IRQ 17
Feb 14 22:29:09 localhost kernel: [4294672.806000] PCI->APIC IRQ transform: 0000:02:07.0[A] -> IRQ 16
Feb 14 22:29:09 localhost kernel: [4294672.806000] PCI->APIC IRQ transform: 0000:02:07.1[B] -> IRQ 18
Feb 14 22:29:09 localhost kernel: [4294672.806000] PCI->APIC IRQ transform: 0000:02:07.2[C] -> IRQ 19
Feb 14 22:29:09 localhost kernel: [4294672.812000] pnp: 00:06: ioport range 0x200-0x20f has been reserved
Feb 14 22:29:09 localhost kernel: [4294672.812000] pnp: 00:06: ioport range 0xc14-0xc14 has been reserved
Feb 14 22:29:09 localhost kernel: [4294672.812000] pnp: 00:06: ioport range 0xc50-0xc52 has been reserved
Feb 14 22:29:09 localhost kernel: [4294672.812000] pnp: 00:06: ioport range 0xc6c-0xc6c has been reserved
Feb 14 22:29:09 localhost kernel: [4294672.812000] audit: initializing netlink socket (disabled)
Feb 14 22:29:09 localhost kernel: [4294672.812000] audit: initialized
Feb 14 22:29:09 localhost kernel: [4294672.812000] VFS: Disk quotas dquot_6.5.1
Feb 14 22:29:09 localhost kernel: [4294672.812000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Feb 14 22:29:09 localhost kernel: [4294672.812000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
Feb 14 22:29:09 localhost kernel: [4294672.812000] devfs: boot_options: 0x0
Feb 14 22:29:09 localhost kernel: [4294672.812000] Initializing Cryptographic API
Feb 14 22:29:09 localhost kernel: [4294672.812000] isapnp: Scanning for PnP cards...
Feb 14 22:29:09 localhost kernel: [4294673.166000] isapnp: No Plug & Play device found
Feb 14 22:29:09 localhost kernel: [4294673.180000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
Feb 14 22:29:09 localhost kernel: [4294673.186000] i8042.c: Detected active multiplexing controller, rev 1.1.
Feb 14 22:29:09 localhost kernel: [4294673.195000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Feb 14 22:29:09 localhost kernel: [4294673.196000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Feb 14 22:29:09 localhost kernel: [4294673.197000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Feb 14 22:29:09 localhost kernel: [4294673.197000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Feb 14 22:29:09 localhost kernel: [4294673.198000] serio: i8042 KBD port at 0x60,0x64 irq 1
Feb 14 22:29:09 localhost kernel: [4294673.198000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
Feb 14 22:29:09 localhost kernel: [4294673.200000] io scheduler noop registered
Feb 14 22:29:09 localhost kernel: [4294673.200000] io scheduler anticipatory registered
Feb 14 22:29:09 localhost kernel: [4294673.200000] io scheduler deadline registered
Feb 14 22:29:09 localhost kernel: [4294673.200000] io scheduler cfq registered
Feb 14 22:29:09 localhost kernel: [4294673.201000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Feb 14 22:29:09 localhost kernel: [4294673.204000] EISA: Probing bus 0 at eisa.0
Feb 14 22:29:09 localhost kernel: [4294673.204000] Cannot allocate resource for EISA slot 1
Feb 14 22:29:09 localhost kernel: [4294673.204000] Cannot allocate resource for EISA slot 8
Feb 14 22:29:09 localhost kernel: [4294673.204000] EISA: Detected 0 cards.
Feb 14 22:29:09 localhost kernel: [4294673.204000] NET: Registered protocol family 2
Feb 14 22:29:09 localhost kernel: [4294673.216000] IP: routing cache hash table of 4096 buckets, 32Kbytes
Feb 14 22:29:09 localhost kernel: [4294673.216000] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
Feb 14 22:29:09 localhost kernel: [4294673.216000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
Feb 14 22:29:09 localhost kernel: [4294673.216000] TCP: Hash tables configured (established 32768 bind 32768)
Feb 14 22:29:09 localhost kernel: [4294673.216000] NET: Registered protocol family 8
Feb 14 22:29:09 localhost kernel: [4294673.216000] NET: Registered protocol family 20
Feb 14 22:29:09 localhost kernel: [4294673.216000] ACPI wakeup devices: 
Feb 14 22:29:09 localhost kernel: [4294673.216000] MODM ELAN USB0 USB1 USB2 
Feb 14 22:29:09 localhost kernel: [4294673.216000] ACPI: (supports S0 S3 S4 S5)
Feb 14 22:29:09 localhost kernel: [4294673.217000] Freeing unused kernel memory: 224k freed
Feb 14 22:29:09 localhost kernel: [4294673.232000] vga16fb: mapped to 0xc00a0000
Feb 14 22:29:09 localhost kernel: [4294673.347000] Console: switching to colour frame buffer device 80x30
Feb 14 22:29:09 localhost kernel: [4294673.347000] fb0: VGA16 VGA frame buffer device
Feb 14 22:29:09 localhost kernel: [4294673.363000] input: AT Translated Set 2 keyboard on isa0060/serio0
Feb 14 22:29:09 localhost kernel: [4294674.506000] Capability LSM initialized
Feb 14 22:29:09 localhost kernel: [4294674.517000] NET: Registered protocol family 1
Feb 14 22:29:09 localhost kernel: [4294674.528000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Feb 14 22:29:09 localhost kernel: [4294674.528000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Feb 14 22:29:09 localhost kernel: [4294674.528000] ACPI: bus type ide registered
Feb 14 22:29:09 localhost kernel: [4294674.537000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
Feb 14 22:29:09 localhost kernel: [4294674.537000] ATIIXP: chipset revision 0
Feb 14 22:29:09 localhost kernel: [4294674.537000] ATIIXP: not 100%% native mode: will probe irqs later
Feb 14 22:29:09 localhost kernel: [4294674.537000]     ide0: BM-DMA at 0x8060-0x8067, BIOS settings: hda:DMA, hdb:pio
Feb 14 22:29:09 localhost kernel: [4294674.537000]     ide1: BM-DMA at 0x8068-0x806f, BIOS settings: hdc:DMA, hdd:pio
Feb 14 22:29:09 localhost kernel: [4294674.801000] hda: IC25N060ATMR04-0, ATA DISK drive
Feb 14 22:29:09 localhost kernel: [4294675.413000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Feb 14 22:29:09 localhost kernel: [4294676.085000] hdc: HL-DT-ST DVD+RW GCA-4040N, ATAPI CD/DVD-ROM drive
Feb 14 22:29:09 localhost kernel: [4294676.391000] ide1 at 0x170-0x177,0x376 on irq 15
Feb 14 22:29:09 localhost kernel: [4294678.446000] hda: max request size: 1024KiB
Feb 14 22:29:09 localhost kernel: [4294678.467000] hda: 117210240 sectors (60011 MB) w/7884KiB Cache, CHS=16383/255/63, UDMA(100)
Feb 14 22:29:09 localhost kernel: [4294678.467000] hda: cache flushes supported
Feb 14 22:29:09 localhost kernel: [4294678.467000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 < p5 >
Feb 14 22:29:09 localhost kernel: [4294678.530000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache
Feb 14 22:29:09 localhost kernel: [4294678.530000] Uniform CD-ROM driver Revision: 3.20
Feb 14 22:29:09 localhost kernel: [4294678.795000] Attempting manual resume
Feb 14 22:29:09 localhost kernel: [4294678.821000] swsusp: Suspend partition has wrong signature?
Feb 14 22:29:09 localhost kernel: [4294678.862000] usbcore: registered new driver usbfs
Feb 14 22:29:09 localhost kernel: [4294678.862000] usbcore: registered new driver hub
Feb 14 22:29:09 localhost kernel: [4294678.862000] ohci_hcd 0000:00:13.0: ATI Technologies Inc OHCI USB Controller #1
Feb 14 22:29:09 localhost kernel: [4294678.863000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
Feb 14 22:29:09 localhost kernel: [4294678.863000] ohci_hcd 0000:00:13.0: irq 19, io mem 0xe8001000
Feb 14 22:29:09 localhost kernel: [4294678.868000] hub 1-0:1.0: USB hub found
Feb 14 22:29:09 localhost kernel: [4294678.868000] hub 1-0:1.0: 3 ports detected
Feb 14 22:29:09 localhost kernel: [4294678.873000] ohci_hcd 0000:00:13.1: ATI Technologies Inc OHCI USB Controller #2
Feb 14 22:29:09 localhost kernel: [4294678.873000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
Feb 14 22:29:09 localhost kernel: [4294678.873000] ohci_hcd 0000:00:13.1: irq 19, io mem 0xe8002000
Feb 14 22:29:09 localhost kernel: [4294678.878000] hub 2-0:1.0: USB hub found
Feb 14 22:29:09 localhost kernel: [4294678.878000] hub 2-0:1.0: 3 ports detected
Feb 14 22:29:09 localhost kernel: [4294678.883000] ohci_hcd 0000:02:07.0: NEC Corporation USB
Feb 14 22:29:09 localhost kernel: [4294678.883000] ohci_hcd 0000:02:07.0: new USB bus registered, assigned bus number 3
Feb 14 22:29:09 localhost kernel: [4294678.883000] ohci_hcd 0000:02:07.0: irq 16, io mem 0xe8206000
Feb 14 22:29:09 localhost kernel: [4294678.914000] hub 3-0:1.0: USB hub found
Feb 14 22:29:09 localhost kernel: [4294678.914000] hub 3-0:1.0: 3 ports detected
Feb 14 22:29:09 localhost kernel: [4294678.945000] ohci_hcd 0000:02:07.1: NEC Corporation USB (#2)
Feb 14 22:29:09 localhost kernel: [4294678.945000] ohci_hcd 0000:02:07.1: new USB bus registered, assigned bus number 4
Feb 14 22:29:09 localhost kernel: [4294678.945000] ohci_hcd 0000:02:07.1: irq 18, io mem 0xe8207000
Feb 14 22:29:09 localhost kernel: [4294678.976000] hub 4-0:1.0: USB hub found
Feb 14 22:29:09 localhost kernel: [4294678.976000] hub 4-0:1.0: 2 ports detected
Feb 14 22:29:09 localhost kernel: [4294679.064000] usb 3-1: new low speed USB device using ohci_hcd and address 2
Feb 14 22:29:09 localhost kernel: [4294679.074000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
Feb 14 22:29:09 localhost kernel: [4294679.074000] 8139cp: pci dev 0000:02:03.0 (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
Feb 14 22:29:09 localhost kernel: [4294679.074000] 8139cp: Try the "8139too" driver instead.
Feb 14 22:29:09 localhost kernel: [4294679.075000] 8139too Fast Ethernet driver 0.9.27
Feb 14 22:29:09 localhost kernel: [4294679.076000] eth0: RealTek RTL8139 at 0xa000, 00:02:3f:6b:77:c5, IRQ 19
Feb 14 22:29:09 localhost kernel: [4294679.113000] ehci_hcd 0000:02:07.2: NEC Corporation USB 2.0
Feb 14 22:29:09 localhost kernel: [4294679.134000] ehci_hcd 0000:02:07.2: new USB bus registered, assigned bus number 5
Feb 14 22:29:09 localhost kernel: [4294679.134000] ehci_hcd 0000:02:07.2: irq 19, io mem 0xe8208c00
Feb 14 22:29:09 localhost kernel: [4294679.134000] ehci_hcd 0000:02:07.2: park 0
Feb 14 22:29:09 localhost kernel: [4294679.134000] ehci_hcd 0000:02:07.2: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
Feb 14 22:29:09 localhost kernel: [4294679.134000] hub 5-0:1.0: USB hub found
Feb 14 22:29:09 localhost kernel: [4294679.134000] hub 5-0:1.0: 5 ports detected
Feb 14 22:29:09 localhost kernel: [4294679.926000] usb 3-1: new low speed USB device using ohci_hcd and address 4
Feb 14 22:29:09 localhost kernel: [4294681.182000] usbcore: registered new driver hiddev
Feb 14 22:29:09 localhost kernel: [4294681.193000] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:02:07.0-1
Feb 14 22:29:09 localhost kernel: [4294681.193000] usbcore: registered new driver usbhid
Feb 14 22:29:09 localhost kernel: [4294681.193000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
Feb 14 22:29:09 localhost kernel: [4294681.618000] ACPI: CPU0 (power states: C1[C1] C2[C2])
Feb 14 22:29:09 localhost kernel: [4294681.625000] ACPI: Thermal Zone [THRM] (49 C)
Feb 14 22:29:09 localhost kernel: [4294681.916000] Attempting manual resume
Feb 14 22:29:09 localhost kernel: [4294681.941000] swsusp: Suspend partition has wrong signature?
Feb 14 22:29:09 localhost kernel: [4294681.979000] EXT3-fs: INFO: recovery required on readonly filesystem.
Feb 14 22:29:09 localhost kernel: [4294681.979000] EXT3-fs: write access will be enabled during recovery.
Feb 14 22:29:09 localhost kernel: [4294689.586000] kjournald starting.  Commit interval 5 seconds
Feb 14 22:29:09 localhost kernel: [4294689.586000] EXT3-fs: recovery complete.
Feb 14 22:29:09 localhost kernel: [4294689.587000] EXT3-fs: mounted filesystem with ordered data mode.
Feb 14 22:29:09 localhost kernel: [4294690.921000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
Feb 14 22:29:09 localhost kernel: [4294694.778000] Adding 457812k swap on /dev/hda5.  Priority:-1 extents:1
Feb 14 22:29:09 localhost kernel: [4294695.120000] EXT3 FS on hda2, internal journal
Feb 14 22:29:09 localhost kernel: [4294704.615000] parport: PnPBIOS parport detected.
Feb 14 22:29:09 localhost kernel: [4294704.615000] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
Feb 14 22:29:09 localhost kernel: [4294704.702000] lp0: using parport0 (interrupt-driven).
Feb 14 22:29:09 localhost kernel: [4294704.737000] mice: PS/2 mouse device common for all mice
Feb 14 22:29:09 localhost kernel: [4294704.828000] SCSI subsystem initialized
Feb 14 22:29:09 localhost kernel: [4294704.834000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
Feb 14 22:29:09 localhost kernel: [4294704.959000] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
Feb 14 22:29:09 localhost kernel: [4294705.055000] alps.c: Enabling hardware tapping
Feb 14 22:29:09 localhost kernel: [4294705.059000] ndiswrapper: driver bcmwl5 (Broadcom,07/17/2003, 3.30.15.0) loaded
Feb 14 22:29:09 localhost kernel: [4294705.065000] ndiswrapper: using irq 18
Feb 14 22:29:09 localhost kernel: [4294705.316000] input: PS/2 Mouse on isa0060/serio4
Feb 14 22:29:09 localhost kernel: [4294705.320000] input: AlpsPS/2 ALPS GlidePoint on isa0060/serio4
Feb 14 22:29:09 localhost kernel: [4294705.573000] ts: Compaq touchscreen protocol output
Feb 14 22:29:09 localhost kernel: [4294705.711000] wlan0: ndiswrapper ethernet device 00:90:4b:4d:01:68 using driver bcmwl5, configuration file 14E4:4320:103C:12F4.5.conf
Feb 14 22:29:09 localhost kernel: [4294705.711000] wlan0: encryption modes supported: WEP, WPA with TKIP, WPA with AES/CCMP
Feb 14 22:29:09 localhost kernel: [4294709.389000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
Feb 14 22:29:09 localhost kernel: [4294710.513000] cdrom: open failed.
Feb 14 22:29:09 localhost kernel: [4294713.673000] Linux agpgart interface v0.101 (c) Dave Jones
Feb 14 22:29:09 localhost kernel: [4294713.682000] agpgart: Detected Ati IGP9100/M chipset
Feb 14 22:29:09 localhost kernel: [4294713.702000] agpgart: AGP aperture is 32M @ 0xea000000
Feb 14 22:29:09 localhost kernel: [4294713.782000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb 14 22:29:09 localhost kernel: [4294715.402000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
Feb 14 22:29:09 localhost kernel: [4294715.458000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[e8208000-e82087ff]  Max Packet=[2048]
Feb 14 22:29:09 localhost kernel: [4294715.657000] Linux Kernel Card Services
Feb 14 22:29:09 localhost kernel: [4294715.657000]   options:  [pci] [cardbus] [pm]
Feb 14 22:29:09 localhost kernel: [4294715.672000] Yenta: CardBus bridge found at 0000:02:04.0 [103c:006b]
Feb 14 22:29:09 localhost kernel: [4294715.672000] Yenta: Enabling burst memory read transactions
Feb 14 22:29:09 localhost kernel: [4294715.672000] Yenta: Using CSCINT to route CSC interrupts to PCI
Feb 14 22:29:09 localhost kernel: [4294715.672000] Yenta: Routing CardBus interrupts to PCI
Feb 14 22:29:09 localhost kernel: [4294715.672000] Yenta TI: socket 0000:02:04.0, mfunc 0x01111d22, devctl 0x64
Feb 14 22:29:09 localhost kernel: [4294715.893000] Yenta: ISA IRQ mask 0x0058, PCI irq 17
Feb 14 22:29:09 localhost kernel: [4294715.893000] Socket status: 30000086
Feb 14 22:29:09 localhost kernel: [4294715.962000] Yenta: CardBus bridge found at 0000:02:04.1 [103c:006b]
Feb 14 22:29:09 localhost kernel: [4294715.963000] Yenta: Using CSCINT to route CSC interrupts to PCI
Feb 14 22:29:09 localhost kernel: [4294715.963000] Yenta: Routing CardBus interrupts to PCI
Feb 14 22:29:09 localhost kernel: [4294715.963000] Yenta TI: socket 0000:02:04.1, mfunc 0x01111d22, devctl 0x64
Feb 14 22:29:09 localhost kernel: [4294716.184000] Yenta: ISA IRQ mask 0x0058, PCI irq 17
Feb 14 22:29:09 localhost kernel: [4294716.184000] Socket status: 30000006
Feb 14 22:29:09 localhost kernel: [4294717.824000] Real Time Clock Driver v1.12
Feb 14 22:29:09 localhost kernel: [4294717.917000] input: PC Speaker
Feb 14 22:29:09 localhost kernel: [4294721.044000] floppy0: no floppy controllers found
Feb 14 22:29:09 localhost kernel: [4294721.951000] NET: Registered protocol family 17
Feb 14 22:29:09 localhost kernel: [4294726.728000] NET: Registered protocol family 10
Feb 14 22:29:09 localhost kernel: [4294726.728000] Disabled Privacy Extensions on device c02eb280(lo)
Feb 14 22:29:09 localhost kernel: [4294726.728000] IPv6 over IPv4 tunneling driver
Feb 14 22:29:09 localhost kernel: [4294729.355000] ACPI: AC Adapter [ACAD] (off-line)
Feb 14 22:29:09 localhost kernel: [4294729.514000] ACPI: Battery Slot [BAT1] (battery present)
Feb 14 22:29:09 localhost kernel: [4294729.533000] ACPI: Power Button (FF) [PWRF]
Feb 14 22:29:09 localhost kernel: [4294729.533000] ACPI: Lid Switch [LID]
Feb 14 22:29:09 localhost kernel: [4294729.533000] ACPI: Power Button (CM) [PWRB]
Feb 14 22:29:09 localhost kernel: [4294729.760000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Feb 14 22:29:12 localhost hpiod: 0.9.5 accepting connections at 32769... 
Feb 14 22:29:12 localhost hp: unable to open /var/run/hplip/hpssd.port: No such file or directory: prnt/hpijs/hplip_api.c 84 
Feb 14 22:29:12 localhost hp: unable to connect hpssd socket 50002: Connection refused: prnt/hpijs/hplip_api.c 710 
Feb 14 22:29:15 localhost kernel: [4294736.685000] apm: BIOS not found.
Feb 14 22:29:16 localhost kernel: [4294737.988000] cs: IO port probe 0x100-0x4ff: excluding 0x408-0x40f 0x4d0-0x4d7
Feb 14 22:29:16 localhost kernel: [4294737.989000] cs: IO port probe 0x100-0x4ff: excluding 0x408-0x40f 0x4d0-0x4d7
Feb 14 22:29:16 localhost kernel: [4294737.991000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xcd0-0xcd7
Feb 14 22:29:16 localhost kernel: [4294737.991000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xcd0-0xcd7
Feb 14 22:29:16 localhost kernel: [4294737.992000] cs: IO port probe 0xa00-0xaff: clean.
Feb 14 22:29:16 localhost kernel: [4294737.992000] cs: IO port probe 0xa00-0xaff: clean.
Feb 14 22:29:17 localhost kernel: [4294738.303000] acpi-cpufreq: CPU0 - ACPI performance management activated.
Feb 14 22:29:19 localhost kernel: [4294740.205000] Bluetooth: Core ver 2.7
Feb 14 22:29:19 localhost kernel: [4294740.205000] NET: Registered protocol family 31
Feb 14 22:29:19 localhost kernel: [4294740.205000] Bluetooth: HCI device and connection manager initialized
Feb 14 22:29:19 localhost kernel: [4294740.205000] Bluetooth: HCI socket layer initialized
Feb 14 22:29:19 localhost kernel: [4294740.269000] Bluetooth: L2CAP ver 2.7
Feb 14 22:29:19 localhost kernel: [4294740.269000] Bluetooth: L2CAP socket layer initialized
Feb 14 22:29:19 localhost kernel: [4294740.316000] Bluetooth: RFCOMM ver 1.5
Feb 14 22:29:19 localhost kernel: [4294740.316000] Bluetooth: RFCOMM socket layer initialized
Feb 14 22:29:19 localhost kernel: [4294740.316000] Bluetooth: RFCOMM TTY layer initialized
Feb 14 22:29:21 localhost kernel: [4294742.380000] [drm] Initialized drm 1.0.0 20040925
Feb 14 22:29:21 localhost kernel: [4294742.391000] [drm] Initialized radeon 1.16.0 20050311 on minor 0: ATI Technologies Inc M9+ 5C61 [Radeon Mobility 9200 (AGP)]
Feb 14 22:29:21 localhost kernel: [4294742.392000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
Feb 14 22:29:21 localhost kernel: [4294742.392000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
Feb 14 22:29:21 localhost kernel: [4294742.392000] agpgart: Putting AGP V3 device at 0000:01:05.0 into 4x mode
Feb 14 22:29:21 localhost kernel: [4294742.397000] [drm] Loading R200 Microcode
Feb 14 22:29:22 localhost kernel: [4294743.482000] acpi-cpufreq: Transition failed
Feb 14 22:29:36 localhost kernel: [4294757.275000] acpi-cpufreq: Transition failed
Feb 14 22:29:45 localhost kernel: [4294766.478000] acpi-cpufreq: Transition failed
```

any ideas ?

j

---

### Post by Greg2 on 2006-02-15
You could give this a try:```
acpi=strict acpi=noirq pci=biosirq pci=nosort irqpoll routeirq
``` It will slow the boot process down a bit, but it may work. If it doesn’t would you please post your dmesg?

Don’t worry, there are some very good kernel hackers working to patch this for future kernels.

---

### Post by waldick on 2006-02-15
ok, i made the change and the system does not crash, but i get the same message regarding cpu freq transition failure...

so here is my dmesg file:

```
bility mode.
[4294667.296000] OEM ID:   Product ID: RS300 Board APIC at: 0xFEE00000
[4294667.296000] I/O APIC #1 Version 17 at 0xFEC00000.
[4294667.296000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[4294667.296000] Processors: 1
[4294667.296000] Allocating PCI resources starting at 30000000 (gap: 30000000:cec00000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda2 ro quiet splash acpi=strict acpi=noirq pci=biosirq pci=nosort irqpoll routeirq
[4294667.296000] Misrouted IRQ fixup and polling support enabled.
[4294667.296000] This may significantly impact system performance.
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] mapped IOAPIC to ffffc000 (fec00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[4294667.296000] Detected 3067.349 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294670.102000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[4294670.103000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294670.116000] Memory: 510340k/523712k available (1416k kernel code, 12740k reserved, 762k data, 224k init, 0k highmem)
[4294670.116000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294670.116000] Calibrating delay loop... 6078.46 BogoMIPS (lpj=3039232)
[4294670.139000] Security Framework v1.0.0 initialized
[4294670.139000] SELinux:  Disabled at boot.
[4294670.139000] Mount-cache hash table entries: 512
[4294670.139000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[4294670.139000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[4294670.139000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[4294670.139000] CPU: L2 cache: 512K
[4294670.139000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00004400 00000000 00000000
[4294670.139000] CPU: Intel Mobile Intel(R) Pentium(R) 4     CPU 3.06GHz stepping 09
[4294670.139000] Enabling fast FPU save and restore... done.
[4294670.139000] Enabling unmasked SIMD FPU exception support... done.
[4294670.139000] Checking 'hlt' instruction... OK.
[4294670.143000] Checking for popad bug... OK.
[4294670.143000] checking if image is initramfs... it is
[4294670.517000] Freeing initrd memory: 5175k freed
[4294670.517000] ACPI: Looking for DSDT in initrd... not found!
[4294670.556000]  not found!
[4294670.561000] ACPI: setting ELCR to 0e20 (from 0c20)
[4294671.390000] ENABLING IO-APIC IRQs
[4294671.390000] ..TIMER: vector=0x31 pin1=2 pin2=0
[4294671.502000] NET: Registered protocol family 16
[4294671.502000] EISA bus registered
[4294671.502000] ACPI: bus type pci registered
[4294671.502000] PCI: PCI BIOS revision 2.10 entry at 0xfd968, last bus=2
[4294671.502000] PCI: Using configuration type 1
[4294671.502000] mtrr: v2.0 (20020519)
[4294671.502000] ACPI: Subsystem revision 20050729
[4294671.528000] ACPI: Interpreter enabled
[4294671.528000] ACPI: Using PIC for interrupt routing
[4294671.528000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294671.528000] PCI: Probing PCI hardware (bus 00)
[4294671.528000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294671.528000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[4294671.553000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:14.1
[4294671.553000] Boot video device is 0000:01:05.0
[4294671.553000] PCI: Transparent bridge - 0000:00:14.4
[4294671.555000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294671.555000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[4294671.556000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[4294671.563000] burst-mode-ec-10-Aug
[4294671.563000] ACPI: Embedded Controller [EC0] (gpe 6)
[4294671.608000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294671.608000] pnp: PnP ACPI init
[4294671.635000] pnp: PnP ACPI: found 9 devices
[4294671.635000] PnPBIOS: Disabled by ACPI PNP
[4294671.635000] PCI: Probing PCI hardware
[4294671.635000] PCI: Using IRQ router default [1002/434c] at 0000:00:14.3
[4294671.635000] PCI->APIC IRQ transform: 0000:00:13.0[A] -> IRQ 19
[4294671.635000] PCI->APIC IRQ transform: 0000:00:13.1[A] -> IRQ 19
[4294671.635000] PCI->APIC IRQ transform: 0000:00:14.1[A] -> IRQ 17
[4294671.635000] PCI->APIC IRQ transform: 0000:00:14.5[B] -> IRQ 17
[4294671.635000] PCI->APIC IRQ transform: 0000:00:14.6[B] -> IRQ 17
[4294671.635000] PCI->APIC IRQ transform: 0000:01:05.0[A] -> IRQ 16
[4294671.635000] PCI->APIC IRQ transform: 0000:02:00.0[A] -> IRQ 16
[4294671.635000] PCI->APIC IRQ transform: 0000:02:02.0[A] -> IRQ 18
[4294671.635000] PCI->APIC IRQ transform: 0000:02:03.0[A] -> IRQ 19
[4294671.635000] PCI: using PPB 0000:00:14.4[A] to get irq 17
[4294671.635000] PCI->APIC IRQ transform: 0000:02:04.0[A] -> IRQ 17
[4294671.635000] PCI: using PPB 0000:00:14.4[B] to get irq 17
[4294671.635000] PCI->APIC IRQ transform: 0000:02:04.1[B] -> IRQ 17
[4294671.635000] PCI->APIC IRQ transform: 0000:02:07.0[A] -> IRQ 16
[4294671.635000] PCI->APIC IRQ transform: 0000:02:07.1[B] -> IRQ 18
[4294671.635000] PCI->APIC IRQ transform: 0000:02:07.2[C] -> IRQ 19
[4294671.635000] pnp: 00:06: ioport range 0x200-0x20f has been reserved
[4294671.635000] pnp: 00:06: ioport range 0xc14-0xc14 has been reserved
[4294671.635000] pnp: 00:06: ioport range 0xc50-0xc52 has been reserved
[4294671.635000] pnp: 00:06: ioport range 0xc6c-0xc6c has been reserved
[4294671.636000] audit: initializing netlink socket (disabled)
[4294671.636000] audit: initialized
[4294671.636000] VFS: Disk quotas dquot_6.5.1
[4294671.636000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294671.636000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294671.636000] devfs: boot_options: 0x0
[4294671.636000] Initializing Cryptographic API
[4294671.636000] isapnp: Scanning for PnP cards...
[4294671.989000] isapnp: No Plug & Play device found
[4294672.003000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[4294672.012000] i8042.c: Detected active multiplexing controller, rev 1.1.
[4294672.017000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[4294672.018000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[4294672.018000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[4294672.019000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[4294672.020000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294672.020000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294672.021000] io scheduler noop registered
[4294672.021000] io scheduler anticipatory registered
[4294672.021000] io scheduler deadline registered
[4294672.021000] io scheduler cfq registered
[4294672.022000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294672.024000] EISA: Probing bus 0 at eisa.0
[4294672.024000] Cannot allocate resource for EISA slot 1
[4294672.024000] Cannot allocate resource for EISA slot 8
[4294672.024000] EISA: Detected 0 cards.
[4294672.024000] NET: Registered protocol family 2
[4294672.036000] IP: routing cache hash table of 4096 buckets, 32Kbytes
[4294672.036000] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[4294672.036000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[4294672.036000] TCP: Hash tables configured (established 32768 bind 32768)
[4294672.036000] NET: Registered protocol family 8
[4294672.036000] NET: Registered protocol family 20
[4294672.036000] ACPI wakeup devices: 
[4294672.036000] MODM ELAN USB0 USB1 USB2 
[4294672.036000] ACPI: (supports S0 S3 S4 S5)
[4294672.037000] Freeing unused kernel memory: 224k freed
[4294672.055000] vga16fb: initializing
[4294672.055000] vga16fb: mapped to 0xc00a0000
[4294672.169000] Console: switching to colour frame buffer device 80x30
[4294672.169000] fb0: VGA16 VGA frame buffer device
[4294672.186000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294673.328000] Capability LSM initialized
[4294673.338000] NET: Registered protocol family 1
[4294673.349000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294673.349000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294673.349000] ACPI: bus type ide registered
[4294673.358000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[4294673.359000] ATIIXP: chipset revision 0
[4294673.359000] ATIIXP: not 100% native mode: will probe irqs later
[4294673.359000]     ide0: BM-DMA at 0x8060-0x8067, BIOS settings: hda:DMA, hdb:pio
[4294673.359000]     ide1: BM-DMA at 0x8068-0x806f, BIOS settings: hdc:DMA, hdd:pio
[4294673.359000] Probing IDE interface ide0...
[4294673.623000] hda: IC25N060ATMR04-0, ATA DISK drive
[4294674.235000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294674.235000] Probing IDE interface ide1...
[4294674.907000] hdc: HL-DT-ST DVD+RW GCA-4040N, ATAPI CD/DVD-ROM drive
[4294675.213000] ide1 at 0x170-0x177,0x376 on irq 15
[4294675.213000] Probing IDE interface ide2...
[4294675.726000] Probing IDE interface ide3...
[4294676.239000] Probing IDE interface ide4...
[4294676.752000] Probing IDE interface ide5...
[4294677.268000] hda: max request size: 1024KiB
[4294677.288000] hda: 117210240 sectors (60011 MB) w/7884KiB Cache, CHS=16383/255/63, UDMA(100)
[4294677.288000] hda: cache flushes supported
[4294677.288000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 < p5 >
[4294677.336000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache
[4294677.336000] Uniform CD-ROM driver Revision: 3.20
[4294677.604000] Attempting manual resume
[4294677.652000] swsusp: Suspend partition has wrong signature?
[4294677.692000] usbcore: registered new driver usbfs
[4294677.692000] usbcore: registered new driver hub
[4294677.692000] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[4294677.693000] ohci_hcd 0000:00:13.0: ATI Technologies Inc OHCI USB Controller #1
[4294677.693000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[4294677.693000] ohci_hcd 0000:00:13.0: irq 19, io mem 0xe8001000
[4294677.698000] hub 1-0:1.0: USB hub found
[4294677.698000] hub 1-0:1.0: 3 ports detected
[4294677.703000] ohci_hcd 0000:00:13.1: ATI Technologies Inc OHCI USB Controller #2
[4294677.703000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[4294677.703000] ohci_hcd 0000:00:13.1: irq 19, io mem 0xe8002000
[4294677.708000] hub 2-0:1.0: USB hub found
[4294677.708000] hub 2-0:1.0: 3 ports detected
[4294677.713000] ohci_hcd 0000:02:07.0: NEC Corporation USB
[4294677.713000] ohci_hcd 0000:02:07.0: new USB bus registered, assigned bus number 3
[4294677.713000] ohci_hcd 0000:02:07.0: irq 16, io mem 0xe8206000
[4294677.744000] hub 3-0:1.0: USB hub found
[4294677.744000] hub 3-0:1.0: 3 ports detected
[4294677.775000] ohci_hcd 0000:02:07.1: NEC Corporation USB (#2)
[4294677.775000] ohci_hcd 0000:02:07.1: new USB bus registered, assigned bus number 4
[4294677.775000] ohci_hcd 0000:02:07.1: irq 18, io mem 0xe8207000
[4294677.806000] hub 4-0:1.0: USB hub found
[4294677.806000] hub 4-0:1.0: 2 ports detected
[4294677.904000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[4294677.904000] 8139cp: pci dev 0000:02:03.0 (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[4294677.904000] 8139cp: Try the "8139too" driver instead.
[4294677.906000] 8139too Fast Ethernet driver 0.9.27
[4294677.906000] eth0: RealTek RTL8139 at 0xa000, 00:02:3f:6b:77:c5, IRQ 19
[4294677.906000] eth0:  Identified 8139 chip type 'RTL-8101'
[4294677.944000] ehci_hcd 0000:02:07.2: NEC Corporation USB 2.0
[4294677.965000] ehci_hcd 0000:02:07.2: new USB bus registered, assigned bus number 5
[4294677.965000] ehci_hcd 0000:02:07.2: irq 19, io mem 0xe8208c00
[4294677.965000] ehci_hcd 0000:02:07.2: park 0
[4294677.965000] ehci_hcd 0000:02:07.2: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294677.965000] hub 5-0:1.0: USB hub found
[4294677.965000] hub 5-0:1.0: 5 ports detected
[4294680.432000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[4294680.439000] ACPI: Thermal Zone [THRM] (47 C)
[4294680.719000] Attempting manual resume
[4294680.743000] swsusp: Suspend partition has wrong signature?
[4294680.798000] kjournald starting.  Commit interval 5 seconds
[4294680.798000] EXT3-fs: mounted filesystem with ordered data mode.
[4294682.288000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294686.159000] Adding 457812k swap on /dev/hda5.  Priority:-1 extents:1
[4294686.572000] EXT3 FS on hda2, internal journal
[4294696.062000] parport: PnPBIOS parport detected.
[4294696.062000] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[4294696.146000] lp0: using parport0 (interrupt-driven).
[4294696.176000] mice: PS/2 mouse device common for all mice
[4294696.208000] ieee1394: Initialized config rom entry `ip1394'
[4294696.215000] SCSI subsystem initialized
[4294696.227000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[4294696.374000] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
[4294696.469000] ndiswrapper: driver bcmwl5 (Broadcom,07/17/2003, 3.30.15.0) loaded
[4294696.475000] ndiswrapper: using irq 18
[4294696.836000] alps.c: Enabling hardware tapping
[4294696.911000] input: PS/2 Mouse on isa0060/serio4
[4294696.913000] input: AlpsPS/2 ALPS GlidePoint on isa0060/serio4
[4294697.109000] ts: Compaq touchscreen protocol output
[4294697.122000] wlan0: ndiswrapper ethernet device 00:90:4b:4d:01:68 using driver bcmwl5, configuration file 14E4:4320:103C:12F4.5.conf
[4294697.122000] wlan0: encryption modes supported: WEP, WPA with TKIP, WPA with AES/CCMP
[4294700.215000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294701.411000] cdrom: open failed.
[4294704.841000] Linux agpgart interface v0.101 (c) Dave Jones
[4294704.850000] agpgart: Detected Ati IGP9100/M chipset
[4294704.870000] agpgart: AGP aperture is 32M @ 0xea000000
[4294704.951000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294704.956000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294704.956000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294706.710000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[4294706.766000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[e8208000-e82087ff]  Max Packet=[2048]
[4294706.956000] Linux Kernel Card Services
[4294706.956000]   options:  [pci] [cardbus] [pm]
[4294706.975000] Yenta: CardBus bridge found at 0000:02:04.0 [103c:006b]
[4294706.975000] Yenta: Enabling burst memory read transactions
[4294706.975000] Yenta: Using CSCINT to route CSC interrupts to PCI
[4294706.975000] Yenta: Routing CardBus interrupts to PCI
[4294706.975000] Yenta TI: socket 0000:02:04.0, mfunc 0x01111d22, devctl 0x64
[4294707.196000] Yenta: ISA IRQ mask 0x0058, PCI irq 17
[4294707.196000] Socket status: 30000086
[4294707.199000] Yenta: CardBus bridge found at 0000:02:04.1 [103c:006b]
[4294707.199000] Yenta: Using CSCINT to route CSC interrupts to PCI
[4294707.199000] Yenta: Routing CardBus interrupts to PCI
[4294707.199000] Yenta TI: socket 0000:02:04.1, mfunc 0x01111d22, devctl 0x64
[4294707.420000] Yenta: ISA IRQ mask 0x0058, PCI irq 17
[4294707.420000] Socket status: 30000006
[4294708.024000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[413f02001985003d]
[4294709.048000] Real Time Clock Driver v1.12
[4294709.186000] input: PC Speaker
[4294712.290000] floppy0: no floppy controllers found
[4294713.261000] NET: Registered protocol family 17
[4294716.517000] NET: Registered protocol family 10
[4294716.517000] Disabled Privacy Extensions on device c02eb280(lo)
[4294716.517000] IPv6 over IPv4 tunneling driver

```

so hopefully this helps,

thanks,
j

---

### Post by waldick on 2006-02-16
well, it just crashed....i rebooted with acpi=off...

so there is still a problem

j

---

### Post by Greg2 on 2006-02-16
Have you tried the 686 kernel for your P4, instead of the stock 386 kernel?

---

### Post by waldick on 2006-02-16
hi Greg,
i'm pretty new at this and frankly i don't know how to update or otherwise change the kernel...

j

---

### Post by Greg2 on 2006-02-17
OK... just use the Synaptic package manager to install the linux-image-686 and linux-restricted-modules-686 and whatever else you need. Then reboot and select the new image from the grub menu.

Please note that you will still ‘probably’ have to add a boot parameter or two to your grub memu.1st file. You should also do a search for  ‘linux-image-686’ on the forum for more ‘specific’ info... because I use the k7 kernel.

---

### Post by waldick on 2006-02-17
hi Greg,
that's what i thought, but i get an error message when i try to download the 686 kernel...maybe the wrong repository..what's the latest version, maybe i need to enable another repository...

any ideas..

j

---

### Post by waldick on 2006-02-17
here's the error message i get:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.12/linux-image-2.6.12-10-686_2.6.12-10.26_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.12/linux-image-2.6.12-10-686_2.6.12-10.26_i386.deb)
  404 Not Found [IP: 82.211.81.138 80]


W: Failed to fetch [http://wine.sourceforge.net/apt/binary/wine_0.9.7-winehq-1_i386.deb](http://wine.sourceforge.net/apt/binary/wine_0.9.7-winehq-1_i386.deb)
  404 Not Found


W: Failed to fetch [http://eyagi.bpa.nu/~jamie/ubuntu/dists/hoary/main/binary-i386/graphics/mplayer-386_1.0-pre7cvs20050716-0.1ubuntu10~udubackport2_i386.deb](http://eyagi.bpa.nu/~jamie/ubuntu/dists/hoary/main/binary-i386/graphics/mplayer-386_1.0-pre7cvs20050716-0.1ubuntu10~udubackport2_i386.deb)
  
thanks,

j

W: Failed to fetch [http://eyagi.bpa.nu/~jamie/ubuntu/dists/hoary/main/binary-i386/x11/transcode_1.0.2-0.0ubuntu0~udubackport1_i386.deb](http://eyagi.bpa.nu/~jamie/ubuntu/dists/hoary/main/binary-i386/x11/transcode_1.0.2-0.0ubuntu0~udubackport1_i386.deb)

---

### Post by Greg2 on 2006-02-18
Please read this section:
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)
Here, use this to make yourself a nice /etc/apt/sources.list:
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
I would also suggest getting your kernel installed properly before you start trying to install wine and whatever else you want. :)

---

### Post by waldick on 2006-02-18
thanks Greg,
i got 686 properly installed, but it still locks up after some time, although it now take longer to lock up...i still get the "Feb 18 13:10:22 localhost kernel: [4294950.348000] acpi-cpufreq: Transition failed" message...

i'll try adding the line you suggested earlier with this new kernel...

i'll update you later...

j

---

