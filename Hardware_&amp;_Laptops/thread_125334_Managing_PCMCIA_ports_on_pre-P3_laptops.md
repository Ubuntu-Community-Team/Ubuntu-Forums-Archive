---
title: "Managing PCMCIA ports on pre-P3 laptops"
date: 2006-02-03
forum: Hardware &amp; Laptops
---

### Post by mohapi on 2006-02-03
Hi. I've been fighting with PCMCIA issues on two machines that predate Pentium III processors (I'm just using that as a marker), and I was wondering if anyone had suggestions for me. I'll try to explain the issues in as much detail as possible.

First, I've tried three different PCMCIA cards: 

[LIST]
[*]a Belkin Wireless G model F5D7010 version 5,
[*]a Linksys WPC54G version 2, and
[*]a SanDisk CF card adapter.
[/LIST]
In two different laptops:

[LIST]
[*]a CTX EzBook 700E, upgraded to a K6-III 475Mhz, 128MB RAM and a 20GB 5400rpm hard drive, and
[*]a Compaq Presario 1020 ... 120Mhz, 48Mb, 1.08Gb
[/LIST]
As you can see, neither of these machines is a real speed demon, and aside from the non-stock additions I've made, the hardware is specific to 1997-1998 technology. I only mention that because I think it is an issue.

In short, neither of those two machines will acknowledge a PCMCIA card when it is inserted. The output of an *lspci* or *lspci -v* command gives _only_ cardbus hardware info. By comparison, putting the same card into my Dell XPS M170 yields this line. ...

[QUOTE=Dell XPS M170]0000:04:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface[/QUOTE]
Which, if I understand it correctly, is the way it should show up. (Of course, the Belkin wireless card and the CF card have slightly different entries, but you should get the picture.)

To complicate things further, all three cards will work perfectly on the EzBook 700E when installed (with the proper drivers, of course) under Windows XP. (The Compaq won't run WinXP and I don't have the patience for any earlier versions.)

I've tinkered with server installations under Ubuntu 5.10 and with DSL 2.1b, and the same problem happens with both distros. I've also tried the PCMCIA tool that comes with DSL, but I think it's just a GUI for the cardctl program, which doesn't have any better success.

Keep in mind that no drivers are installed, and *ndiswrapper* is not in use. Personally, I don't think drivers or *ndiswrapper* would be of much help, since they would simply report that the hardware was not installed (in fact, I know this to be true, since I've tried full Ubuntu installs on the EzBook and I get the same results). 

I'm starting to wonder if there was a change in PCMCIA protocol somwhere between 1998 and 2005 that keeps the older machines from acknowledging a newer PCMCIA card (without prodding from Windows, which is why they work in the EzBook under WinXP).

Can anyone suggest a way of prodding Linux into acknowledging those slots?

Thanks in advance. Cheers.

---

### Post by mpvano on 2006-02-03
I don't have a fix for you, but I do have a suggestion - lspci only displays PCI cards. ONLY cardbus cards are PCI! PCMCIA cards are basically a special variant of ISA bus with plug and play information.

Perhaps you'd do better troubleshooting using lshw, which is designed to show other kinds of cards as well.

hope this helps you troubleshoot...

Mario

---

### Post by mohapi on 2006-02-03
Thanks. I'll try that as well. ;)

---

### Post by Duster929 on 2006-02-04
Hey there.  I'm new here.  First post, in fact... and trying to learn about Ubuntu but having a bit of a hard time of it.

First off, I'm having the EXACT same problem you are with an older laptop and a Linksys wireless card.

Did you manage to resolve the problem, and if so, how did you do it.  And please, if I can ask in advance, keep it simple and walk me through the steps, since I'm really new to all this.

--- D

---

### Post by mohapi on 2006-02-04
No, unfortunately, I haven't gotten a solution. I hunted down the documentation for the PCMCIA routines that Linux uses, but the bulk of it is so far over my head that it did me little good.

I've posted this message in four forums, but this one is the only one that seems productive. If I hear anything I will DEFINITELY repeat it here, just for the sake of other Ubuntu users.

But surely somebody uses a PCMCIA wireless card on an early laptop and can give us some sort of clue? :confused:

---

### Post by mohapi on 2006-02-05
Well, I seem to be moving in the right direction, even if I'm not making much progress. 

I tried the acpi=off trick described [here]("http://ubuntuforums.org/showthread.php?t=96240"), but it was only moderately successful. I found that, after modifying the GRUB command line, I could get ident and info out of cardctl, but *only for the CF card reader.* And I couldn't mount it, because I'm not sure what format a CF card uses for the *mount* command. :rolleyes: If it isn't one thing, it's another, right?

