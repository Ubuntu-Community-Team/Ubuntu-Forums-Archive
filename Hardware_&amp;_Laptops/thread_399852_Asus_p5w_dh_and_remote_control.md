---
title: "Asus p5w dh and remote control"
date: 2007-04-02
forum: Hardware &amp; Laptops
---

### Post by Jeffa on 2007-04-02
Hi all, 

I was wondering if anyone has been able to get the DH Remote control working on an Asus p5w dh.  I'm not having too much luck, and I can't seem to find much on the Asus website. 

Thanks in advance

---

### Post by RapMan on 2007-04-03
Yes, you have to compile lirc 0.81 pre from sources, there is support for asus remote.
I am using it with irkick for kde, works ok.

---

### Post by Jeffa on 2007-04-05
Thanks, that looks interesting but which hardware did you select from the install script? I don't see the Asus DH Remote. 

Thanks again.

---

### Post by Jeffa on 2007-04-08
bumping thread. 

I can't seem to get this working. I've tried compiling from sources, but I'm just not sure which dirver to select. There are no Asus devices listed in the USB devices. 

anyone have any thoughts? 

Many thanks.

---

### Post by RapMan on 2007-04-09
If you download and unpack [this]("http://lirc.sourceforge.net/software/snapshots/lirc-0.8.2pre1.tar.bz2"), then run ./setup.sh as root, you can choose the Asus DH driver (from USB drivers I think), then copy the config file for Asus DH remote.
Maybe you will have the same problem as me, I had to also specify my device when running lircd daemon. Becouse lircd thinks, that the device is something like /dev/usb/hiddev0 , but in (k)ubuntu is it only /dev/hiddev0 , so you have to run lircd --device=/dev/hiddev0 or specify this device in hardware.conf I think.
I can't have a look now, becouse I am not on my computer.

---

### Post by Jeffa on 2007-04-09
ahh. Thanks for fingind the right version. I see the Asus DH remote now. It appears to work properly, but when i finish, nothing happens. If I try the lircd --device=/dev/hiddev0 (or any other command in lircd) I get:
lircd: there seems to already be a lircd process with pid 20076
lircd: otherwise delete stale lockfile /var/run/lircd.pid 

any thoughts? 

thanks again for all the help. I'm definitely getting closer!

---

### Post by RapMan on 2007-04-11
Uff, there are lot of possible mistakes.
First try to run irw command to see, if the remote is working. You should see the names when pressing buttons on the remote.
If not, exit the program, copy the right config file for the Asus remote as lircd.conf, then run as root 
lircd stop
lircd 

and see what happends, it the device is recognised correctly, then in irw program, you will see the button names, if not, run as root
lircd stop
lircd start --device=/dev/hiddev0

---

### Post by Explosive_Cornflake on 2007-04-13
I'm stuck at this last step also. irw doesn't seem to pick anything up. I'm using the .conf file from the package in as /etc/lircd.conf. Any ideas? I notice i have to run irw as root, is that normal?

---

### Post by Jeffa on 2007-04-19
So, I'm still having a little trouble with this. 

I installed the package from source. Then ran

```
sudo /etc/init.d/lirc start
```

and get:

```
Starting lirc daemon: lircd.
```

then terminal returns. 

then i type:

```
irw
```

and the terminal returns immediately. according to [this]("https://help.ubuntu.com/community/Install_Lirc_Edgy") that means some modules aren't loading correctly and to check dmesg. which returns this:

