---
title: "Slow bootup"
date: 2005-10-26
forum: Hardware &amp; Laptops
---

### Post by jacodt on 2005-10-26
Hello all,

I am running Kubuntu 5.10 with the 686 kernel on a Toshiba A40 Satellite Pro. The problem I am experiencing is that bootup takes extremely long. I have narrowed the delay down to ide probing. 

Dmesg (or booting with noquiet parameter) shows the following:

d000 (fee00000)
[4294667.296000] mapped IOAPIC to ffffc000 (fec00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[4294667.296000] Detected 2593.511 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294671.188000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294671.188000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294671.200000] Memory: 493836k/507136k available (1622k kernel code, 12672k reserved, 731k data, 168k init, 0k highmem)
[4294671.200000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294671.200000] Calibrating delay loop... 5144.57 BogoMIPS (lpj=2572288)
[4294671.223000] Security Framework v1.0.0 initialized
[4294671.223000] SELinux:  Disabled at boot.
[4294671.223000] Mount-cache hash table entries: 512
[4294671.223000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[4294671.223000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[4294671.223000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[4294671.223000] CPU: L2 cache: 128K
[4294671.223000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00004400 00000000 00000000
[4294671.223000] Intel machine check architecture supported.
[4294671.223000] Intel machine check reporting enabled on CPU#0.
[4294671.223000] CPU0: Intel P4/Xeon Extended MCE MSRs (12) available
[4294671.223000] CPU0: Thermal monitoring enabled
[4294671.223000] CPU: Intel(R) Celeron(R) CPU 2.60GHz stepping 09
[4294671.223000] Enabling fast FPU save and restore... done.
[4294671.223000] Enabling unmasked SIMD FPU exception support... done.
[4294671.223000] Checking 'hlt' instruction... OK.
[4294671.227000] checking if image is initramfs... it is
[4294671.743000] Freeing initrd memory: 5501k freed
[4294671.744000] ACPI: Looking for DSDT in initrd... not found!
[4294671.793000]  not found!
[4294671.801000] ENABLING IO-APIC IRQs
[4294671.801000] ..TIMER: vector=0x31 pin1=2 pin2=-1
[4294671.912000] NET: Registered protocol family 16
[4294671.912000] ACPI: bus type pci registered
[4294671.912000] PCI: PCI BIOS revision 2.10 entry at 0xfd2fe, last bus=3
[4294671.912000] PCI: Using configuration type 1
[4294671.912000] mtrr: v2.0 (20020519)
[4294671.913000] ACPI: Subsystem revision 20050729
[4294671.917000] ACPI: Interpreter enabled
[4294671.917000] ACPI: Using IOAPIC for interrupt routing
[4294671.918000] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
[4294671.918000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *11)
[4294671.919000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *11)
[4294671.919000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *11)
[4294671.920000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *11)
[4294671.920000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *11)
[4294671.921000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *11)
[4294671.921000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *11)
[4294671.922000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294671.922000] PCI: Probing PCI hardware (bus 00)
[4294671.922000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294671.922000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[4294671.924000] Boot video device is 0000:00:02.0
[4294671.924000] PCI: Enabled i801 SMBus device
[4294671.924000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[4294671.924000] PCI: Transparent bridge - 0000:00:1e.0
[4294671.927000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294671.927000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[4294671.933000] ACPI: Power Resource [PFAN] (off)
[4294671.933000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294671.934000] pnp: PnP ACPI init
[4294671.938000] pnp: PnP ACPI: found 10 devices
[4294671.938000] PnPBIOS: Disabled by ACPI PNP
[4294671.938000] PCI: Using ACPI for IRQ routing
[4294671.938000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294671.946000] Simple Boot Flag at 0x7c set to 0x1
[4294671.946000] audit: initializing netlink socket (disabled)
[4294671.946000] audit: initialized
[4294671.947000] VFS: Disk quotas dquot_6.5.1
[4294671.947000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294671.947000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294671.947000] devfs: boot_options: 0x0
[4294671.947000] Initializing Cryptographic API
[4294671.947000] isapnp: Scanning for PnP cards...
[4294672.301000] isapnp: No Plug & Play device found
[4294672.361000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294672.372000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294672.373000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294672.373000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294672.379000] PCI: Enabling device 0000:00:1f.6 (0000 -> 0001)
[4294672.379000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> GSI 17 (level, low) -> IRQ 17
[4294672.379000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[4294672.379000] io scheduler noop registered
[4294672.379000] io scheduler anticipatory registered
[4294672.379000] io scheduler deadline registered
[4294672.379000] io scheduler cfq registered
[4294672.380000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294672.381000] NET: Registered protocol family 2
[4294672.391000] IP: routing cache hash table of 4096 buckets, 32Kbytes
[4294672.391000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[4294672.391000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294672.391000] TCP: Hash tables configured (established 16384 bind 16384)
[4294672.391000] NET: Registered protocol family 8
[4294672.391000] NET: Registered protocol family 20
[4294672.391000] ACPI wakeup devices: 
[4294672.392000] VIY0 USB1 USB2 USB4 AMDM  LID PWRB 
[4294672.392000] ACPI: (supports S0 S3 S4 S5)
[4294672.392000] Freeing unused kernel memory: 168k freed
[4294672.444000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294672.447000] Capability LSM initialized
[4294672.467000] NET: Registered protocol family 1
[4294672.490000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294672.490000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294672.490000] ACPI: bus type ide registered
[4294672.500000] ICH4: IDE controller at PCI slot 0000:00:1f.1
[4294672.500000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[4294672.500000] ICH4: chipset revision 3
[4294672.500000] ICH4: not 100% native mode: will probe irqs later
[4294672.500000]     ide0: BM-DMA at 0xbfa0-0xbfa7, BIOS settings: hda:DMA, hdb:pio
[4294672.500000]     ide1: BM-DMA at 0xbfa8-0xbfaf, BIOS settings: hdc:DMA, hdd:pio
[4294672.500000] Probing IDE interface ide0...
[4294672.764000] hda: TOSHIBA MK4025GAS, ATA DISK drive
[4294673.376000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294673.376000] Probing IDE interface ide1...
[4294674.048000] hdc: TOSHIBA DVD-ROM SD-R2412, ATAPI CD/DVD-ROM drive
[4294674.660000] ide1 at 0x170-0x177,0x376 on irq 15
<------------------------------------------->>>> This is where a delay occurs for approximately 30seconds and then bootup continues normally

[4294674.660000] Probing IDE interface ide2...
[4294675.173000] Probing IDE interface ide3...
[4294675.685000] Probing IDE interface ide4...
[4294710.453000] ide4: Wait for ready failed before probe !
[4294710.963000] Probing IDE interface ide5...
[4294711.480000] hda: max request size: 128KiB
[4294711.720000] hda: 78140160 sectors (40007 MB), CHS=65535/16/63, UDMA(100)

<------- REST CUT

Now I have tried adding ide2=noprobe ide3=noprobe ide4=noprobe, and played arround with acpi vs noacpi kernel parameters, all to no avail. Currently I am using no special kernel parameters, only ro and noquiet.

Any help would be appreciated

Kind regards
Jaco Du Toit

---

### Post by pereira on 2005-11-06
I´m having the same problem with a Toshiba A45-S150. Stops just after probe my ide1 and before ide2.

Someone has an idea?

I have the same problem with other linux distribution.

Bye,
---
Prof. Rodrigo Pereira Braga

---

### Post by dedalus on 2005-11-10
Hi, 
if you see at the timestamp, you see that the problem ist after probing ide4:

[4294675.685000] Probing IDE interface ide4...
[4294710.453000] ide4: Wait for ready failed before probe !

imho are there 35 seconds between this to things.

I have the same problem with my Toshiba Sattelite 2410-404.

I tried also to disable ide4 with ther kernel command ide4=noprobe, but it didn' work  (in the documentation (ide.txt) is something daid that ide4 has something to do with pci and that such commands are only for ide0-ide3)

Did you find something new?
Does someone know how to deactivate ide4?


Cheers

---

### Post by varunus on 2005-11-11
I have the same problem with my satellite A45-S150.  Seems to be a toshiba-specific issue...

Sometimes, however, this does not happen.  I have no idea, I was pretty sure it had to do with the CD drive, since I notice the delay after IDE1 too.  Maybe there's a BIOS setting we can change or something?

Anyone with a toshiba know?

---

### Post by richardh on 2005-11-13
I had the same problem with Sat a10-169
NEW 6.14 kernel fixes it no problem. Just read how to compile Vanilla kernel in the Ubunto forum.
Slow boot was driving me mad. Could not get rid of it with any of fixes (koption ide1=noprobe ... and also tried recompiling kernel, but gave up)
Problem - it seems - is due to generic IDE module probing for IDE interfaces that arent there (actually the hang-up seems to be on IDE4)

---

### Post by obscenic on 2005-11-28
Having the same problem, but with probing for ide0. My primary IDE chain has on drives on it (I have an asus A7V-133), all my hdd's are on the promise controller...  Lags for over 90 seconds trying to probe ide0 and ide1.

Noprobe options don't stop it from probing, and no one seems to know how to rebuild the drivers or kernel to just disable this altogether...

I also encounter massive errors whilst trying to upgrade to the vanilla kernel.

---

### Post by krasny on 2006-01-15
Hi!

I have the same issue and it sucks. I read in other forums that the problem is CONFIG_GENERIC_IDE, but i tried to recompile without this module and kernel dont boot.

Anyone has reported this bug to ubuntu malone? it will be great a kernel fix :)

---