Frustrating, to say the least, but like I said, a step in the right direction. I still have no idea why either of the wireless cards won't follow suit, but I'm starting over with a clean system, in hopes of figuring it out. I have a sneaky suspicion that all my tinkering and tweaking might have some effect on what I'm doing.

Either way, I would more than welcome suggestions. Cheers!

---

### Post by mohapi on 2006-02-07
Another update in my eternal quest to understand legacy PCMCIA and how it works with Linux 2.6.12.

Apparently there are some known situations where the PCMCIA card is undetected, but these seem unique to other hardware, other kernels or other configurations. I don't think it's a bug, I think it's some sort of quirk of legacy systems.

I built a custom kernel for the Compaq that stripped out anything made after 1993, and included anything I could think of that might improve PCMCIA support. But apart from speeding things up slightly, I had no better success than when I attached the acpi=off flag to my GRUB command line.

As a troubleshooting measure, I used the Ubuntu 5.10 Live CD in my father's Inspiron 8000, and aside from configuring the WPC11, there was no problem whatsoever getting it online. The same PCMCIA card was ignored in the EzBook 700E ... except in Windows, of course.

I suppose that means my suspected hardware change did happen somewhere between the Pentium and Pentium III models, which only vaguely pins it down for me. Unless it's a hardware command that powers up the card, making it recognizable ... ?

I haven't given up yet, although I could easily write it off and find another cheap P3 laptop to tinker with, and get started networking. I guess I'm just one of those people who can't let something alone. And I am learning a lot.

As always, every idea and suggestion is highly appreciated. Short of "Use Windows, dude." :confused:

edited: Removed a mislink. And for some reason I had the Linux version wrong.

---

### Post by mohapi on 2006-02-07
I just realized I haven't been very good at giving the help it might take to solve this problem. Here are a few common commands that might give you information about this situation.

These are from the CTX EzBook 700E. This is a socket 7 machine that came stock with 64MB and a Pentium II 233Mhz processor. The machine has been upgraded to a K6-III 475Mhz and 128MB RAM. This is a dual boot WinXP and Ubuntu 5.10 server install on a 2GB Toshiba 4200rpm hard drive (gawd that drive is SLOW and LOUD).

The card is inserted. This model has an indicator light to show the presence of a card in either socket. The card works perfectly under Windows XP, when the drivers are installed.

Ndiswrapper is not running or installed. I don't believe it will come into play until the device can be detected.

Output, as root, of *cardctl ident *...

```
Socket 0:
  no product info available
Socket 1:
  no product info available

```
Output, as root, of *cardctl info* ...

```
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

```
Output, as root, of *dmesg* ...