```

[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Console: colour VGA+ 80x25
[17179569.184000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.184000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.184000] Memory: 2068960k/2096640k available (1911k kernel code, 26352k reserved, 1073k data, 308k init, 1179136k highmem)
[17179569.184000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.184000] hpet0: at MMIO 0xfed00000 (virtual 0xf8800000), IRQs 2, 8, 0
[17179569.184000] hpet0: 3 64-bit timers, 14318180 Hz
[17179569.184000] Using HPET for base-timer
[17179569.184000] Using HPET for gettimeofday
[17179569.184000] Detected 2404.145 MHz processor.
[17179569.184000] Using hpet for high-res timesource
[17179569.268000] Calibrating delay using timer specific routine.. 4811.83 BogoMIPS (lpj=9623668)
[17179569.268000] Security Framework v1.0.0 initialized
[17179569.268000] SELinux:  Disabled at boot.
[17179569.268000] Mount-cache hash table entries: 512
[17179569.268000] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e3bd 00000000 00000001
[17179569.268000] CPU: After vendor identify, caps: bfebfbff 20000000 00000000 00000000 0000e3bd 00000000 00000001
[17179569.268000] monitor/mwait feature present.
[17179569.268000] using mwait in idle threads.
[17179569.268000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179569.268000] CPU: L2 cache: 4096K
[17179569.268000] CPU: Hyper-Threading is disabled
[17179569.268000] CPU: After all inits, caps: bfebfbff 20000000 00000000 00000140 0000e3bd 00000000 00000001
[17179569.268000] Checking 'hlt' instruction... OK.
[17179569.284000] SMP alternatives: switching to UP code
[17179569.284000] checking if image is initramfs... it is
[17179569.628000] Freeing initrd memory: 5327k freed
[17179569.628000] ACPI: Core revision 20060707
[17179569.628000] ACPI: Looking for DSDT ... not found!
[17179569.648000] CPU0: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz stepping 06
[17179569.648000] SMP alternatives: switching to SMP code
[17179569.648000] Booting processor 1/1 eip 3000
[17179569.656000] Initializing CPU#1
[17179569.736000] Calibrating delay using timer specific routine.. 4808.28 BogoMIPS (lpj=9616574)
[17179569.736000] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e3bd 00000000 00000001
[17179569.736000] CPU: After vendor identify, caps: bfebfbff 20000000 00000000 00000000 0000e3bd 00000000 00000001
[17179569.736000] monitor/mwait feature present.
[17179569.736000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179569.736000] CPU: L2 cache: 4096K
[17179569.736000] CPU: Hyper-Threading is disabled
[17179569.736000] CPU: After all inits, caps: bfebfbff 20000000 00000000 00000140 0000e3bd 00000000 00000001
[17179569.736000] CPU1: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz stepping 06
[17179569.736000] Total of 2 processors activated (9620.12 BogoMIPS).
[17179569.736000] ENABLING IO-APIC IRQs
[17179569.736000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179569.904000] checking TSC synchronization across 2 CPUs: passed.
[17179569.908000] Brought up 2 CPUs
[17179569.984000] migration_cost=4000
[17179569.984000] NET: Registered protocol family 16
[17179569.984000] EISA bus registered
[17179569.984000] ACPI: bus type pci registered
[17179569.984000] PCI: BIOS Bug: MCFG area at f0000000 is not E820-reserved
[17179569.984000] PCI: Not using MMCONFIG.
[17179569.984000] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=6
[17179569.984000] PCI: Using configuration type 1
[17179569.984000] Setting up standard PCI resources
[17179570.000000] ACPI: Interpreter enabled
[17179570.000000] ACPI: Using IOAPIC for interrupt routing
[17179570.000000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.000000] PCI: Probing PCI hardware (bus 00)
[17179570.000000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179570.000000] Boot video device is 0000:06:00.0
[17179570.000000] PCI: JMB36x: Enabling dual function on 0000:02:00.0
[17179570.004000] PCI: Transparent bridge - 0000:00:1e.0
[17179570.004000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.004000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[17179570.004000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[17179570.004000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[17179570.004000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[17179570.004000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[17179570.004000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[17179570.008000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179570.008000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179570.008000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[17179570.012000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179570.012000] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 6 7 10 11 12 14 15)
[17179570.012000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179570.012000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.012000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179570.012000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.012000] pnp: PnP ACPI init
[17179570.012000] pnp: PnP ACPI: found 16 devices
[17179570.012000] PnPBIOS: Disabled by ACPI PNP
[17179570.012000] PCI: Using ACPI for IRQ routing
[17179570.012000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.012000] PCI: Cannot allocate resource region 0 of device 0000:02:00.0
[17179570.012000] PCI: Cannot allocate resource region 1 of device 0000:02:00.0
[17179570.012000] PCI: Cannot allocate resource region 2 of device 0000:02:00.0
[17179570.012000] PCI: Cannot allocate resource region 3 of device 0000:02:00.0
[17179570.024000] pnp: 00:07: ioport range 0x290-0x297 has been reserved
[17179570.024000] PCI: Bridge: 0000:00:01.0
[17179570.024000]   IO window: c000-cfff
[17179570.024000]   MEM window: faa00000-feafffff
[17179570.024000]   PREFETCH window: cff00000-efefffff
[17179570.024000] PCI: Bridge: 0000:00:1c.0
[17179570.024000]   IO window: disabled.
[17179570.024000]   MEM window: disabled.
[17179570.024000]   PREFETCH window: cfe00000-cfefffff
[17179570.024000] PCI: Bridge: 0000:00:1c.3
[17179570.024000]   IO window: b000-bfff
[17179570.024000]   MEM window: fa900000-fa9fffff
[17179570.024000]   PREFETCH window: disabled.
[17179570.024000] PCI: Bridge: 0000:00:1c.4
[17179570.024000]   IO window: a000-afff
[17179570.024000]   MEM window: fa800000-fa8fffff
[17179570.024000]   PREFETCH window: disabled.
[17179570.024000] PCI: Ignore bogus resource 1 [0:0] of 0000:02:00.0
[17179570.024000] PCI: Ignore bogus resource 3 [0:0] of 0000:02:00.0
[17179570.024000] PCI: Error while updating region 0000:02:00.0/0 (00009000 != 00000000)
[17179570.024000] PCI: Error while updating region 0000:02:00.0/2 (00009008 != 00000000)
[17179570.024000] PCI: Bridge: 0000:00:1c.5
[17179570.024000]   IO window: 9000-9fff
[17179570.024000]   MEM window: fa700000-fa7fffff
[17179570.024000]   PREFETCH window: disabled.
[17179570.024000] PCI: Bridge: 0000:00:1e.0
[17179570.024000]   IO window: disabled.
[17179570.024000]   MEM window: fa600000-fa6fffff
[17179570.024000]   PREFETCH window: disabled.
[17179570.024000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179570.024000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179570.024000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179570.024000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179570.024000] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 177
[17179570.024000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[17179570.024000] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 169
[17179570.024000] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[17179570.024000] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 17 (level, low) -> IRQ 185
[17179570.024000] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[17179570.024000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179570.024000] NET: Registered protocol family 2
[17179570.068000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.068000] TCP established hash table entries: 262144 (order: 9, 2097152 bytes)
[17179570.072000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179570.072000] TCP: Hash tables configured (established 262144 bind 65536)
[17179570.072000] TCP reno registered
[17179570.072000] audit: initializing netlink socket (disabled)
[17179570.072000] audit(1177018060.072:1): initialized
[17179570.072000] highmem bounce pool size: 64 pages
[17179570.072000] VFS: Disk quotas dquot_6.5.1
[17179570.072000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.072000] Initializing Cryptographic API
[17179570.072000] io scheduler noop registered
[17179570.072000] io scheduler anticipatory registered
[17179570.072000] io scheduler deadline registered
[17179570.072000] io scheduler cfq registered (default)
[17179570.072000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179570.072000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179570.072000] assign_interrupt_mode Found MSI capability
[17179570.072000] Allocate Port Service[0000:00:01.0:pcie00]
[17179570.072000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179570.072000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179570.072000] assign_interrupt_mode Found MSI capability
[17179570.072000] Allocate Port Service[0000:00:1c.0:pcie00]
[17179570.072000] Allocate Port Service[0000:00:1c.0:pcie02]
[17179570.072000] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 177
[17179570.072000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[17179570.072000] assign_interrupt_mode Found MSI capability
[17179570.072000] Allocate Port Service[0000:00:1c.3:pcie00]
[17179570.072000] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 169
[17179570.072000] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[17179570.072000] assign_interrupt_mode Found MSI capability
[17179570.072000] Allocate Port Service[0000:00:1c.4:pcie00]
[17179570.072000] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 17 (level, low) -> IRQ 185
[17179570.072000] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[17179570.072000] assign_interrupt_mode Found MSI capability
[17179570.072000] Allocate Port Service[0000:00:1c.5:pcie00]
[17179570.072000] isapnp: Scanning for PnP cards...
[17179570.424000] isapnp: No Plug & Play device found
[17179570.440000] Real Time Clock Driver v1.12ac
[17179570.440000] hpet_resources: 0xfed00000 is busy
[17179570.440000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179570.440000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.440000] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.440000] mice: PS/2 mouse device common for all mice
[17179570.440000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179570.440000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179570.440000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179570.440000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[17179570.444000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179570.444000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179570.444000] EISA: Probing bus 0 at eisa.0
[17179570.444000] EISA: Detected 0 cards.
[17179570.444000] TCP bic registered
[17179570.444000] NET: Registered protocol family 1
[17179570.444000] NET: Registered protocol family 8
[17179570.444000] NET: Registered protocol family 20
[17179570.444000] Starting balanced_irq
[17179570.444000] Using IPI No-Shortcut mode
[17179570.444000] ACPI: (supports S0 S1 S3 S4 S5)
[17179570.444000] Freeing unused kernel memory: 308k freed
[17179570.476000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179571.492000] Capability LSM initialized
[17179571.516000] ACPI: Processor [CPU1] (supports 8 throttling states)
[17179571.516000] ACPI: Processor [CPU2] (supports 8 throttling states)
[17179571.516000] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[17179571.516000] ACPI: Getting cpuindex for acpiid 0x3
[17179571.516000] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[17179571.516000] ACPI: Getting cpuindex for acpiid 0x4
[17179571.748000] ICH7: IDE controller at PCI slot 0000:00:1f.1
[17179571.748000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 22 (level, low) -> IRQ 50
[17179571.748000] ICH7: chipset revision 1
[17179571.748000] ICH7: not 100% native mode: will probe irqs later
[17179571.748000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[17179571.748000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:pio, hdd:pio
[17179571.748000] Probing IDE interface ide0...
[17179572.492000] hda: HL-DT-ST DVDRAM GSA-H42L, ATAPI CD/DVD-ROM drive
[17179572.840000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179572.844000] Probing IDE interface ide1...
[17179573.420000] hda: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)
[17179573.420000] Uniform CD-ROM driver Revision: 3.20
[17179573.496000] SCSI subsystem initialized
[17179573.496000] libata version 1.20 loaded.
[17179573.496000] ata_piix 0000:00:1f.2: version 1.05
[17179573.496000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 23 (level, low) -> IRQ 58
[17179573.496000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179573.496000] ata1: SATA max UDMA/133 cmd 0xE400 ctl 0xE082 bmdma 0xD880 irq 58
[17179573.496000] ata2: SATA max UDMA/133 cmd 0xE000 ctl 0xDC02 bmdma 0xD888 irq 58
[17179573.660000] ata1: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4023 85:3469 86:3c01 87:4023 88:207f
[17179573.660000] ata1: dev 0 ATA-7, max UDMA/133, 488397168 sectors: LBA48
[17179573.668000] ata1: dev 0 configured for UDMA/133
[17179573.668000] scsi0 : ata_piix
[17179573.836000] ata2: disabling port
[17179573.836000] scsi1 : ata_piix
[17179573.836000]   Vendor: ATA       Model: ST3250820AS       Rev: 3.AA
[17179573.836000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179573.836000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[17179573.836000] sda: Write Protect is off
[17179573.836000] sda: Mode Sense: 00 3a 00 00
[17179573.836000] SCSI device sda: drive cache: write back
[17179573.836000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[17179573.836000] sda: Write Protect is off
[17179573.836000] sda: Mode Sense: 00 3a 00 00
[17179573.836000] SCSI device sda: drive cache: write back
[17179573.836000]  sda: sda1 sda2
[17179573.856000] sd 0:0:0:0: Attached scsi disk sda
[17179573.988000] ahci 0000:02:00.0: version 1.2
[17179573.988000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 185
[17179578.308000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[17179578.308000] ahci 0000:02:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[17179578.308000] ahci 0000:02:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[17179578.308000] ata3: SATA max UDMA/133 cmd 0xF8868100 ctl 0x0 bmdma 0x0 irq 185
[17179578.308000] ata4: SATA max UDMA/133 cmd 0xF8868180 ctl 0x0 bmdma 0x0 irq 185
[17179578.512000] ata3: SATA link down (SStatus 0)
[17179578.512000] scsi2 : ahci
[17179578.716000] ata4: SATA link down (SStatus 0)
[17179578.716000] scsi3 : ahci
[17179578.720000] JMB361: IDE controller at PCI slot 0000:02:00.1
[17179578.720000] PCI: Enabling device 0000:02:00.1 (0000 -> 0001)
[17179578.720000] ACPI: PCI Interrupt 0000:02:00.1[B] -> GSI 16 (level, low) -> IRQ 169
[17179578.720000] JMB361: chipset revision 2
[17179578.720000] JMB361: 100% native mode on irq 169
[17179578.720000] PCI: Setting latency timer of device 0000:02:00.1 to 64
[17179578.720000]     ide2: BM-DMA at 0x9400-0x9407, BIOS settings: hde:pio, hdf:pio
[17179578.720000]     ide3: BM-DMA at 0x9408-0x940f, BIOS settings: hdg:pio, hdh:pio
[17179578.720000] Probing IDE interface ide2...
[17179579.304000] Probing IDE interface ide3...
[17179579.960000] Probing IDE interface ide1...
[17179579.968000] usbcore: registered new driver usbfs
[17179579.968000] usbcore: registered new driver hub
[17179579.968000] USB Universal Host Controller Interface driver v3.0
[17179579.968000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 66
[17179579.968000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179579.968000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179579.968000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179579.968000] uhci_hcd 0000:00:1d.0: irq 66, io base 0x0000e480
[17179579.968000] usb usb1: configuration #1 chosen from 1 choice
[17179579.968000] hub 1-0:1.0: USB hub found
[17179579.968000] hub 1-0:1.0: 2 ports detected
[17179580.000000] ieee1394: Initialized config rom entry `ip1394'
[17179580.072000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 185
[17179580.072000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179580.072000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179580.072000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179580.072000] uhci_hcd 0000:00:1d.1: irq 185, io base 0x0000e800
[17179580.072000] usb usb2: configuration #1 chosen from 1 choice
[17179580.072000] hub 2-0:1.0: USB hub found
[17179580.072000] hub 2-0:1.0: 2 ports detected
[17179580.176000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 74
[17179580.176000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179580.176000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179580.176000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179580.176000] uhci_hcd 0000:00:1d.2: irq 74, io base 0x0000e880
[17179580.176000] usb usb3: configuration #1 chosen from 1 choice
[17179580.176000] hub 3-0:1.0: USB hub found
[17179580.176000] hub 3-0:1.0: 2 ports detected
[17179580.280000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 177
[17179580.280000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179580.280000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179580.280000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179580.280000] uhci_hcd 0000:00:1d.3: irq 177, io base 0x0000ec00
[17179580.280000] usb usb4: configuration #1 chosen from 1 choice
[17179580.280000] hub 4-0:1.0: USB hub found
[17179580.280000] hub 4-0:1.0: 2 ports detected
[17179580.384000] ACPI: PCI Interrupt 0000:01:03.0[A] -> GSI 21 (level, low) -> IRQ 82
[17179580.384000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 66
[17179580.384000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179580.384000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179580.384000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179580.384000] ehci_hcd 0000:00:1d.7: debug port 1
[17179580.384000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179580.384000] ehci_hcd 0000:00:1d.7: irq 66, io mem 0xfebfbc00
[17179580.388000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179580.388000] usb usb5: configuration #1 chosen from 1 choice
[17179580.388000] hub 5-0:1.0: USB hub found
[17179580.388000] hub 5-0:1.0: 8 ports detected
[17179580.416000] usb 2-2: new low speed USB device using uhci_hcd and address 2
[17179580.432000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[82]  MMIO=[fa6ff800-fa6fffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[17179580.580000] Probing IDE interface ide2...
[17179581.052000] usb 5-7: new high speed USB device using ehci_hcd and address 3
[17179581.160000] Probing IDE interface ide3...
[17179581.188000] usb 5-7: configuration #1 chosen from 1 choice
[17179581.188000] hub 5-7:1.0: USB hub found
[17179581.188000] hub 5-7:1.0: 4 ports detected
[17179581.536000] usb 2-2: new low speed USB device using uhci_hcd and address 3
[17179581.708000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d800011bfd5e]
[17179581.712000] usb 2-2: configuration #1 chosen from 1 choice
[17179581.916000] usb 5-7.3: new high speed USB device using ehci_hcd and address 4
[17179582.016000] usb 5-7.3: configuration #1 chosen from 1 choice
[17179582.016000] usbcore: registered new driver hiddev
[17179582.028000] hiddev96: USB HID v1.10 Device [T-wins ASUS DH Remote] on usb-0000:00:1d.1-2
[17179582.028000] usbcore: registered new driver usbhid
[17179582.028000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179582.080000] Attempting manual resume
[17179582.108000] kjournald starting.  Commit interval 5 seconds
[17179582.108000] EXT3-fs: mounted filesystem with ordered data mode.
[17179588.544000] hw_random: RNG not detected
[17179588.728000] Floppy drive(s): fd0 is 1.44M
[17179588.748000] FDC 0 is a post-1991 82077
[17179588.796000] input: PC Speaker as /class/input/input1
[17179588.804000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179588.804000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179589.104000] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 19 (level, low) -> IRQ 177
[17179589.104000] PCI: Setting latency timer of device 0000:04:00.0 to 64
[17179589.104000] sky2 v1.6.1 addr 0xfa9fc000 irq 177 Yukon-EC (0xb6) rev 2
[17179589.104000] sky2 eth0: addr 00:1a:92:42:7d:98
[17179589.104000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179589.104000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[17179589.104000] sky2 v1.6.1 addr 0xfa8fc000 irq 169 Yukon-EC (0xb6) rev 2
[17179589.104000] sky2 eth1: addr 00:1a:92:42:77:c2
[17179589.336000] sky2 eth1: enabling interface
[17179589.388000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 19 (level, low) -> IRQ 177
[17179589.388000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[17179589.404000] rtl_ieee80211_crypt: registered algorithm 'NULL'
[17179589.404000] rtl_ieee80211_crypt: registered algorithm 'TKIP'
[17179589.404000] rtl_ieee80211_crypt: registered algorithm 'WEP'
[17179589.404000] rtl_ieee80211_crypt: registered algorithm 'CCMP'
[17179589.408000] 
[17179589.408000] Linux kernel driver for RTL8187 based WLAN cards
[17179589.408000] Copyright (c) 2004-2005, Andrea Merello
[17179589.408000] rtl8187: Initializing module
[17179589.408000] rtl8187: Wireless extensions version 20
[17179589.408000] rtl8187: Initializing proc filesystem
[17179589.408000] rtl8187: Reported EEPROM chip is a 93c46 (1Kbit)
[17179589.444000] sky2 eth0: enabling interface
[17179589.472000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179589.480000] Linux agpgart interface v0.101 (c) Dave Jones
[17179589.524000] rtl8187: Card MAC address is 00:15:af:0e:a2:79
[17179589.588000] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[17179589.636000] nvidia: module license 'NVIDIA' taints kernel.
[17179589.716000] rtl8187: Card reports RF frontend Realtek 8225
[17179589.716000] rtl8187: WW:This driver has EXPERIMENTAL support for this chipset.
[17179589.716000] rtl8187: WW:use it with care and at your own risk and
[17179589.716000] rtl8187: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO andreamrl@tiscali.it
[17179589.760000] rtl8187: This seems a new V2 radio
[17179589.760000] rtl8187: PAPE from CONFIG2: 0
[17179589.760000] rtl8187: Driver probe completed
[17179589.760000] 
[17179589.760000] usbcore: registered new driver rtl8187
[17179589.984000] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
[17179589.984000] ts: Compaq touchscreen protocol output
[17179590.248000] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179590.248000] PCI: Setting latency timer of device 0000:06:00.0 to 64
[17179590.248000] NVRM: loading NVIDIA UNIX x86 Kernel Module  1.0-9755  Mon Feb 26 23:21:15 PST 2007
[17179590.384000] rtl8187: Card successfully reset
[17179590.588000] lp: driver loaded but no devices found
[17179591.004000] sky2 eth1: Link is up at 100 Mbps, full duplex, flow control both
[17179591.688000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179591.688000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179591.708000] Adding 1020116k swap on /dev/disk/by-uuid/5c10f310-1b07-4079-a6af-36dbdb86a82a.  Priority:-1 extents:1 across:1020116k
[17179591.740000] EXT3 FS on sda1, internal journal
[17179595.224000] NET: Registered protocol family 17
[17179595.352000] NET: Registered protocol family 10
[17179595.352000] lo: Disabled Privacy Extensions
[17179595.352000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179595.352000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17179595.352000] IPv6 over IPv4 tunneling driver
[17179598.020000] ACPI: Power Button (FF) [PWRF]
[17179598.020000] ACPI: Power Button (CM) [PWRB]
[17179598.104000] ibm_acpi: ec object not found
[17179598.140000] pcc_acpi: loading...
[17179601.520000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179601.520000] apm: disabled - APM is not SMP safe.
[17179604.012000] Bluetooth: Core ver 2.8
[17179604.012000] NET: Registered protocol family 31
[17179604.012000] Bluetooth: HCI device and connection manager initialized
[17179604.012000] Bluetooth: HCI socket layer initialized
[17179604.048000] Bluetooth: L2CAP ver 2.8
[17179604.048000] Bluetooth: L2CAP socket layer initialized
[17179604.064000] Bluetooth: RFCOMM socket layer initialized
[17179604.064000] Bluetooth: RFCOMM TTY layer initialized
[17179604.064000] Bluetooth: RFCOMM ver 1.7
[17179605.636000] eth1: no IPv6 routers present

```

Now, that's a lot of stuff, and I'll have to be honest, i don't really understand any of it. If anyone has any ideas, I'd be very appreciative. 

Thanks.

---

### Post by lvanderree on 2007-04-26
I think I have the solution for you.

I didn't check your log file (yet), but I think I had the same problem.

first of all, I have 2 hid-devices, so to check which one is your remote, i did the following:

```
sudo cat /dev/hiddev0
```

and pressed some buttons on the remote, but nothing happend.
So I pressed CTRL+C and tried it again with hiddev1

```
sudo cat /dev/hiddev1
```
Now I did see a respons. 

starting irw after 
```
sudo /etc/init.d/lirc restart
``` 
didin't work for me either (yet ;))

What I now did was editing 
```
sudo vi /etc/lirc/hardware.conf 
```

and changed it to this:

```

# /etc/lirc/hardware.conf
#
# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
START_LIRCMD=true

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER="AsusDH"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE="/dev/hiddev1"
MODULES=""

# Default configuration files for your hardware if any
LIRCD_CONF="/etc/lircd.conf"
#LIRCMD_CONF=""

```

Pay attention to the device location!!!

restart lirc again and now it should work...

Does this help?

---

### Post by Jeffa on 2007-04-26
Getting closer!

I edited /etc/lirc/hardware.conf to match the file you posted above, but used hiddev0 instead of hiddev1. Then when i run 

```
sudo cat /dev/hiddev0
```

and press buttons, the system beeps and i get a lot of funny looking characters in the terminal. 

The LIRC documentation is a little vague. Do i now need to make a lircrc file that looks something like:

```

    begin
	prog	= amarok
	remote	= asusdh
	button	= 0x09
	config	= play
    end

    begin
	prog	= amarok
	remote	= asusdh
	button	= 0x08
	config	= rev
    end

```

and so on? How does it know what application to launch when i hit "ap launch" on the remote?

Thanks so much for your help! I've been struggling with this for quite a while. 

Jeff

---

### Post by lvanderree on 2007-04-27
Yep, now you need to edit /etc/lircd.conf to this:

```


#
# contributed by Bernhard Frauendienst <lirc|nospam.obeliks.de>
#
# brand:             Asus
# model:             Asus DH Deluxe IR
#

begin remote

  name          AsusDH
  bits          32
  pre_data_bits 32
  pre_data      0xFF000000
  post_data_bits  0

        begin codes
          POWER                 0x01
          QUICK_POWER           0x02
          NOISE_OFF             0x03
          WIFI                  0x04
          AP_LAUNCH             0x05
          MAXIMIZE              0x06
          PLUS                  0x07
          REV                   0x08
          PLAY/PAUSE            0x09
          FWD                   0x0A
          MINUS                 0x0B
        end codes

end remote


```

Which makes the remote buttons match with their signal.

when you now again run "etc/init.d/lirc restart" and start irw you should see the output of you pressing on buttons of the remote.

To attach actions on these buttons you can edit the ~/.lircrc file, but I think this is not the nicest way to do so. Actually I didn't want to take a look at finding application actions. I just installed the kde application kdelirc which als integrates nicely in gnome I think. You can start it with klirc and the rest speaks for itself I think.

Good luck

---

### Post by Tompalaz on 2007-11-11
> **RapMan said:**
> If you download and unpack [this]("http://lirc.sourceforge.net/software/snapshots/lirc-0.8.2pre1.tar.bz2"), then run ./setup.sh as root, you can choose the Asus DH driver (from USB drivers I think), then copy the config file for Asus DH remote.
Maybe you will have the same problem as me, I had to also specify my device when running lircd daemon. Becouse lircd thinks, that the device is something like /dev/usb/hiddev0 , but in (k)ubuntu is it only /dev/hiddev0 , so you have to run lircd --device=/dev/hiddev0 or specify this device in hardware.conf I think.
I can't have a look now, becouse I am not on my computer.
My config files seems do match yours, bit it still doesn't work, do i have to run irw to use the remote?

my /etc/lirc/hardware.conf look like this:
```
# /etc/lirc/hardware.conf
#
# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
START_LIRCMD=true

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER="AsusDH"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE="/dev/hiddev0"
MODULES=""

# Default configuration files for your hardware if any
LIRCD_CONF="/etc/lircd.conf"
#LIRCMD_CONF=""
```

and my lrcd.conf

```
#
# contributed by Bernhard Frauendienst <lirc|nospam.obeliks.de>
#
# brand:             Asus
# model:             Asus DH Deluxe IR
#

begin remote

  name          AsusDH
  bits          32
  pre_data_bits 32
  pre_data      0xFF000000
  post_data_bits  0

        begin codes
          POWER                 0x01
          QUICK_POWER           0x02
          NOISE_OFF             0x03
          WIFI                  0x04
          AP_LAUNCH             0x05
          MAXIMIZE              0x06
          PLUS                  0x07
          REV                   0x08
          PLAY/PAUSE            0x09
          FWD                   0x0A
          MINUS                 0x0B
        end codes

end remote
```

---

### Post by lvanderree on 2007-11-11
Since Gutsy you don't have to compile anything anymore, installing lirc should be enough to be able to select the Asus DH USB Remote.
```

sudo apt-get install lirc

```

My /etc/lirc/hardware.conf is (I thought from the setup):
```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Asus DH USB Remote"

# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER="asusdh"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE=""
MODULES=""

# Default configuration files for your hardware if any
LIRCD_CONF="asus/lircd.conf.asusdh"
LIRCMD_CONF=""


```


My /etc/lirc/lircd.conf is:
```

#
# contributed by Bernhard Frauendienst <lirc|nospam.obeliks.de>
# 
# brand:             Asus
# model:             Asus DH Deluxe IR
#

begin remote

  name          AsusDH
  bits          32
  pre_data_bits 32
  pre_data      0xFF000000
  post_data_bits  0

        begin codes
          POWER                 0x01
          QUICK_POWER           0x02
          NOISE_OFF             0x03
          WIFI                  0x04
          AP_LAUNCH             0x05
          MAXIMIZE              0x06
          PLUS                  0x07
          REV                   0x08
          PLAY/PAUSE            0x09
          FWD                   0x0A
          MINUS                 0x0B
        end codes

end remote

```

finally you have to setup a .lircrc file in your home folder, I have attached mine (remove the .txt extention!), which can control amarok, totem and others (in rhythmbox you might have to enable a plugin, but this works as well).

You possible have to restart lircd and re-login before things work.

---

### Post by Tompalaz on 2007-11-12
Thank you!
Though it seems as amaroK don't "answer" to the remote.
I can boot the computer, at least i could do it twice today, but when i came home from school it didn't whant to boot, could it be cuz i used the power button to turn it off?

Do you have to do anything with amarok to get it to work? Like the global shortcuts?

---

### Post by lvanderree on 2007-11-12
Ah yes, for amarok, I use the application irexec (this is installed with lirc) but which requires an extra bash-script, which I also called irexec placed in my home folder, containing:

```

#/bin/sh

irexec -d ~/.lircrc
exit 0

```

this runs in daemon mode (I think I added it to my session applications to start up automatically (not at home right now, so can't check))

this is used to execute dcop commands to control amarok.

Booting your computer with the remote has nothing to do with linux/ubuntu. You should have the remote connected  to the green usb-port at the back of your pc, but it can possibly have something to do with the way you shutdown your computer (so holding the power button probably can brake it).

Check the lirc manual to see how you should change the .lircrc file to your like: [http://www.lirc.org/html/configure.html#lircrc_format](http://www.lirc.org/html/configure.html#lircrc_format)
If you have nice additions (for example how to change the overal volume) please share it with everyone ;)

---

### Post by Tompalaz on 2007-11-14
Thanks for your reply.
I don't get amarok to work with the remote. I tried your script

#/bin/sh

irexec -d ~/.lircrc
exit 0

and then save as irexec.? 
Should i run it in the terminal?
Sorry for maybe misunderstanding you

---

### Post by lvanderree on 2007-11-14
The only thing the script does is starting irexec as a daemon application (running in the background) listering at commands from lirc.

So if you want to start it from the terminal, would be the same as starting: 
irexec -d ~/.lircrc 

from the terminal. You can do this to test your .lircrc configuration with amarok.

The thing is you don't want to start irexec -d ~/.lircrc everytime you rebooted your computer and logged in. So that's why I created this script. You can add this script to your session-applications, so it automatically starts when you login in gnome. To do this, you have to go to System\preferences\sessions (I think, I've got the dutch translation, so I can be wrong...) Here you can add an application, which gets started automatically when you login, so give it a name, and point to the script you have created and everything should work everytime you login.

---

### Post by Tompalaz on 2007-11-30
Hello again, i found a program that lets you configure EVERYTHING to your remote, without any scripts.

Download IRkick witch is a frontend GUI program to lirc. I could increase and decrease the volume. I can do everything i want, just one problem, probably an easy one. 
Play/Pause can just be assigned one of those options either play or pause though im happy it work better that ever :D:guitar:

Edit: i fixed the play/pause thing, you can add everything to anything in amarok or other applications
Edit2: upload a img link so you can see how it works. Though i don't know the command to execute it, i suppose it's irkick

---

### Post by andymushu on 2007-12-26
thanks tompalaz for that irkick suggestion, it makes configuring the remote very easy. One thing i could not figure out how to do in irkick was shutdown the computer. Could anyone please tell me how to configure my remote to shutdown when i hit the power button and reboot when i hit the quick power button?

---

### Post by Tompalaz on 2007-12-26
> **andymushu said:**
> thanks tompalaz for that irkick suggestion, it makes configuring the remote very easy. One thing i could not figure out how to do in irkick was shutdown the computer. Could anyone please tell me how to configure my remote to shutdown when i hit the power button and reboot when i hit the quick power button?

You can make a script, but i don't know how this should look like
maybe:
> #!/bin/sh
$ sudo shutdown -h now to shutdown now
or
$ sudo shutdown -r now to restart

?
then you can give the quick power button a path to the script



Just press  Add - KDE Program Launcher
next
choose Quick_Power
next
Perform a function in the application
Then there seems to be a way to give a location to a script.
I don't know if this work though.

---

### Post by andymushu on 2007-12-26
thanks for the quick reply. i tried to map the buttons to those scripts, but it seems the issue is the sudo part. I have to enter the sudo password in order to shutdown. is there any way to make it not ask for a password to shutdown or reboot?

---

### Post by Tompalaz on 2007-12-26
I tried to google for answers, the best thing i could came up with was something like this:

{user}ALL=NOPASSWD: /way/to/shutdowns/script
i didn't get it to work though, i suggest you ask in the programming section.
(please give me the answer if you find it ^^ )

---

### Post by andymushu on 2007-12-26
thanks for the help. i did end up getting it. first, i chmodded the shutdown script with this command: ```
sudo chmod +s /sbin/shutdown
```

that took away the need for a sudo when you run the shutdown command. then i wrote a very simple script in my home directory called shutdown_script. this text file only contained the command ```
shutdown -h now
``` i then gave the script executable permissions with ```
sudo chmod +x shutdown_script
```next, in irkick, i added a new function for the power button, assigned the function to kde program launcher, clicked the "execute and wait" option, then selected the "executable name and path of the program or script to run" option. then in the bottom text field i just typed in the path of the script, in this case /home/andy/shutdown_script. that's pretty much it. thanks for your help, it was instrumental in getting this to work. 

if you want to use this for rebooting, just make another script, and in it type ```
shutdown -r now
``` then just follow the rest of the above steps.

---

### Post by Tompalaz on 2007-12-26
Great that you got it to work!

---

