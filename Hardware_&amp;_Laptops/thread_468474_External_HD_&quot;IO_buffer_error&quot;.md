---
title: "External HD &quot;I/O buffer error&quot;"
date: 2007-06-08
forum: Hardware &amp; Laptops
---

### Post by maluze on 2007-06-08
Ok, I am running Ubuntu Fiesty, and I recently purchased a Seagate 160Gb external Hard drive, which is connected via USB 2.0 and has a separate external power supply. I had problems with mounting, and practically begged for help here, but got no reply. But anyway, i did a google search on the problem, and it appeared to be a problem with the motherboard, and running rmmod ehci-hd seemed to do the trick. Yesterday, however, I turned my external HD on, and left it on for almost 24 hours. Everything was fine, until i realized that the hard drive was no longer showing up, and it mentioned in sys log something referring to a I/O buffer error, at which point it dismounted. Subsequent attempts to recreate the I/O error message did not result in a I/O error message, but the onlyrelevant message I got was this:

"USB 4-1 can't set config #1, error #32". 

Again, this seems seems to be Ubuntu/Linux specific, becuase i hooked it up to my sisters' laptop and everything was swell, without a hitch. Can anyone help me out here? pretty please? what do I have to do to get help around here???

---

### Post by maluze on 2007-06-09
> **maluze said:**
> Ok, I am running Ubuntu Fiesty, and I recently purchased a Seagate 160Gb external Hard drive, which is connected via USB 2.0 and has a separate external power supply. I had problems with mounting, and practically begged for help here, but got no reply. But anyway, i did a google search on the problem, and it appeared to be a problem with the motherboard, and running rmmod ehci-hd seemed to do the trick. Yesterday, however, I turned my external HD on, and left it on for almost 24 hours. Everything was fine, until i realized that the hard drive was no longer showing up, and it mentioned in sys log something referring to a I/O buffer error, at which point it dismounted. Subsequent attempts to recreate the I/O error message did not result in a I/O error message, but the onlyrelevant message I got was this:

"USB 4-1 can't set config #1, error #32". 

Again, this seems seems to be Ubuntu/Linux specific, becuase i hooked it up to my sisters' laptop and everything was swell, without a hitch. Can anyone help me out here? pretty please? what do I have to do to get help around here???

*bump*...