```
[4294667.296000] Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e801: 0000000000000000 - 000000000009f000 (usable)
[4294667.296000]  BIOS-e801: 0000000000100000 - 0000000008000000 (usable)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 128MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 32768
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:1
[4294667.296000]   Normal zone: 28672 pages, LIFO batch:15
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:1
[4294667.296000] DMI not present.
[4294667.296000] ACPI: Unable to locate RSDP
[4294667.296000] Allocating PCI resources starting at 08000000 (gap: 08000000:f8000000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda3 ro quiet splash
[4294667.296000] No local APIC present or hardware disabled
[4294667.296000] mapped APIC to ffffd000 (01101000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[    0.000000] Detected 232.141 MHz processor.
[15952.682114] Using tsc for high-res timesource
[15952.683646] Console: colour VGA+ 80x25
[15952.688284] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[15952.690156] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[15952.719323] Memory: 121860k/131072k available (1415k kernel code, 8696k reserved, 763k data, 224k init, 0k highmem)
[15952.719357] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[15952.719869] Calibrating delay loop... 457.72 BogoMIPS (lpj=228864)
[15952.737078] Security Framework v1.0.0 initialized
[15952.737121] SELinux:  Disabled at boot.
[15952.737235] Mount-cache hash table entries: 512
[15952.738095] CPU: After generic identify, caps: 008021bf 808029bf 00000000 00000000 00000000 00000000 00000000
[15952.738155] CPU: After vendor identify, caps: 008021bf 808029bf 00000000 00000000 00000000 00000000 00000000
[15952.738215] CPU: L1 I Cache: 32K (32 bytes/line), D cache 32K (32 bytes/line)
[15952.738240] CPU: After all inits, caps: 008021bf 808029bf 00000000 00000002 00000000 00000000 00000000
[15952.738285] CPU: AMD-K6(tm) 3D processor stepping 0c
[15952.738320] Checking 'hlt' instruction... OK.
[15952.741832] Checking for popad bug... OK.
[15952.742804] checking if image is initramfs... it is
[15956.584853] Freeing initrd memory: 4791k freed
[15956.589535] NET: Registered protocol family 16
[15956.589805] EISA bus registered
[15956.590291] PCI: PCI BIOS revision 2.10 entry at 0xeb360, last bus=2
[15956.590357] PCI: Using configuration type 1
[15956.590381] mtrr: v2.0 (20020519)
[15956.592375] ACPI: Subsystem revision 20050729
[15956.592394] ACPI: Interpreter disabled.
[15956.592420] Linux Plug and Play Support v0.97 (c) Adam Belay
[15956.592527] pnp: PnP ACPI: disabled
[15956.592550] PnPBIOS: Scanning system for PnP BIOS support...
[15956.593348] PnPBIOS: Found PnP BIOS installation structure at 0xc00ff020
[15956.593386] PnPBIOS: PnP BIOS version 1.0, entry 0xec000:0x230d, dseg 0xec000
[15956.601684] PnPBIOS: 16 nodes reported by PnP BIOS; 16 recorded by driver
[15956.602100] PCI: Probing PCI hardware
[15956.602124] PCI: Probing PCI hardware (bus 00)
[15956.603716] Boot video device is 0000:00:08.0
[15956.607939] PCI: Using IRQ router PIIX/ICH [8086/7110] at 0000:00:01.0
[15956.608009] PCI: IRQ 0 for device 0000:00:0a.0 doesn't match PIRQ mask - try pci=usepirqmask
[15956.608049] PCI: IRQ 0 for device 0000:00:0a.1 doesn't match PIRQ mask - try pci=usepirqmask
[15956.613401] pnp: 00:01: ioport range 0xcf8-0xcff could not be reserved
[15956.613431] pnp: 00:01: ioport range 0x4d0-0x4d1 has been reserved
[15956.613459] pnp: 00:01: ioport range 0x398-0x399 has been reserved
[15956.613487] pnp: 00:01: ioport range 0x3f0-0x3f1 has been reserved
[15956.613514] pnp: 00:01: ioport range 0x3f3-0x3f3 has been reserved
[15956.613542] pnp: 00:01: ioport range 0x3f7-0x3f7 has been reserved
[15956.613571] pnp: 00:01: ioport range 0x1000-0x107f could not be reserved
[15956.619528] audit: initializing netlink socket (disabled)
[15956.619578] audit: initialized
[15956.620616] VFS: Disk quotas dquot_6.5.1
[15956.620792] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[15956.621110] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[15956.621170] devfs: boot_options: 0x0
[15956.621486] Initializing Cryptographic API
[15956.621527] Limiting direct PCI/PCI transfers.
[15956.622376] isapnp: Scanning for PnP cards...
[15956.719657] isapnp: Card 'ESS ES1869 Plug and Play AudioDrive'
[15956.719683] isapnp: 1 Plug & Play card detected total
[15957.031517] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[15957.033826] serio: i8042 AUX port at 0x60,0x64 irq 12
[15957.034020] serio: i8042 KBD port at 0x60,0x64 irq 1
[15957.034053] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[15957.034627] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[15957.035394] ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
[15957.069645] pnp: Device 00:0d activated.
[15957.070184] ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[15957.071769] io scheduler noop registered
[15957.071862] io scheduler anticipatory registered
[15957.071907] io scheduler deadline registered
[15957.071994] io scheduler cfq registered
[15957.076953] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[15957.078063] EISA: Probing bus 0 at eisa.0
[15957.078107] Cannot allocate resource for EISA slot 1
[15957.078140] Cannot allocate resource for EISA slot 3
[15957.078214] EISA: Detected 0 cards.
[15957.078502] NET: Registered protocol family 2
[15957.088860] IP: routing cache hash table of 1024 buckets, 8Kbytes
[15957.090114] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[15957.090924] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[15957.091416] TCP: Hash tables configured (established 8192 bind 8192)
[15957.092265] NET: Registered protocol family 8
[15957.092316] NET: Registered protocol family 20
[15957.095432] Freeing unused kernel memory: 224k freed
[15957.190527] input: AT Translated Set 2 keyboard on isa0060/serio0
[15957.447986] Capability LSM initialized
[15957.616048] NET: Registered protocol family 1
[15957.750424] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[15957.750537] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[15957.811741] PIIX4: IDE controller at PCI slot 0000:00:01.1
[15957.811815] PIIX4: chipset revision 1
[15957.811834] PIIX4: not 100% native mode: will probe irqs later
[15957.811880]     ide0: BM-DMA at 0x3000-0x3007, BIOS settings: hda:DMA, hdb:pio
[15957.811951]     ide1: BM-DMA at 0x3008-0x300f, BIOS settings: hdc:pio, hdd:pio
[15957.812017] Probing IDE interface ide0...
[15958.075593] hda: TOSHIBA MK2104MAV, ATA DISK drive
[15958.687873] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[15958.688376] Probing IDE interface ide1...
[15959.359747] hdc: CD-ROM CDR_U241, ATAPI CD/DVD-ROM drive
[15959.665814] ide1 at 0x170-0x177,0x376 on irq 15
[15959.666799] ide2: I/O resource 0x3EE-0x3EE not free.
[15959.666823] ide2: ports already in use, skipping probe
[15959.666846] Probing IDE interface ide3...
[15960.179753] Probing IDE interface ide4...
[15960.692814] Probing IDE interface ide5...
[15961.245722] hda: max request size: 128KiB
[15961.548421] hda: 4233600 sectors (2167 MB), CHS=4200/16/63, DMA
[15961.548459] hda: cache flushes not supported
[15961.549050]  /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 p4 < p5 >
[15961.633455] hdc: ATAPI 24X CD-ROM drive, 128kB Cache
[15961.633502] Uniform CD-ROM driver Revision: 3.20
[15965.160990] Attempting manual resume
[15965.161731] swsusp: Suspend partition has wrong signature?
[15965.533628] usbcore: registered new driver usbfs
[15965.533938] usbcore: registered new driver hub
[15965.543806] USB Universal Host Controller Interface driver v2.2
[15965.544276] PCI: Enabling device 0000:00:01.2 (0000 -> 0001)
[15965.544319] PCI: setting IRQ 11 as level-triggered
[15965.544341] PCI: Assigned IRQ 11 for device 0000:00:01.2
[15965.544470] uhci_hcd 0000:00:01.2: Intel Corporation 82371AB/EB/MB PIIX4 USB
[15965.607835] uhci_hcd 0000:00:01.2: new USB bus registered, assigned bus number 1
[15965.607893] uhci_hcd 0000:00:01.2: irq 11, io base 0x0000fbe0
[15965.609295] hub 1-0:1.0: USB hub found
[15965.609441] hub 1-0:1.0: 2 ports detected
[15972.473394] Attempting manual resume
[15972.491336] swsusp: Suspend partition has wrong signature?
[15972.618564] kjournald starting.  Commit interval 5 seconds
[15972.618663] EXT3-fs: mounted filesystem with ordered data mode.
[15977.541245] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[15993.626599] Adding 84632k swap on /dev/hda5.  Priority:-1 extents:1
[15994.443299] EXT3 FS on hda3, internal journal
[16034.776359] pnp: Device 00:0c activated.
[16034.776389] parport: PnPBIOS parport detected.
[16034.776463] parport0: PC-style at 0x378, irq 7 [PCSPP]
[16034.920711] lp0: using parport0 (interrupt-driven).
[16035.242107] mice: PS/2 mouse device common for all mice
[16036.105486] Synaptics Touchpad, model: 1, fw: 4.1, id: 0x148a1, caps: 0x0/0x0
[16036.125308] input: SynPS/2 Synaptics TouchPad on isa0060/serio1
[16038.808893] ts: Compaq touchscreen protocol output
[16043.633146] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[16047.551771] cdrom: open failed.
[16055.106884] piix4_smbus 0000:00:01.3: Found 0000:00:01.3 device
[16056.210834] Linux Kernel Card Services
[16056.210870]   options:  [pci] [cardbus] [pm]
[16056.336632] PCI: IRQ 0 for device 0000:00:0a.0 doesn't match PIRQ mask - try pci=usepirqmask
[16056.336685] PCI: setting IRQ 9 as level-triggered
[16056.336708] PCI: Assigned IRQ 9 for device 0000:00:0a.0
[16056.336816] Yenta: CardBus bridge found at 0000:00:0a.0 [0000:0000]
[16056.457042] Yenta: ISA IRQ mask 0x0000, PCI irq 9
[16056.457062] Socket status: 00000000
[16056.506853] PCI: IRQ 0 for device 0000:00:0a.1 doesn't match PIRQ mask - try pci=usepirqmask
[16056.506910] PCI: Assigned IRQ 9 for device 0000:00:0a.1
[16056.507025] Yenta: CardBus bridge found at 0000:00:0a.1 [0000:0000]
[16056.627063] Yenta: ISA IRQ mask 0x0000, PCI irq 9
[16056.627082] Socket status: 00000000
[16061.470861] Real Time Clock Driver v1.12
[16062.176737] input: PC Speaker
[16063.965706] Floppy drive(s): fd0 is 1.44M
[16063.965983] floppy0: Floppy io-port 0x03f2 in use
[16065.569105] irda_init()
[16065.569243] NET: Registered protocol family 23
[16067.349735] pnp: Device 01:01.02 activated.
[16067.392641] gameport: NS558 PnP Gameport is pnp01:01.02/gameport0, io 0x201, speed 817kHz
[16080.253715] cs: IO port probe 0x100-0x4ff: clean.
[16080.256595] cs: IO port probe 0x100-0x4ff: clean.
[16080.261174] cs: IO port probe 0xc00-0xcf7: clean.
[16080.262023] cs: IO port probe 0xc00-0xcf7: clean.
[16080.264292] cs: IO port probe 0xa00-0xaff: clean.
[16080.265138] cs: IO port probe 0xa00-0xaff: clean.

```
Output, as root, of *lshw* ...

