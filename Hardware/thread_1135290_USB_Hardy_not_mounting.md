---
title: "USB Hardy not mounting"
date: 2009-04-24
forum: Hardware
---

### Post by petebarchetta on 2009-04-24
hello all,

i have recently come across an issue with USB after updating from Dapper LTS install onto Hardy LTS, all services appear to work apart from the USB, i can use a USB mouse with the machine, but when i try to plug in my USB mamory stick i get the following error
"mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
similar to the thread below

[http://ubuntuforums.org/showthread.php?t=388106]("http://ubuntuforums.org/showthread.php?t=388106")
my concern is that although it all worked in Dapper, something has changed in hardy to stop it working.
see the Dmesg output in the thread below

[http://ubuntuforums.org/showthread.php?t=1100412&highlight=petebarchetta]("http://ubuntuforums.org/showthread.php?t=1100412&highlight=petebarchetta")

any ideas, as the Dmesg doesnt show anything out of place,
to get USB working before i have edited the Grub to include noapic and Irqpoll, which solved it, but now its not working with these entries in grub. i can see the devices coming in and out of the usb list, but it is unmountable, the filesystem is Fat32

---

### Post by KhurramM on 2009-04-24
Put a line like this in /etc/fstab

/dev/hda8      /win/pen               vfat    rw,uid,umask=0002,iocharset=iso8859-1,utf8   0 0

try a mount -av or/and a system restart.

I think it should mount it.

Hope this helps. Adios.

---

### Post by petebarchetta on 2009-05-21
if i understand you right then the line should read like this for USB as they are SDA?
/dev/sda1 /win/pen vfat rw,uid,umask=0002,iocharset=iso8859-1,utf$

---

### Post by Zimmer on 2009-05-21
I think they should be SD- in Hardy, too.

So, why does your dmsg output refer to hd- in relation to your drives?

Is fstab correctly constructed?
Did GRUB update ?
Are you really booting a Hardy kernel? The version in your dmesg is 2.6.15

Mine is on 2.6.24     

Too many questions and variables if the upgrade has failed/corrupted/ not completed etc.

Might be best to back up any data you want and do a clean install...

EDIT: ! oh and I would suggest you DO NOT try and mount sda1 (that should be your installation drive) as vfat !!
use sdb for USB devices..

---

### Post by Zimmer on 2009-05-21
what does this command in a terminal tell you??

lsb_release -a

oh, and have a look here

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by petebarchetta on 2009-05-22
here's the output's of the requested commands and the most recent dmesg and fstab:
cassiopeia:~$ dmesg
[17179569.184000] Linux version 2.6.15-53-386 (buildd@palmer) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Sun Jan 25 23:29:51 UTC 2009
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000a020000 (usable)
[17179569.184000]  BIOS-e820: 000000000a020000 - 000000000a040000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fef80000 - 00000000ff000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fffe0000 - 00000000fffe6e00 (reserved)
[17179569.184000]  BIOS-e820: 00000000fffe6e00 - 00000000fffe7000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000fffe7000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 160MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 40992
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 36896 pages, LIFO batch:7
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI not present.
[17179569.184000] ACPI: Unable to locate RSDP
[17179569.184000] Allocating PCI resources starting at 10000000 (gap: 0a040000:f4f40000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda3 ro quiet splash irqpoll noapic
[17179569.184000] Misrouted IRQ fixup and polling support enabled
[17179569.184000] This may significantly impact system performance
[17179569.184000] No local APIC present or hardware disabled
[17179569.184000] mapped APIC to ffffd000 (01141000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[    0.000000] Detected 266.663 MHz processor.
[   15.834306] Using tsc for high-res timesource
[   15.837462] Console: colour VGA+ 80x25
[   15.841101] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[   15.845019] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[   15.893992] Memory: 151980k/163968k available (1979k kernel code, 11456k reserved, 607k data, 288k init, 0k highmem)
[   15.894037] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   15.974696] Calibrating delay using timer specific routine.. 538.55 BogoMIPS (lpj=1077106)
[   15.975055] Security Framework v1.0.0 initialized
[   15.975125] SELinux:  Disabled at boot.
[   15.975248] Mount-cache hash table entries: 512
[   15.976516] CPU: After generic identify, caps: 008001bf 00000000 00000000 00000000 00000000 00000000 00000000
[   15.976577] CPU: After vendor identify, caps: 008001bf 00000000 00000000 00000000 00000000 00000000 00000000
[   15.976630] Intel Pentium with F0 0F bug - workaround enabled.
[   15.976660] CPU: After all inits, caps: 008001bf 00000000 00000000 00000000 00000000 00000000 00000000
[   15.976882] mtrr: v2.0 (20020519)
[   15.976898] CPU: Intel Mobile Pentium MMX stepping 01
[   15.976938] Checking 'hlt' instruction... OK.
[   15.991977] checking if image is initramfs... it is
[   23.138197] Freeing initrd memory: 6668k freed
[   23.278605] NET: Registered protocol family 16
[   23.279032] EISA bus registered
[   23.281004] PCI: PCI BIOS revision 2.10 entry at 0xfd752, last bus=21
[   23.281051] PCI: Using configuration type 1
[   23.284453] ACPI: Subsystem revision 20051216
[   23.284476] ACPI: Interpreter disabled.
[   23.284500] Linux Plug and Play Support v0.97 (c) Adam Belay
[   23.284587] pnp: PnP ACPI: disabled
[   23.284610] PnPBIOS: Scanning system for PnP BIOS support...
[   23.284813] PnPBIOS: Found PnP BIOS installation structure at 0xc00f8e30
[   23.284849] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x9114, dseg 0x0
[   23.478289] PnPBIOS: 17 nodes reported by PnP BIOS; 17 recorded by driver
[   23.478461] PCI: Probing PCI hardware
[   23.478489] PCI: Probing PCI hardware (bus 00)
[   23.479461] Boot video device is 0000:00:04.0
[   23.484596] PCI: IRQ 0 for device 0000:00:02.0 doesn't match PIRQ mask - try pci=usepirqmask
[   23.484641] PCI: IRQ 0 for device 0000:00:02.1 doesn't match PIRQ mask - try pci=usepirqmask
[   23.496451] PCI: Bus 1, cardbus bridge: 0000:00:02.0
[   23.496480]   IO window: 00001000-000010ff
[   23.496505]   IO window: 00001400-000014ff
[   23.496529]   PREFETCH window: 10000000-11ffffff
[   23.496556]   MEM window: 12000000-13ffffff
[   23.496579] PCI: Bus 5, cardbus bridge: 0000:00:02.1
[   23.496602]   IO window: 00001800-000018ff
[   23.496626]   IO window: 00001c00-00001cff
[   23.496650]   PREFETCH window: 14000000-15ffffff
[   23.496676]   MEM window: 16000000-17ffffff
[   23.496720] PCI: IRQ 0 for device 0000:00:02.0 doesn't match PIRQ mask - try pci=usepirqmask
[   23.496757] PCI: No IRQ known for interrupt pin A of device 0000:00:02.0. Please try using pci=biosirq.
[   23.496798] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   23.496835] PCI: IRQ 0 for device 0000:00:02.1 doesn't match PIRQ mask - try pci=usepirqmask
[   23.496868] PCI: No IRQ known for interrupt pin B of device 0000:00:02.1. Please try using pci=biosirq.
[   23.496906] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   23.504028] audit: initializing netlink socket (disabled)
[   23.504123] audit(1242971015.689:1): initialized
[   23.505296] VFS: Disk quotas dquot_6.5.1
[   23.505543] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   23.506250] Initializing Cryptographic API
[   23.506289] io scheduler noop registered
[   23.506340] io scheduler anticipatory registered
[   23.506379] io scheduler deadline registered
[   23.506472] io scheduler cfq registered
[   23.508351] isapnp: Scanning for PnP cards...
[   23.866361] isapnp: No Plug & Play device found
[   24.177713] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   24.183512] serio: i8042 AUX port at 0x60,0x64 irq 12
[   24.184207] serio: i8042 KBD port at 0x60,0x64 irq 1
[   24.184755] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[   24.185623] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.222013] 00:0e: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.230070] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   24.230660] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   24.230698] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   24.232276] mice: PS/2 mouse device common for all mice
[   24.234539] EISA: Probing bus 0 at eisa.0
[   24.234595] Cannot allocate resource for EISA slot 1
[   24.234700] EISA: Detected 0 cards.
[   24.235034] NET: Registered protocol family 2
[   24.256106] input: AT Translated Set 2 keyboard as /class/input/input0
[   24.274127] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[   24.275816] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[   24.276488] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[   24.277151] TCP: Hash tables configured (established 8192 bind 8192)
[   24.277178] TCP reno registered
[   24.278074] TCP bic registered
[   24.278152] NET: Registered protocol family 1
[   24.278215] NET: Registered protocol family 8
[   24.278236] NET: Registered protocol family 20
[   24.278404] Using IPI Shortcut mode
[   24.278687] Freeing unused kernel memory: 288k freed
[   24.925509] vga16fb: initializing
[   24.925563] vga16fb: mapped to 0xc00a0000
[   25.107304] Console: switching to colour frame buffer device 80x25
[   25.107353] fb0: VGA16 VGA frame buffer device
[   26.516069] Capability LSM initialized
[   33.582147] usbcore: registered new driver usbfs
[   33.586280] usbcore: registered new driver hub
[   33.603820] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   33.607983] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   33.611584] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[   33.611653] ohci_hcd 0000:00:0b.0: irq 11, io mem 0xf7fff000
[   34.178511] hub 1-0:1.0: USB hub found
[   34.178696] hub 1-0:1.0: 2 ports detected
[   34.867879] Probing IDE interface ide0...
[   35.284144] hda: IBM-IC25N020ATDA04-0, ATA DISK drive
[   35.955958] Probing IDE interface ide1...
[   36.516059] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   36.599384] hda: max request size: 128KiB
[   36.831530] hda: 39070080 sectors (20003 MB) w/1806KiB Cache, CHS=38760/16/63
[   36.831576] hda: cache flushes not supported
[   36.832995]  hda: hda1 hda2 < hda5 hda6 hda7 hda8 hda9 > hda3 hda4
[   38.733567] Attempting manual resume
[   38.883214] EXT3-fs: INFO: recovery required on readonly filesystem.
[   38.883254] EXT3-fs: write access will be enabled during recovery.
[   51.080446] EXT3-fs: hda3: orphan cleanup on readonly fs
[   51.080533] ext3_orphan_cleanup: deleting unreferenced inode 17044
[   51.080999] ext3_orphan_cleanup: deleting unreferenced inode 112237
[   51.081101] EXT3-fs: hda3: 2 orphan inodes deleted
[   51.081126] EXT3-fs: recovery complete.
[   51.081166] kjournald starting.  Commit interval 5 seconds
[   51.163579] EXT3-fs: mounted filesystem with ordered data mode.
[   82.712671] PCI: IRQ 0 for device 0000:00:02.0 doesn't match PIRQ mask - try pci=usepirqmask
[   82.712728] PCI: No IRQ known for interrupt pin A of device 0000:00:02.0. Please try using pci=biosirq.
[   82.712798] Yenta: CardBus bridge found at 0000:00:02.0 [1179:0001]
[   82.712859] Yenta: no PCI IRQ, CardBus support disabled for this socket.
[   82.712877] Yenta: check your BIOS CardBus, BIOS IRQ or ACPI settings.
[   92.504064] BUG: soft lockup detected on CPU#0!
[   92.504103] 
[   92.504119] Pid: 2743, comm:             modprobe
[   92.504142] EIP: 0060:[<c01214f7>] CPU: 0
[   92.504193] EIP is at __do_softirq+0x47/0xb0
[   92.504219]  EFLAGS: 00000202    Not tainted  (2.6.15-53-386)
[   92.504246] EAX: c4db6000 EBX: 00000002 ECX: 00000000 EDX: 00000002
[   92.504275] ESI: c0400700 EDI: 0000000a EBP: c4eaa000 DS: 007b ES: 007b
[   92.504312] CR0: 8005003b CR2: b7f8a000 CR3: 04833000 CR4: 00000010
[   92.504372]  [<c0121595>] do_softirq+0x35/0x40
[   92.504403]  [<c0121645>] irq_exit+0x35/0x40
[   92.504437]  [<c010596f>] do_IRQ+0x1f/0x30
[   92.504488]  [<c01040aa>] common_interrupt+0x1a/0x20
[   92.504532]  [<cb0cfabe>] yenta_probe_irq+0x8e/0xe0 [yenta_socket]
[   92.504646]  [<cb0cfc9b>] yenta_get_socket_capabilities+0x4b/0x70 [yenta_socket]
[   92.504707]  [<cb0d0044>] yenta_probe+0x1b4/0x2d0 [yenta_socket]
[   92.504771]  [<c01e769c>] __pci_device_probe+0x3c/0x60
[   92.504816]  [<c01e76df>] pci_device_probe+0x1f/0x40
[   92.504856]  [<c0244c3b>] driver_probe_device+0x3b/0xc0
[   92.504897]  [<c0244d30>] __driver_attach+0x0/0x40
[   92.504929]  [<c0244d6b>] __driver_attach+0x3b/0x40
[   92.504962]  [<c0244318>] bus_for_each_dev+0x48/0x80
[   92.505034]  [<c0244d85>] driver_attach+0x15/0x20
[   92.505065]  [<c0244d30>] __driver_attach+0x0/0x40
[   92.505096]  [<c02447b9>] bus_add_driver+0x69/0xc0
[   92.505132]  [<c01e792a>] __pci_register_driver+0x6a/0xa0
[   92.505172]  [<cb02800f>] yenta_socket_init+0xf/0x12 [yenta_socket]
[   92.505226]  [<c013826f>] sys_init_module+0x9f/0x1d0
[   92.505272]  [<c0103049>] syscall_call+0x7/0xb
[   93.239377] irq 11: nobody cared (try booting with the "irqpoll" option)
[   93.239428]  [<c013eee2>] __report_bad_irq+0x22/0x80
[   93.239469]  [<c013efd8>] note_interrupt+0x68/0xc0
[   93.239506]  [<c013e89c>] __do_IRQ+0xbc/0xe0
[   93.239563]  [<c010596a>] do_IRQ+0x1a/0x30
[   93.239595]  [<c01040aa>] common_interrupt+0x1a/0x20
[   93.239636]  [<c01214f7>] __do_softirq+0x47/0xb0
[   93.239670]  [<c0121595>] do_softirq+0x35/0x40
[   93.239699]  [<c0121645>] irq_exit+0x35/0x40
[   93.239728]  [<c010596f>] do_IRQ+0x1f/0x30
[   93.239756]  [<c01040aa>] common_interrupt+0x1a/0x20
[   93.239799]  [<cb0cfabe>] yenta_probe_irq+0x8e/0xe0 [yenta_socket]
[   93.239872]  [<cb0cfc9b>] yenta_get_socket_capabilities+0x4b/0x70 [yenta_socket]
[   93.239934]  [<cb0d0044>] yenta_probe+0x1b4/0x2d0 [yenta_socket]
[   93.239996]  [<c01e769c>] __pci_device_probe+0x3c/0x60
[   93.240037]  [<c01e76df>] pci_device_probe+0x1f/0x40
[   93.240076]  [<c0244c3b>] driver_probe_device+0x3b/0xc0
[   93.240113]  [<c0244d30>] __driver_attach+0x0/0x40
[   93.240143]  [<c0244d6b>] __driver_attach+0x3b/0x40
[   93.240176]  [<c0244318>] bus_for_each_dev+0x48/0x80
[   93.240228]  [<c0244d85>] driver_attach+0x15/0x20
[   93.240259]  [<c0244d30>] __driver_attach+0x0/0x40
[   93.240290]  [<c02447b9>] bus_add_driver+0x69/0xc0
[   93.240325]  [<c01e792a>] __pci_register_driver+0x6a/0xa0
[   93.240362]  [<cb02800f>] yenta_socket_init+0xf/0x12 [yenta_socket]
[   93.240415]  [<c013826f>] sys_init_module+0x9f/0x1d0
[   93.240452]  [<c0103049>] syscall_call+0x7/0xb
[   93.240496] handlers:
[   93.240512] [<cb096720>] (usb_hcd_irq+0x0/0x60 [usbcore])
[   93.240757] Disabling IRQ #11
[   93.336883] Yenta: ISA IRQ mask 0x06b8, PCI irq 0
[   93.336914] Socket status: 30000011
[   93.729982] PCI: IRQ 0 for device 0000:00:02.1 doesn't match PIRQ mask - try pci=usepirqmask
[   93.730037] PCI: No IRQ known for interrupt pin B of device 0000:00:02.1. Please try using pci=biosirq.
[   93.730113] Yenta: CardBus bridge found at 0000:00:02.1 [1179:0001]
[   93.730170] Yenta: no PCI IRQ, CardBus support disabled for this socket.
[   93.730188] Yenta: check your BIOS CardBus, BIOS IRQ or ACPI settings.
[   93.886011] Yenta: ISA IRQ mask 0x06b8, PCI irq 0
[   93.886048] Socket status: 30000011
[   94.614243] input: PS/2 Generic Mouse as /class/input/input1
[   95.326791] irda_init()
[   95.326920] NET: Registered protocol family 23
[   95.509090] input: PC Speaker as /class/input/input2
[   96.431007] IrDA: Registered device irda0
[   96.431047] toshoboe: Using multiple tasks, version $Id: donauboe.c V2.18 ven jan 10 03:14:16 2003$
[   96.513470] Floppy drive(s): fd0 is 1.44M
[   96.518059] pccard: PCMCIA card inserted into slot 0
[   96.529181] FDC 0 is an 8272A
[   97.351474] pccard: PCMCIA card inserted into slot 1
[   97.810675] parport: PnPBIOS parport detected.
[   97.810817] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   98.352713] Real Time Clock Driver v1.12
[  100.844081] cs: IO port probe 0x100-0x3af: excluding 0x220-0x22f 0x330-0x337 0x370-0x37f 0x388-0x38f
[  100.845918] cs: IO port probe 0x3e0-0x4ff: excluding 0x480-0x48f 0x4d0-0x4d7
[  100.847159] cs: IO port probe 0x820-0x8ff: clean.
[  100.848179] cs: IO port probe 0xc00-0xcf7: clean.
[  100.850789] cs: IO port probe 0xa00-0xaff: clean.
[  100.851998] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[  100.864024] pcmcia: registering new device pcmcia1.0
[  100.874198] cs: IO port probe 0x100-0x3af: excluding 0x220-0x22f 0x330-0x337 0x370-0x37f 0x388-0x38f
[  100.876346] cs: IO port probe 0x3e0-0x4ff: excluding 0x480-0x48f 0x4d0-0x4d7
[  100.877438] cs: IO port probe 0x820-0x8ff: clean.
[  100.878441] cs: IO port probe 0xc00-0xcf7: clean.
[  100.881235] cs: IO port probe 0xa00-0xaff: clean.
[  100.882281] cs: memory probe 0xa0000000-0xa0ffffff: excluding 0xa0000000-0xa00fffff
[  100.891820] pcmcia: registering new device pcmcia0.0
[  102.307201] airo:  Probing for PCI adapters
[  102.311963] airo:  Finished probing for PCI adapters
[  104.003711] airo: cmd= 111
[  104.003749] airo: status= 7f11
[  104.003764] airo: Rsp0= 2
[  104.003777] airo: Rsp1= 0
[  104.003790] airo: Rsp2= 0
[  104.003809] airo: Doing fast bap_reads
[  104.030324] airo: MAC enabled eth0 0:40:96:36:5c:90
[  104.031293] eth0: index 0x05: Vcc 5.0, Vpp 5.0, irq 3, io 0x0100-0x013f
[  104.083219] eth1: 3Com 3c589, io 0x300, irq 4, hw_addr 00:10:5A:FC:7D:29
[  104.083275]   8K FIFO split 5:3 Rx:Tx, auto xcvr
[  104.473810] Setting key 0
[  106.598632] NET: Registered protocol family 17
[  106.911199] lp0: using parport0 (interrupt-driven).
[  107.293410] fuse init (API version 7.3)
[  107.957484] Adding 465844k swap on /dev/hda5.  Priority:-1 extents:1 across:465844k
[  109.292489] EXT3 FS on hda3, internal journal
[  169.353256] kjournald starting.  Commit interval 5 seconds
[  169.353626] EXT3 FS on hda1, internal journal
[  169.353682] EXT3-fs: mounted filesystem with ordered data mode.
[  169.407685] kjournald starting.  Commit interval 5 seconds
[  169.408606] EXT3 FS on hda8, internal journal
[  169.408648] EXT3-fs: mounted filesystem with ordered data mode.
[  169.441265] kjournald starting.  Commit interval 5 seconds
[  169.441487] EXT3 FS on hda7, internal journal
[  169.441535] EXT3-fs: mounted filesystem with ordered data mode.
[  169.483675] kjournald starting.  Commit interval 5 seconds
[  169.483822] EXT3 FS on hda9, internal journal
[  169.483864] EXT3-fs: mounted filesystem with ordered data mode.
[  169.521633] kjournald starting.  Commit interval 5 seconds
[  169.523698] EXT3 FS on hda4, internal journal
[  169.523739] EXT3-fs: mounted filesystem with ordered data mode.
[  169.565131] kjournald starting.  Commit interval 5 seconds
[  169.566842] EXT3 FS on hda6, internal journal
[  169.566891] EXT3-fs: mounted filesystem with ordered data mode.
[  181.765246] ip_tables: (C) 2000-2002 Netfilter core team
[  206.189848] ppdev: user-space parallel port driver
[  207.591274] apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
[  300.219268] eth1: flipped to 10base2
[  336.214274] eth1: coax cable problem
[  367.975012] NET: Registered protocol family 10
[  367.976098] lo: Disabled Privacy Extensions
[  367.978352] IPv6 over IPv4 tunneling driver
[  378.200810] eth0: no IPv6 routers present
[  378.232478] eth1: no IPv6 routers present
hutchp@cassiopeia:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.2
Release:	8.04
Codename:	hardy
hutchp@cassiopeia:~$ 