on another note, i did this post becuase my hard drive does not mount...im thinking of just getting all the stuff off the hard drive and just reformatting it to ext3...that would make my life so much easier :P; but in the meantime, i need help! :(

---

### Post by maluze on 2007-06-10
I seriosuly think its a linux issue (or at least a motherboard issue), becuase I transferred all the files off the hard drive, reformatted it to FAT32, ubuntu didnt mount it, I reformatted to ext3, my ubuntu didnt mount it!...I hoped wiping out everything on the HD would make everything alright, but it didnt...I'm really up in arms over what to do now...can anyone suggest anything? anyone?...there must be someone here who can help me out :cry: 

(on a side note, my windows partition on my boot hard drive no longer works, it worked until a week or so ago, and stopped working magically, so i cant tell if its linux or a motherboard issue)...

for reference, here is the output of the dmesg command (my hard drive is Seagate ST316002 3A, for reference)

> [    0.000000] Detected 2699.830 MHz processor.
[   59.662111] Built 1 zonelists.  Total pages: 62802
[   59.662116] Kernel command line: root=UUID=cd9d6e01-1edb-4705-910c-4805c3712da7 ro single
[   59.662276] mapped APIC to ffffd000 (fee00000)
[   59.662279] mapped IOAPIC to ffffc000 (fec00000)
[   59.662282] Enabling fast FPU save and restore... done.
[   59.662287] Enabling unmasked SIMD FPU exception support... done.
[   59.662296] Initializing CPU#0
[   59.662373] PID hash table entries: 1024 (order: 10, 4096 bytes)
[   59.663891] Console: colour VGA+ 80x25
[   59.666255] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[   59.666562] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[   59.672579] Memory: 239928k/253184k available (1992k kernel code, 12636k reserved, 896k data, 328k init, 0k highmem)
[   59.672655] virtual kernel memory layout:
[   59.672656]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   59.672657]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   59.672658]     vmalloc : 0xd0000000 - 0xff7fe000   ( 759 MB)
[   59.672659]     lowmem  : 0xc0000000 - 0xcf740000   ( 247 MB)
[   59.672660]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   59.672661]       .data : 0xc02f2354 - 0xc03d26d4   ( 896 kB)
[   59.672662]       .text : 0xc0100000 - 0xc02f2354   (1992 kB)
[   59.673033] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   59.750313] Calibrating delay using timer specific routine.. 5403.98 BogoMIPS (lpj=10807972)
[   59.750461] Security Framework v1.0.0 initialized
[   59.750518] SELinux:  Disabled at boot.
[   59.750586] Mount-cache hash table entries: 512
[   59.750850] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[   59.750867] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   59.750951] CPU: L2 cache: 128K
[   59.750997] CPU: Hyper-Threading is disabled
[   59.751044] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003080 00004400 00000000 00000000
[   59.751061] Compat vDSO mapped to ffffe000.
[   59.751111] Remapping vsyscall page to ffffe000
[   59.751173] Checking 'hlt' instruction... OK.
[   59.766488] SMP alternatives: switching to UP code
[   59.766955] Freeing SMP alternatives: 11k freed
[   59.767321] Early unpacking initramfs... done
[   60.083811] ACPI: Core revision 20060707
[   60.084065] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   60.086411] CPU0: Intel(R) Celeron(R) CPU 2.70GHz stepping 09
[   60.086576] Total of 1 processors activated (5403.98 BogoMIPS).
[   60.086765] ENABLING IO-APIC IRQs
[   60.087009] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   60.234039] Brought up 1 CPUs
[   60.234445] Booting paravirtualized kernel on bare hardware
[   60.234660] Time: 22:09:52  Date: 05/09/107
[   60.234759] NET: Registered protocol family 16
[   60.235022] EISA bus registered
[   60.235083] ACPI: bus type pci registered
[   60.235239] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[   60.235290] PCI: Using configuration type 1
[   60.235335] Setting up standard PCI resources
[   60.250521] ACPI: Interpreter enabled
[   60.250581] ACPI: Using IOAPIC for interrupt routing
[   60.251572] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   60.251635] PCI: Probing PCI hardware (bus 00)
[   60.252094] Boot video device is 0000:00:02.0
[   60.252392] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[   60.252394] * this clock source is slow. If you are sure your timer does not have
[   60.252395] * this bug, please use "acpi_pm_good" to disable the workaround
[   60.252607] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[   60.252659] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[   60.253144] PCI: Firmware left 0000:01:08.0 e100 interrupts enabled, disabling
[   60.253280] PCI: Transparent bridge - 0000:00:1e.0
[   60.253364] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   60.256409] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   60.260607] ACPI: Power Resource [URP1] (off)
[   60.260846] ACPI: Power Resource [FDDP] (off)
[   60.261088] ACPI: Power Resource [LPTP] (off)
[   60.265423] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   60.266507] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[   60.267493] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   60.268473] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   60.269470] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   60.270552] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   60.271535] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   60.272570] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   60.273578] Linux Plug and Play Support v0.97 (c) Adam Belay
[   60.273652] pnp: PnP ACPI init
[   60.280411] pnp: PnP ACPI: found 14 devices
[   60.280473] PnPBIOS: Disabled by ACPI PNP
[   60.280639] PCI: Using ACPI for IRQ routing
[   60.280694] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   60.284168] NET: Registered protocol family 8
[   60.284219] NET: Registered protocol family 20
[   60.285656] pnp: 00:0c: ioport range 0x400-0x47f could not be reserved
[   60.285715] pnp: 00:0c: ioport range 0x680-0x6ff has been reserved
[   60.285765] pnp: 00:0c: ioport range 0x480-0x4bf has been reserved
[   60.286790] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[   60.286859] PCI: Bridge: 0000:00:1e.0
[   60.286906]   IO window: d000-dfff
[   60.286955]   MEM window: ff800000-ff8fffff
[   60.287005]   PREFETCH window: dea00000-deafffff
[   60.287065] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   60.287112] NET: Registered protocol family 2
[   60.322024] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[   60.322223] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[   60.322349] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[   60.322438] TCP: Hash tables configured (established 8192 bind 4096)
[   60.322491] TCP reno registered
[   60.334089] checking if image is initramfs... it is
[   60.938334] Freeing initrd memory: 6751k freed
[   60.939393] audit: initializing netlink socket (disabled)
[   60.939466] audit(1181426993.356:1): initialized
[   60.939812] VFS: Disk quotas dquot_6.5.1
[   60.939894] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   60.940041] io scheduler noop registered
[   60.940129] io scheduler anticipatory registered
[   60.940208] io scheduler deadline registered
[   60.940313] io scheduler cfq registered (default)
[   68.939320] 0000:00:1d.7 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[   68.939954] isapnp: Scanning for PnP cards...
[   69.293910] isapnp: No Plug & Play device found
[   69.420785] Real Time Clock Driver v1.12ac
[   69.420972] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   69.421236] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   69.423395] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   69.424210] mice: PS/2 mouse device common for all mice
[   69.425883] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   69.426299] input: Macintosh mouse button emulation as /class/input/input0
[   69.426462] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   69.426518] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   69.427067] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   69.430178] serio: i8042 KBD port at 0x60,0x64 irq 1
[   69.430235] serio: i8042 AUX port at 0x60,0x64 irq 12
[   69.430625] EISA: Probing bus 0 at eisa.0
[   69.430715] EISA: Detected 0 cards.
[   69.460876] TCP cubic registered
[   69.460944] NET: Registered protocol family 1
[   69.461030] Using IPI No-Shortcut mode
[   69.461251] ACPI: (supports S0 S1 S3 S4 S5)
[   69.461556]   Magic number: 11:625:198
[   69.461691]   hash matches device ttypd
[   69.462395] Freeing unused kernel memory: 328k freed
[   69.463129] Time: tsc clocksource has been installed.
[   69.519048] input: AT Translated Set 2 keyboard as /class/input/input1
[   69.791917] Capability LSM initialized
[   69.875622] ACPI: Processor [CPU1] (supports 8 throttling states)
[   69.875760] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   70.897345] usbcore: registered new interface driver usbfs
[   70.897449] usbcore: registered new interface driver hub
[   70.897560] usbcore: registered new device driver usb
[   70.898907] USB Universal Host Controller Interface driver v3.0
[   70.899058] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   70.899165] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   70.899170] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   70.899433] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   70.899536] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000e800
[   70.899764] usb usb1: configuration #1 chosen from 1 choice
[   70.899861] hub 1-0:1.0: USB hub found
[   70.899924] hub 1-0:1.0: 2 ports detected
[   70.997042] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI
[   70.997102] e100: Copyright(c) 1999-2006 Intel Corporation
[   71.005971] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   71.006094] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   71.006099] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   71.006203] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   71.006296] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000e880
[   71.006512] usb usb2: configuration #1 chosen from 1 choice
[   71.006619] hub 2-0:1.0: USB hub found
[   71.006682] hub 2-0:1.0: 2 ports detected
[   71.114001] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   71.114116] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   71.114121] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   71.114226] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   71.114321] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ec00
[   71.114540] usb usb3: configuration #1 chosen from 1 choice
[   71.114645] hub 3-0:1.0: USB hub found
[   71.114710] hub 3-0:1.0: 2 ports detected
[   71.132196] Floppy drive(s): fd0 is 1.44M
[   71.207918] FDC 0 is a National Semiconductor PC87306
[   71.222049] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[   71.222172] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   71.222177] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   71.222300] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   71.222415] ehci_hcd 0000:00:1d.7: debug port 1
[   71.222471] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   71.222488] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xffa7fc00
[   71.226417] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   71.226622] usb usb4: configuration #1 chosen from 1 choice
[   71.226724] hub 4-0:1.0: USB hub found
[   71.226790] hub 4-0:1.0: 6 ports detected
[   71.335756] ICH4: IDE controller at PCI slot 0000:00:1f.1
[   71.335823] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   71.335878] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   71.335980] ICH4: chipset revision 1
[   71.336025] ICH4: not 100% native mode: will probe irqs later
[   71.336085]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[   71.336224]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:DMA
[   71.336355] Probing IDE interface ide0...
[   71.577320] usb 4-4: new high speed USB device using ehci_hcd and address 2
[   71.625430] hda: WDC WD400EB-11CPF0, ATA DISK drive
[   71.714494] usb 4-4: configuration #1 chosen from 2 choices
[   71.957020] usb 4-6: new high speed USB device using ehci_hcd and address 3
[   72.088928] usb 4-6: device descriptor read/64, error -71
[   72.301903] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   72.326316] Probing IDE interface ide1...
[   72.476633] usb 4-6: device descriptor read/64, error -71
[   72.692469] usb 4-6: new high speed USB device using ehci_hcd and address 4
[   73.064345] hdc: HL-DT-ST GCE-8400B, ATAPI CD/DVD-ROM drive
[   73.232072] usb 4-6: device descriptor read/64, error -71
[   73.851753] hdd: DVD-ROM DDU1621, ATAPI CD/DVD-ROM drive
[   73.911852] ide1 at 0x170-0x177,0x376 on irq 15
[   73.922935] SCSI subsystem initialized
[   73.932437] libata version 2.20 loaded.
[   73.936222] ACPI: PCI Interrupt 0000:01:08.0[A] -> GSI 20 (level, low) -> IRQ 20
[   73.966363] e100: eth0: e100_probe: addr 0xff8cf000, irq 20, MAC addr 00:0C:F1:B2:5B:3C
[   73.979351] hda: max request size: 128KiB
[   74.000567] hda: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[   74.000775] hda: cache flushes not supported
[   74.000887]  hda: hda1 hda2 hda3 < hda5 >
[   74.050269] hdc: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache, DMA
[   74.050574] Uniform CD-ROM driver Revision: 3.20
[   74.052455] hdd: ATAPI 40X DVD-ROM drive, 512kB Cache, UDMA(33)
[   74.398738] Attempting manual resume
[   74.398793] swsusp: Resume From Partition 3:5
[   74.398795] PM: Checking swsusp image.
[   74.398978] PM: Resume from disk failed.
[   74.452320] kjournald starting.  Commit interval 5 seconds
[   74.452404] EXT3-fs: mounted filesystem with ordered data mode.
[   88.436431] usb 4-6: device descriptor read/64, error -110
[   88.652273] usb 4-6: new high speed USB device using ehci_hcd and address 5
[   98.360618] Linux agpgart interface v0.102 (c) Dave Jones
[   98.439629] iTCO_vendor_support: vendor-support=0
[   98.525877] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   98.526185] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460)
[   98.526344] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   98.584099] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   98.586698] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   98.725616] agpgart: Detected an Intel 845G Chipset.
[   98.725802] agpgart: Detected 8060K stolen memory.
[   98.743036] agpgart: AGP aperture is 128M @ 0xf0000000
[   98.828414] intel_rng: Firmware space is locked read-only. If you can't or
[   98.828418] intel_rng: don't want to disable this in firmware setup, and if
[   98.828419] intel_rng: you are certain that your system has a functional
[   98.828421] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   98.840684] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
[   98.863152] input: PC Speaker as /class/input/input2
[   99.052329] usb 4-6: device not accepting address 5, error -110
[   99.063034] parport: PnPBIOS parport detected.
[   99.063167] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   99.164275] usb 4-6: new high speed USB device using ehci_hcd and address 6
[   99.650917] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 21
[   99.651068] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   99.971609] intel8x0_measure_ac97_clock: measured 58983 usecs
[   99.971673] intel8x0: clocking to 48000
[  100.076799] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[  109.564278] usb 4-6: device not accepting address 6, error -110
[  109.564440] usbcore: registered new interface driver libusual
[  109.782215] lp0: using parport0 (interrupt-driven).
[  109.820110] usb 4-4: USB disconnect, address 2
[  109.910513] fuse init (API version 7.8)
[  109.932060] usb 4-4: new high speed USB device using ehci_hcd and address 7
[  109.975927] Adding 224868k swap on /dev/disk/by-uuid/85ee343a-2d21-4461-a02a-3f7ee7264bc4.  Priority:-1 extents:1 across:224868k
[  110.065244] usb 4-4: configuration #1 chosen from 2 choices
[  110.112934] Initializing USB Mass Storage driver...
[  110.113126] scsi0 : SCSI emulation for USB Mass Storage devices
[  110.113233] usb-storage: device found at 7
[  110.113236] usb-storage: waiting for device to settle before scanning
[  110.113256] usbcore: registered new interface driver usb-storage
[  110.113261] USB Mass Storage support registered.
[  110.189165] EXT3 FS on hda2, internal journal
[  112.389768] NET: Registered protocol family 17
[  114.930734] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[  115.035855] ndiswrapper: driver mrv8000c (Marvell,09/17/2004,3.1.0.19) loaded
[  115.036236] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 21 (level, low) -> IRQ 22
[  115.038053] ndiswrapper: using IRQ 22
[  115.112270] usb-storage: device scan complete
[  115.112770] scsi 0:0:0:0: Direct-Access     Apple    iPod             2.70 PQ: 0 ANSI: 2
[  115.156331] SCSI device sda: 495616 2048-byte hdwr sectors (1015 MB)
[  115.156944] sda: Write Protect is off
[  115.156948] sda: Mode Sense: 64 00 00 08
[  115.156950] sda: assuming drive cache: write through
[  115.158693] SCSI device sda: 495616 2048-byte hdwr sectors (1015 MB)
[  115.159316] sda: Write Protect is off
[  115.159320] sda: Mode Sense: 64 00 00 08
[  115.159322] sda: assuming drive cache: write through
[  115.159378]  sda: unknown partition table
[  115.184648] sd 0:0:0:0: Attached scsi removable disk sda
[  115.200201] sd 0:0:0:0: Attached scsi generic sg0 type 0
[  115.591807] wlan0: ethernet device 00:14:6c:71:c7:6d using NDIS driver: mrv8000c, version: 0x3000027, NDIS version: 0x501, vendor: '', 11AB:1FAA.5.conf
[  115.591827] ndiswrapper (set_encr_mode:694): setting encryption mode to 6 failed (C00000BB)
[  115.591833] wlan0: encryption modes supported: WEP; TKIP with WPA
[  123.839657] usbcore: registered new interface driver ndiswrapper
[  177.822167] NET: Registered protocol family 10
[  177.822353] lo: Disabled Privacy Extensions
[  177.822439] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  194.593638] input: Power Button (FF) as /class/input/input4
[  194.600941] ACPI: Power Button (FF) [PWRF]
[  194.641034] input: Sleep Button (CM) as /class/input/input5
[  194.648410] ACPI: Sleep Button (CM) [SLPB]
[  194.672738] Using specific hotkey driver
[  194.712922] No dock devices found.
[  194.773055] ibm_acpi: ec object not found
[  194.958013] pcc_acpi: loading...
[  202.327164] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  203.781799] ppdev: user-space parallel port driver
[  203.808972] [drm] Initialized drm 1.1.0 20060810
[  203.814552] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[  203.815786] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  206.100196] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  206.100204] apm: overridden by ACPI.
[  206.911913] Bluetooth: Core ver 2.11
[  206.912032] NET: Registered protocol family 31
[  206.912036] Bluetooth: HCI device and connection manager initialized
[  206.912041] Bluetooth: HCI socket layer initialized
[  206.979981] Bluetooth: L2CAP ver 2.8
[  206.979987] Bluetooth: L2CAP socket layer initialized
[  207.118157] Bluetooth: RFCOMM socket layer initialized
[  207.118185] Bluetooth: RFCOMM TTY layer initialized
[  207.118188] Bluetooth: RFCOMM ver 1.8
[  726.964805] usb 4-4: USB disconnect, address 7
[  726.988586] scsi 0:0:0:0: rejecting I/O to dead device
[  726.988609] scsi 0:0:0:0: rejecting I/O to dead device
[  726.988616] scsi 0:0:0:0: rejecting I/O to dead device
[  726.988621] scsi 0:0:0:0: rejecting I/O to dead device
[  726.988627] sda : READ CAPACITY failed.
[  726.988628] sda : status=0, message=00, host=1, driver=00 
[  726.988630] sda : sense not available. 
[  726.988635] scsi 0:0:0:0: rejecting I/O to dead device
[  726.988641] sda: Write Protect is off
[  726.988643] sda: Mode Sense: 00 00 00 00
[  726.988646] sda: assuming drive cache: write through
[  726.988655] scsi 0:0:0:0: rejecting I/O to dead device
[  726.988675] scsi 0:0:0:0: rejecting I/O to dead device
[  726.988683] scsi 0:0:0:0: rejecting I/O to dead device
[  726.988689] scsi 0:0:0:0: rejecting I/O to dead device
[  726.988694] scsi 0:0:0:0: rejecting I/O to dead device
[  726.988699] sda : READ CAPACITY failed.
[  726.988700] sda : status=0, message=00, host=1, driver=00 
[  726.988702] sda : sense not available. 
[  726.988706] scsi 0:0:0:0: rejecting I/O to dead device
[  726.988709] sda: Write Protect is off
[  726.988712] sda: Mode Sense: 00 00 00 00
[  726.988714] sda: assuming drive cache: write through
[  726.994471] scsi 0:0:0:0: rejecting I/O to dead device
[  802.634700] usb 4-4: new high speed USB device using ehci_hcd and address 8
[  802.767846] usb 4-4: configuration #1 chosen from 2 choices
[  802.768310] scsi1 : SCSI emulation for USB Mass Storage devices
[  802.768463] usb-storage: device found at 8
[  802.768467] usb-storage: waiting for device to settle before scanning
[  802.882517] usb 4-6: new high speed USB device using ehci_hcd and address 9
[  803.773838] usb 4-6: device descriptor read/64, error -71
[  807.079309] usb 4-6: device descriptor read/64, error -71
[  807.295141] usb 4-6: new high speed USB device using ehci_hcd and address 10
[  807.767035] usb-storage: device scan complete
[  807.768403] scsi 1:0:0:0: Direct-Access     Apple    iPod             2.70 PQ: 0 ANSI: 2
[  807.772389] SCSI device sda: 495616 2048-byte hdwr sectors (1015 MB)
[  807.774544] sda: Write Protect is off
[  807.774554] sda: Mode Sense: 64 00 00 08
[  807.774557] sda: assuming drive cache: write through
[  807.778738] SCSI device sda: 495616 2048-byte hdwr sectors (1015 MB)
[  807.780234] sda: Write Protect is off
[  807.780243] sda: Mode Sense: 64 00 00 08
[  807.780246] sda: assuming drive cache: write through
[  807.780252]  sda: unknown partition table
[  807.805305] sd 1:0:0:0: Attached scsi removable disk sda
[  807.805397] sd 1:0:0:0: Attached scsi generic sg0 type 0
[  808.454258] usb 4-6: device descriptor read/64, error -71
[  809.773256] usb 4-6: device descriptor read/64, error -71
[  809.989092] usb 4-6: new high speed USB device using ehci_hcd and address 11
[  810.708541] usb 4-6: device not accepting address 11, error -71
[  810.820477] usb 4-6: new high speed USB device using ehci_hcd and address 12
[  811.447972] usb 4-6: device not accepting address 12, error -71
[ 1657.329679] usb 4-4: USB disconnect, address 8
[ 1659.027268] scsi 1:0:0:0: rejecting I/O to dead device
[ 4622.367953] usb 4-4: new high speed USB device using ehci_hcd and address 13
[ 4622.503038] usb 4-4: configuration #1 chosen from 1 choice
[ 4622.503664] scsi2 : SCSI emulation for USB Mass Storage devices
[ 4622.504028] usb-storage: device found at 13
[ 4622.504032] usb-storage: waiting for device to settle before scanning
[ 4627.500350] usb-storage: device scan complete
[ 4628.133998] scsi 2:0:0:0: Direct-Access     ST316002 3A               8.01 PQ: 0 ANSI: 0
[ 4628.137578] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[ 4628.138592] sda: Write Protect is off
[ 4628.138600] sda: Mode Sense: 10 00 00 00
[ 4628.138603] sda: assuming drive cache: write through
[ 4628.139742] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[ 4628.140840] sda: Write Protect is off
[ 4628.140848] sda: Mode Sense: 10 00 00 00
[ 4628.140851] sda: assuming drive cache: write through
[ 4628.140858]  sda: sda1
[ 4628.150131] sd 2:0:0:0: Attached scsi disk sda
[ 4628.150210] sd 2:0:0:0: Attached scsi generic sg0 type 0
[ 4873.456128] usb 4-4: USB disconnect, address 13
[ 5843.534863] usb 4-4: new high speed USB device using ehci_hcd and address 14
[ 5843.686139] usb 4-4: configuration #1 chosen from 1 choice
[ 5843.686946] scsi3 : SCSI emulation for USB Mass Storage devices
[ 5843.687387] usb-storage: device found at 14
[ 5843.687392] usb-storage: waiting for device to settle before scanning
[ 5848.687210] usb-storage: device scan complete
[ 5849.321481] scsi 3:0:0:0: Direct-Access     ST316002 3A               8.01 PQ: 0 ANSI: 0
[ 5849.326185] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[ 5849.327204] sda: Write Protect is off
[ 5849.327213] sda: Mode Sense: 10 00 00 00
[ 5849.327215] sda: assuming drive cache: write through
[ 5849.328477] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[ 5849.329573] sda: Write Protect is off
[ 5849.329582] sda: Mode Sense: 10 00 00 00
[ 5849.329585] sda: assuming drive cache: write through
[ 5849.329591]  sda: sda1
[ 5849.352233] sd 3:0:0:0: Attached scsi disk sda
[ 5849.352313] sd 3:0:0:0: Attached scsi generic sg0 type 0
[ 5882.345101] ehci_hcd 0000:00:1d.7: remove, state 1
[ 5882.345267] usb usb4: USB disconnect, address 1
[ 5882.345272] usb 4-4: USB disconnect, address 14
[ 5882.353131] ehci_hcd 0000:00:1d.7: USB bus 4 deregistered
[ 5882.355720] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
[ 5882.632953] usb 2-2: new full speed USB device using uhci_hcd and address 2
[ 5882.808924] usb 2-2: configuration #1 chosen from 1 choice
[ 5882.812054] scsi4 : SCSI emulation for USB Mass Storage devices
[ 5882.812778] usb-storage: device found at 2
[ 5882.812786] usb-storage: waiting for device to settle before scanning
[ 5887.811005] usb-storage: device scan complete
[ 5888.449401] scsi 4:0:0:0: Direct-Access     ST316002 3A               8.01 PQ: 0 ANSI: 0
[ 5888.455364] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[ 5888.460367] sda: Write Protect is off
[ 5888.460377] sda: Mode Sense: 10 00 00 00
[ 5888.460379] sda: assuming drive cache: write through
[ 5888.465390] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[ 5888.470348] sda: Write Protect is off
[ 5888.470357] sda: Mode Sense: 10 00 00 00
[ 5888.470359] sda: assuming drive cache: write through
[ 5888.470367]  sda: sda1
[ 5888.500535] sd 4:0:0:0: Attached scsi disk sda
[ 5888.500611] sd 4:0:0:0: Attached scsi generic sg0 type 0
[ 5926.715306] usb 2-2: USB disconnect, address 2
[ 5936.619699] usb 3-1: new full speed USB device using uhci_hcd and address 2
[ 5936.787666] usb 3-1: configuration #1 chosen from 1 choice
[ 5936.790747] scsi5 : SCSI emulation for USB Mass Storage devices
[ 5936.791021] usb-storage: device found at 2
[ 5936.791025] usb-storage: waiting for device to settle before scanning
[ 5941.789729] usb-storage: device scan complete
[ 5942.427444] scsi 5:0:0:0: Direct-Access     ST316002 3A               8.01 PQ: 0 ANSI: 0
[ 5942.434074] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[ 5942.439084] sda: Write Protect is off
[ 5942.439093] sda: Mode Sense: 10 00 00 00
[ 5942.439095] sda: assuming drive cache: write through
[ 5942.444063] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[ 5942.449068] sda: Write Protect is off
[ 5942.449077] sda: Mode Sense: 10 00 00 00
[ 5942.449079] sda: assuming drive cache: write through
[ 5942.449087]  sda: sda1
[ 5942.475251] sd 5:0:0:0: Attached scsi disk sda
[ 5942.475334] sd 5:0:0:0: Attached scsi generic sg0 type 0
justin@justin-desktop:~$ 