```
e700-a475
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 128MB
     *-cpu
          product: AMD-K6(tm) 3D processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 5.8.12
          size: 250MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 pge mmx syscall 3dnow k6_mtrr
        *-cache
             description: L1 cache
             physical id: 0
             size: 64KB
     *-pci
          description: Host bridge
          product: 430TX - 82439TX MTXC
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82371AB/EB/MB PIIX4 ISA
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: 82371AB/EB/MB PIIX4 IDE
             vendor: Intel Corporation
             physical id: 1.1
             bus info: pci@00:01.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:3000-300f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: TOSHIBA MK2104MAV
                   vendor: Toshiba
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: E4.02 A
                   serial: 88E40351
                   size: 2067MB
                   capacity: 2067MB
                   capabilities: ata dma lba iordy smart security pm
                   configuration: smart=on
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: IDE CD-ROM
                   product: CD-ROM CDR_U241
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 1.04
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio
        *-usb
             description: USB Controller
             product: 82371AB/EB/MB PIIX4 USB
             vendor: Intel Corporation
             physical id: 1.2
             bus info: pci@00:01.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:fbe0-fbff irq:11
           *-usbhost
                product: Intel Corporation 82371AB/EB/MB PIIX4 USB
                vendor: Linux 2.6.12-9-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-bridge
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ACPI
             vendor: Intel Corporation
             physical id: 1.3
             bus info: pci@00:01.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=piix4_smbus
             resources: irq:9
        *-display
             description: VGA compatible controller
             product: NM2160 [MagicGraph 128XD]
             vendor: Neomagic Corporation
             physical id: 8
             bus info: pci@00:08.0
             version: 01
             size: 16MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master
             resources: iomemory:c5000000-c5ffffff iomemory:c6e00000-c6ffffff iomemory:c7100000-c71fffff
        *-pcmcia:0
             description: CardBus bridge
             product: PCI1131
             vendor: Texas Instruments
             physical id: a
             bus info: pci@00:0a.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master
             configuration: driver=yenta_cardbus
             resources: iomemory:8000000-8000fff irq:9
        *-pcmcia:1
             description: CardBus bridge
             product: PCI1131
             vendor: Texas Instruments
             physical id: a.1
             bus info: pci@00:0a.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master
             configuration: driver=yenta_cardbus
             resources: iomemory:8001000-8001fff irq:9

```
Output, as root, of *lsmod* ...