Grub Menu;-
## ## End Default Options ##

title           Ubuntu 8.04.2, kernel 2.6.24-24-386
root            (hd0,0)
kernel          /vmlinuz-2.6.24-24-386 root=/dev/hda3 ro quiet splash noapic
initrd          /initrd.img-2.6.24-24-386

title           Ubuntu 8.04.2, kernel 2.6.24-24-386 (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.24-24-386 root=/dev/hda3 ro single irqpoll noapic
initrd          /initrd.img-2.6.24-24-386

title           Ubuntu 8.04.2, kernel 2.6.24-23-386
root            (hd0,0)
kernel          /vmlinuz-2.6.24-23-386 root=/dev/hda3 ro quiet splash irqpoll n$
initrd          /initrd.img-2.6.24-23-386

title           Ubuntu 8.04.2, kernel 2.6.24-23-386 (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.24-23-386 root=/dev/hda3 ro single irqpoll noapic
initrd          /initrd.img-2.6.24-23-386

title           Ubuntu 8.04.2, kernel 2.6.15-53-386
root            (hd0,0)
kernel          /vmlinuz-2.6.15-53-386 root=/dev/hda3 ro quiet splash irqpoll n$
initrd          /initrd.img-2.6.15-53-386

title           Ubuntu 8.04.2, kernel 2.6.15-53-386 (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.15-53-386 root=/dev/hda3 ro single irqpoll noapic
initrd          /initrd.img-2.6.15-53-386

title           Ubuntu 8.04.2, kernel 2.6.15-26-386
root            (hd0,0)
kernel          /vmlinuz-2.6.15-53-386 root=/dev/hda3 ro single irqpoll noapic
initrd          /initrd.img-2.6.15-26-386

title           Ubuntu 8.04.2, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.15-26-386 root=/dev/hda3 ro single irqpoll noapic
initrd          /initrd.img-2.6.15-26-386

title           Ubuntu 8.04.2, memtest86+
root            (hd0,0)
kernel          /memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

My output from mount -av:
root@cassiopeia:/# mount -av
mount: proc already mounted on /proc
mount: UUID=3ca3efc4-c299-4f1a-ad9d-ff5feea3725a already mounted on /boot
mount: UUID=7cfca44c-fa15-4568-96b9-872477657776 already mounted on /home
mount: UUID=018b3f84-ce41-4bc4-8233-d5ecd1d644bf already mounted on /media/hda7
mount: UUID=bb74b41b-7e55-4bb5-95b2-30c5b3d00c5f already mounted on /media/hda9
mount: UUID=8a113530-31af-4386-ad4c-d9ab53a86b6d already mounted on /usr
mount: UUID=9175213c-840c-4220-a2c3-93c8df05783f already mounted on /var
mount: mount point /win/pen does not exist
root@cassiopeia:/# 

added syslog output:
May 22 08:59:32 cassiopeia kernel: [ 2667.121482] usb 1-1: USB disconnect, address 2
May 22 08:59:32 cassiopeia NetworkManager: <debug> [1242979172.619577] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1241_1177_noserial_if0'). 
May 22 08:59:32 cassiopeia NetworkManager: <debug> [1242979172.657979] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1241_1177_noserial_usbraw'). 
May 22 08:59:32 cassiopeia NetworkManager: <debug> [1242979172.689038] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1241_1177_noserial'). 
May 22 08:59:49 cassiopeia kernel: [ 2683.803077] usb 1-1: new full speed USB device using ohci_hcd and address 3
May 22 08:59:49 cassiopeia NetworkManager: <debug> [1242979189.562306] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5dc_a701_3563BF01112659150707'). 
May 22 08:59:50 cassiopeia kernel: [ 2684.909912] SCSI subsystem initialized
May 22 08:59:50 cassiopeia kernel: [ 2685.005245] Initializing USB Mass Storage driver...
May 22 08:59:50 cassiopeia kernel: [ 2685.011254] scsi0 : SCSI emulation for USB Mass Storage devices
May 22 08:59:50 cassiopeia kernel: [ 2685.013915] usb-storage: device found at 3
May 22 08:59:50 cassiopeia kernel: [ 2685.013941] usb-storage: waiting for device to settle before scanning
May 22 08:59:50 cassiopeia kernel: [ 2685.014025] usbcore: registered new driver usb-storage
May 22 08:59:50 cassiopeia kernel: [ 2685.014053] USB Mass Storage support registered.
May 22 08:59:51 cassiopeia NetworkManager: <debug> [1242979191.204089] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5dc_a701_3563BF01112659150707_if0'). 
May 22 08:59:51 cassiopeia NetworkManager: <debug> [1242979191.697361] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5dc_a701_3563BF01112659150707_usbraw'). 
May 22 08:59:55 cassiopeia kernel: [ 2690.034436]   Vendor: LEXAR     Model: JD FIREFLY        Rev: 1100
May 22 08:59:55 cassiopeia kernel: [ 2690.034525]   Type:   Direct-Access                      ANSI SCSI revision: 00
May 22 08:59:55 cassiopeia kernel: [ 2690.066325] usb-storage: device scan complete
May 22 08:59:55 cassiopeia kernel: [ 2690.204750] Driver 'sd' needs updating - please use bus_type methods
May 22 08:59:55 cassiopeia kernel: [ 2690.294378] SCSI device sda: 7864320 512-byte hdwr sectors (4027 MB)
May 22 08:59:55 cassiopeia kernel: [ 2690.320263] sda: Write Protect is off
May 22 08:59:55 cassiopeia kernel: [ 2690.320637] sda: Mode Sense: 43 00 00 00
May 22 08:59:55 cassiopeia kernel: [ 2690.320962] sda: assuming drive cache: write through
May 22 08:59:55 cassiopeia kernel: [ 2690.402389] SCSI device sda: 7864320 512-byte hdwr sectors (4027 MB)
May 22 08:59:55 cassiopeia kernel: [ 2690.430952] sda: Write Protect is off
May 22 08:59:55 cassiopeia kernel: [ 2690.431328] sda: Mode Sense: 43 00 00 00
May 22 08:59:55 cassiopeia kernel: [ 2690.431654] sda: assuming drive cache: write through
May 22 08:59:56 cassiopeia kernel: [ 2690.432061]  sda: unknown partition table
May 22 08:59:56 cassiopeia kernel: [ 2690.539810] sd 0:0:0:0: Attached scsi removable disk sda
May 22 08:59:56 cassiopeia kernel: [ 2690.707225] sd 0:0:0:0: Attached scsi generic sg0 type 0
May 22 08:59:56 cassiopeia NetworkManager: <debug> [1242979196.362348] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5dc_a701_3563BF01112659150707_if0_scsi_host'). 
May 22 08:59:56 cassiopeia NetworkManager: <debug> [1242979196.489993] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5dc_a701_3563BF01112659150707_if0_scsi_host_scsi_device_lun0'). 
May 22 08:59:57 cassiopeia NetworkManager: <debug> [1242979197.357748] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5dc_a701_3563BF01112659150707_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
May 22 09:00:02 cassiopeia NetworkManager: <debug> [1242979202.631211] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_30F4_0B65'). 
May 22 09:00:02 cassiopeia NetworkManager: <debug> [1242979202.744057] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_LEXAR_JD_FIREFLY_3563BF01112659150707_0_0'). 

May 22 09:02:04 cassiopeia kernel: [ 2819.466930] FAT: Unrecognized mount option "flush" or missing value

let me know what issues you see, maybe i'm missing the glaring error.....

---

### Post by Zimmer on 2009-05-22
First error:
mount: mount point /win/pen does not exist

you have not created the mount point for fstab to mount it at boot .
Try creating that folder first and rebooting with the stick in place.

Also

in your log
May 22 09:02:04 cassiopeia kernel: [ 2819.466930] FAT: Unrecognized mount option "flush" or missing value
See 
[http://www.niftiestsoftware.com/?p=26#more-26](http://www.niftiestsoftware.com/?p=26#more-26)
which refers to an older kernel problem..

But...
> to get USB working before i have edited the Grub to include noapic and Irqpoll, which solved it, but now its not working with these entries in grub. i can see the devices coming in and out of the usb list, but it is unmountable, the filesystem is Fat32

there is this message in your logs:
> [ 23.496720] PCI: IRQ 0 for device 0000:00:02.0 doesn't match PIRQ mask - try pci=usepirqmask
[ 23.496757] PCI: No IRQ known for interrupt pin A of device 0000:00:02.0. Please try using pci=biosirq.
[ 23.496798] PCI: Setting latency timer of device 0000:00:02.0 to 64
[ 23.496835] PCI: IRQ 0 for device 0000:00:02.1 doesn't match PIRQ mask - try pci=usepirqmask
[ 23.496868] PCI: No IRQ known for interrupt pin B of device 0000:00:02.1. Please try using pci=biosirq.

So it might be worth trying either of those options in GRUB...

(grasping at straws as I cannot find anything definitive yet, sorry...)
Have a read to see if any of this (and the links from it) can point the way forward..
[http://www.linux-usb.org/FAQ.html#ts3](http://www.linux-usb.org/FAQ.html#ts3)

---