---

### Post by bluknight on 2007-06-10
> **maluze said:**
> Ok, I am running Ubuntu Fiesty, and I recently purchased a Seagate 160Gb external Hard drive, which is connected via USB 2.0 and has a separate external power supply. I had problems with mounting, and practically begged for help here, but got no reply. <snip>Can anyone help me out here? pretty please? what do I have to do to get help around here???

OK Im yr first customer. I have success installing 6.10 (Edgy) on my external USB - Hardrive because (I think) it doesn't use the libata system of identifying drives. Just be careful to repartition, reboot before installing into /dev/sd...

I tried everything I can with Feisty and always having root mount problems. It re-labels my IDE disks from /dev/hd.. to /dev/sd.. and even when I identify the correct root /dev/ using the grub-auto-commands I get kernel panics until I give up rebooting and destroying my PC.

Other distro with libata system (ZenWalk 4.6) also has not end of booting problems on my mixed SATA/PATA system.  HTH

---

### Post by maluze on 2007-06-11
^ interesting...I rebooted, and reformatted my HD (as stated earlier),at which ubuntu SHOULD recognize it as a mass storage device, and mount it, right?...well, its always done the first part (recognize it), but never mounted it. Im at a loss over what to do :(

---

### Post by bluknight on 2007-06-11
You can mount it manually but I think you meant the system doesnt mount it automatically after you have selected the mounted partition. Your bios must allow boot from USB devices. There're lots of thread - just search "USB". Im now trying to make a new initrd to enable Feisty to see the USB devices. Here is a thread:
[http://ubuntuforums.org/showthread.php?t=20522](http://ubuntuforums.org/showthread.php?t=20522)

Good luck.

---

### Post by maluze on 2007-06-11
^ I dont think you read my posts above correctly...after running "mount -a", it says, "Fuse: mountpoint creation failed, /media/SEAGATE doesnt exist"

---

### Post by maluze on 2007-06-12
.. since this past weekend, I have 1) reformatted my Seagate HD to ext3 (as stated above), and 2) Reinstalled Ubuntu on my PC.

I figured, this problem may be caused by some changes i have made to Ubuntu, but after doing a fresh install, it still will not mount (shouldnt ubuntu automount an ext3???); dmesg revealed the following error message: 	

"USB 4-4: string descriptor 0 read error -71", and then "USB 4-4 can't set config #1, error -71". 	

can someone even tell me what error -71 means? i searched on google and could find anything, much less get a solution :(

---

### Post by bluknight on 2007-06-12
OK found a suggestion from the thread: As root
Boot into liveCD and mount your installed system to /mnt/target
>chroot /mnt/target
>su
>edit the /etc/initramfs-tools/modules file to add the line "piix"
>update-initramfs -u
>reboot with the new initrd.img file now replaced in /boot

As it turned out kernel 2.6.20.. no longer uses mkinitrd

Let me know if it works for you. It worked only partly for me :(

[http://ubuntuforums.org/showthread.php?t=421588&highlight=can%27t+access+tty](http://ubuntuforums.org/showthread.php?t=421588&highlight=can%27t+access+tty)

---