```
Module                  Size  Used by
sg                     33696  0 
scsi_mod              124872  1 sg
pcmcia                 24584  4 
analog                 10528  0 
ns558                   5508  0 
gameport               14472  3 analog,ns558
irtty_sir               7808  0 
sir_dev                17324  1 irtty_sir
irda                  159804  2 irtty_sir,sir_dev
crc_ccitt               2176  1 irda
pcspkr                  3652  0 
rtc                    11832  0 
yenta_socket           22540  2 
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_piix4               8336  0 
i2c_core               19728  1 i2c_piix4
dm_mod                 50364  1 
joydev                  9280  0 
tsdev                   7616  0 
evdev                   9088  0 
psmouse                26116  0 
mousedev               10912  0 
parport_pc             31812  1 
lp                     11460  0 
parport                32072  2 parport_pc,lp
md                     40656  0 
ext3                  115976  1 
jbd                    48536  1 ext3
processor              23100  0 
uhci_hcd               28048  0 
usbcore               104188  2 uhci_hcd
ide_cd                 36996  0 
cdrom                  33952  1 ide_cd
ide_disk               16128  3 
ide_generic             1664  0 
piix                    9476  1 
ide_core              125268  4 ide_cd,ide_disk,ide_generic,piix
unix                   24624  10 
fbcon                  34176  0 
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon
vesafb                  8088  0 
cfbcopyarea             4480  1 vesafb
cfbimgblt               2944  1 vesafb
cfbfillrect             3840  1 vesafb
softcursor              2432  1 vesafb
capability              5000  0 
commoncap               6784  1 capability

```
Output, as root, of *lspci* ... 

```
0000:00:00.0 Host bridge: Intel Corp. 430TX - 82439TX MTXC (rev 01)
0000:00:01.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 01)
0000:00:01.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:01.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:01.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 01)
0000:00:08.0 VGA compatible controller: Neomagic Corporation NM2160 [MagicGraph 128XD] (rev 01)
0000:00:0a.0 CardBus bridge: Texas Instruments PCI1131 (rev 01)
0000:00:0a.1 CardBus bridge: Texas Instruments PCI1131 (rev 01)

```

And finally, output, as root, of *lspci -vvv* ...

```
0000:00:00.0 Host bridge: Intel Corp. 430TX - 82439TX MTXC (rev 01)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
	Latency: 32

0000:00:01.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 01)
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0

0000:00:01.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32
	Region 4: I/O ports at 3000 [size=16]

0000:00:01.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64
	Interrupt: pin D routed to IRQ 11
	Region 4: I/O ports at fbe0 [size=32]

0000:00:01.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 01)
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin ? routed to IRQ 9

0000:00:08.0 VGA compatible controller: Neomagic Corporation NM2160 [MagicGraph 128XD] (rev 01) (prog-if 00 [VGA])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (4000ns min, 63750ns max)
	Interrupt: pin A routed to IRQ 0
	Region 0: Memory at c5000000 (32-bit, prefetchable) [size=16M]
	Region 1: Memory at c6e00000 (32-bit, non-prefetchable) [size=2M]
	Region 2: Memory at c7100000 (32-bit, non-prefetchable) [size=1M]

0000:00:0a.0 CardBus bridge: Texas Instruments PCI1131 (rev 01)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 168, Cache Line Size: 0x20 (128 bytes)
	Interrupt: pin A routed to IRQ 9
	Region 0: Memory at 08000000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=01, subordinate=04, sec-latency=176
	Memory window 0: 08400000-087ff000 (prefetchable)
	Memory window 1: 08800000-08bff000
	I/O window 0: 00004000-000040ff
	I/O window 1: 00004400-000044ff
	BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt- PostWrite+
	16-bit legacy interface ports at 0001

0000:00:0a.1 CardBus bridge: Texas Instruments PCI1131 (rev 01)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 168, Cache Line Size: 0x20 (128 bytes)
	Interrupt: pin B routed to IRQ 9
	Region 0: Memory at 08001000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=05, subordinate=08, sec-latency=176
	Memory window 0: 08c00000-08fff000 (prefetchable)
	Memory window 1: 09000000-093ff000
	I/O window 0: 00004800-000048ff
	I/O window 1: 00004c00-00004cff
	BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+
	16-bit legacy interface ports at 0001


```

Thanks again. Let me know if there's anything that might give you more info.

edited: Removed uglifying typo. ;)

---

### Post by mohapi on 2006-02-07
One last note: I've seen the bug report for PCMCIA in Linux 2.6, and the [problem with port subordination]("http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html#knownproblems"), but adding pci=assign-busses to the kernel boot line did nothing. Thanks. :)

---

### Post by mohapi on 2006-02-13
Well, it is time for me to admit defeat. I played my last card today (no pun intended), and came up with nothing to show for it.

I recompiled the kernel for the EzBook 700e, this time leaving out the PCMCIA structure that was built in by default. Hours later, I installed it, ran it and tried to incorporate the [PCMCIA services for Linux](http://pcmcia-cs.sourceforge.net/) package.

Unfortunately, that turned into an entirely new can of worms -- and one I decided I didn't want to open. It was too time-consuming, I couldn't be sure it would be of any real use, and most of all, the resources I needed to do it properly were online ... and without my PCMCIA wireless, I can't get online with that machine. 

So I was caught in a bit of a Catch-22. That's quite a catch, that Catch-22. Best there is.

Perhaps one day when I have more than just a month's experience with Linux and a better grasp of hardware quirks, I'll tackle the problem again. I don't know how Windows is able to activate those cards on these machines, but the solution is beyond my grasp.

Either way, my efforts are posted here for the benefit of the next person who stumbles onto this problem. I wish them better luck. I appreciate the help I found in this forum and the suggestions everyone made, even if it was just "install ndiswrapper, dude."

The real tragedy is this: The function for either of these laptops is as a passive network monitor (not even an Internet gateway, just a monitor), so without Internet access, they are of little use to me. I love these old machines, but I don't like keeping things that have no function. I call that junk.

I think they shall pass into the great afterworld of technology, the digital heaven, the place where all good computers go when they die ...

eBay. :mrgreen: 

Cheers and good luck. See you all around the boards. \\:D/

---

### Post by mips on 2006-02-13
Hi,

Two suggestions.
1. Update the BIOS on those laptops to the latest you can find available.
2. Download the latest Knoppix LiveCD (I assume those machines have cd-rom drives ?) and see if knoppic detects the cards. Knoppix has excellent hardware support. If it works you could always implement changes in Ubuntu.

Do those laptops actually have full 32-bit cardbus slots ???

---

### Post by mohapi on 2006-02-13
[QUOTE=mips]Hi,

Two suggestions.
1. Update the BIOS on those laptops to the latest you can find available.
2. Download the latest Knoppix LiveCD (I assume those machines have cd-rom drives ?) and see if knoppic detects the cards. Knoppix has excellent hardware support. If it works you could always implement changes in Ubuntu.

Do those laptops actually have full 32-bit cardbus slots ???[/QUOTE]
Thanks, mips. 

1. Both machines have the most current BIOS I could find. Of course, the Presario dates back to 1993, so that one is a bit tougher to find. The EzBook I'm sure has the 1.01 version of SystemSoft. An awful, awful BIOS, that one. ...

2. I'm going to try that now. It'll be my last-ditch effort. Thanks for the idea.

As far as the cardbus slots, I assumed they did after looking at the results of a *lshw* and *lspci -vvv* commands (see above). And if it was a true hardware incompatibility, would Windows still be able to use those cards?

---

### Post by mips on 2006-02-13
[QUOTE=mohapi] And if it was a true hardware incompatibility, would Windows still be able to use those cards?[/QUOTE]


:oops: Sorry, forgot about that. If it worked in windows then it proves slots are fine.

---

### Post by mohapi on 2006-02-14
[QUOTE=mips]:oops: Sorry, forgot about that. If it worked in windows then it proves slots are fine.[/QUOTE]
No problem. That's the real stumper in this whole situation. Windows just turns the darn things on, like there's nothing wrong in the whole wide world. Linux can't even see them. It's infuriating. 

Either way, I'll post again after I try Knoppix. Maybe I'll get lucky. :rolleyes:

---

### Post by mohapi on 2006-02-14
Well, it almost worked. The Knoppix 4.0.2 Live CD had no better luck. Still nothing at the ports, and nothing sensed on configuration.

I'm going to poke around with DSL 2.2, though. I see that [the newest version]("http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?;act=ST;f=4;t=11356") drops back to kernel 2.4.26, which might help me. 

Here and I thought I had surrendered to this problem. It just won't leave me be. .... :o

---

### Post by mips on 2006-02-14
you are going to have nightmares....;)

I hope you get it working, DSL will perform better as well.

---

### Post by Greg2 on 2006-02-14
[QUOTE=mohapi]
Output, as root, of *dmesg* ...

```

-snip-

[4294667.296000] No local APIC present or hardware disabled

-snip-

[15956.592394] ACPI: Interpreter disabled.

-snip-

[15956.607939] PCI: Using IRQ router PIIX/ICH [8086/7110] at 0000:00:01.0
[15956.608009] PCI: IRQ 0 for device 0000:00:0a.0 doesn't match PIRQ mask - try pci=usepirqmask
[15956.608049] PCI: IRQ 0 for device 0000:00:0a.1 doesn't match PIRQ mask - try pci=usepirqmask

```[/QUOTE]
Have you tried using this as a boot parameter:```
pci=usepirqmask
```or```
noapic pci=usepirqmask
```

---

### Post by mohapi on 2006-02-14
No luck. I still get nothing with *lshw*, *lspci -vvv*, *cardctl info* or *cardctl ident*. I also tried the *pci=assign-busses* tag on my boot line again, this time with a clean and fresh server install. No luck. :(

If I use *sudo cardctl insert*, I get an error message. ...

```
[10134.865901] PCMCIA: socket c209bc2c: *** DANGER *** unable to remove socket power
[10134.867892] PCMCIA: socket c20eb42c: *** DANGER *** unable to remove socket power
```
*info* and *ident* still come up empty. The laptop's indicator light is on for that socket, but the power to the card is dead. No lights, no signal.

Thanks for all your help, gang.

---

### Post by mohapi on 2006-02-15
My list of casualties seems to be growing. 

Out of curiosity, I borrowed a Microsoft MN-520, an 802.11b wireless that's a bit dated but listed as working out of the box. My hope was that an older card would prove more successful in an older laptop.

No dice. No lights, no power, no beeps on insert. Same lack of information from *cardctl*. *Lspci -vvv* and *lshw* are identical. (This wouldn't have anything to do with the whole Linux-Microsoft thing, would it? :mrgreen: )

I'm going to try one more idea ... recompile an early, early kernel and see if anything improves. What the heck. I've spent way too much time on this already. Might was well keep plugging at it. ... :cry:

---

### Post by mips on 2006-02-15
I'll give you 10/10 for perseverance ;) You're like a dog with a bone that just wont let go....

---

### Post by Greg2 on 2006-02-15
I’ve found one person that has your laptop PCMCIA bridge working with a 16 bit Ethernet controller:
[http://home.comcast.net/~fbui/Linux-on-CTXEz700.html](http://home.comcast.net/~fbui/Linux-on-CTXEz700.html)

---

### Post by mohapi on 2006-02-15
Thanks. I might try another distro, just to see if it's somehow workaroundable (is that a word? :confused: ). Damn Small Linux didn't have any better luck, but you never know.

I wonder: He describes his bridge as a Omega Micro Inc. 82C092G (rev 02). Isn't mine the Texas Instruments PCI1131?

---

### Post by Greg2 on 2006-02-15
[QUOTE=mohapi]I wonder: He describes his bridge as a Omega Micro Inc. 82C092G (rev 02). Isn't mine the Texas Instruments PCI1131?[/QUOTE]
Yes, but it still looks like Slackware will work:
[http://www.eskimo.com/~meik/linux/slackwareinstall.html](http://www.eskimo.com/~meik/linux/slackwareinstall.html)

---

### Post by mohapi on 2006-02-16
SUCCESS! \\:D/  UNBELIEVABLE! Slackware did it. I don't understand how or why, but I have both lamps lit on the MN-520 and full reports from cardctl. 

Amazing. I thought for sure I was going to be in the market for a new machine.

Just for the record, this is the Microsoft MN-520 on the CTX EzBook 700E with Slackware 10.2 and the 2.4.31 kernel. 

Slack is quite a bit different from Ubuntu, that's for sure. Installation was a bit more ... weird. It's still as step above what little I've seen of Gentoo, though. 

I need to figure out how to link with my router now, but I'll do that on a Slackware board. Cheers and thanks a bunch folks.

---

### Post by Greg2 on 2006-02-16
[QUOTE=mohapi]Just for the record, this is the Microsoft MN-520 on the CTX EzBook 700E with Slackware 10.2 and the 2.4.31 kernel. [/QUOTE]
Congratulations! I think the magic was in the 2.4.31 kernel. This is good to know when I’m at the local yard sales this coming summer.
>  I need to figure out how to link with my router now, but I'll do that on a Slackware board.You can always put the 2.4.31 kernel source on your 20 GB HDD and build one for Ubuntu if you like.:)

---

### Post by mohapi on 2006-02-16
I think that might be my next step. I've learned a lot over the past month trying to figure this out, and one thing I've learned as that I am *quite* spoiled with Ubuntu.

Slack is good, and Slack did the job for me, but I don't think I'll stick with it if I can help it. There are things I've just gotten used to in Ubuntu that don't really work in Slackware, and I've come to expect them. Even just terminal commands like *lshw* don't seem supported. And logging in as root each time is kind of creepy. I feel like I need sudo.

Here's a snapshot of our winner, cruising the Internet for the first time in Linux. ...

[CENTER][[IMG]http://img132.imageshack.us/img132/6411/winner9lx.th.jpg[/IMG]](http://img132.imageshack.us/my.php?image=winner9lx.jpg)[/CENTER]

Now you know why I wasn't keen on tossing out this machine. Quite pretty, isn't it? Oh well. I suppose a parent always loves his own child best. ... :p 

Thanks everyone! We did it!

---

