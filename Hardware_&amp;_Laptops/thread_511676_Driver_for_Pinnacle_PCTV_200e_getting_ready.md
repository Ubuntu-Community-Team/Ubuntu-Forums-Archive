---
title: "Driver for Pinnacle PCTV 200e getting ready"
date: 2007-07-28
forum: Hardware &amp; Laptops
---

### Post by Kubunteando on 2007-07-28
There is hope for the Digital DVB-T tuner from Pinnacle, the PCTV 200e in Linux.

Just today I started to be able to tune the channels, watch some TV channels and listen to some digital radio channels.

Still it is in beta development stage, but there has been a lot of progress in the last weeks.

If someone is interested in testing the driver or helping in the development just post here.

---

### Post by meneiye on 2007-08-11
I dont speak english, sorry.

Funciona la tarjeta Pinnacle PCTV Dual DVB-T Pro PCI en ubuntu?

Gracias y espero su respuesta.

---

### Post by Kubunteando on 2007-08-12
Parece que no funciona todavia.

Echale un ojo a:

[http://linuxtv.org/wiki/index.php/DVB-T_PCI_Cards](http://linuxtv.org/wiki/index.php/DVB-T_PCI_Cards)

Las tarjetas Pinnacle son de las menos soportadas, el fabricante no saca drivers para Linux, ni tampoco ofrece las especificaciones.

Mi error fue comprar una Pinnacle (la compre cuando todavia usaba Windows), y al final me toco ayudar a desarrollar el driver. Ahora ya puedo usarla tambien en Linux.

Asi que he aprendido la leccion, es mejor compar HW que sea mas comopatible, o al menos que tenga mas soporte y este mas probado.

Tienes pocas opciones:

1- ser paciente y esperar a que alguien desarrolle el driver, puede pasar facilmente mas de un año, o puede que no se desarolle nunca...

2- ayudar a desarrollar el driver

3- comparar otra tarjeta. En la pagina web de arriba puedes encontrar las que estan soportadas

---

### Post by Kubunteando on 2007-08-12
The driver is ready for testing. Check:

[http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_200e](http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_200e)

What is working this far:

- you can scan channels (I have tested it with Kaffeine 0.84)
  You may not get all the channels if they requiere finetunning

- View TV and listen to digital radio

- driver is quite stable. In my opinion more than the Windows one.

What does not work this far:

- remote control

Enjoy it. And let us know the results in your case.

---

### Post by Kubunteando on 2007-08-16
My colleague said that the Pinnalce PCTV 200e is the same as the following ones:

PCTV 260e, the PCTV 60e and the "PCTV DVB-T Pro USB.

So you may want also to give a try to the driver on those ones.

---

### Post by blutch on 2007-09-12
Hello,

I have a pctv 60e. How do I test with your driver ?
I get the lastest V4L-DVB by : 
hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
cd v4l-dvb
make
make install

How do I add the [http://freeznet.ath.cx:81/files/pctv200e-update1.zip](http://freeznet.ath.cx:81/files/pctv200e-update1.zip) files ?

Regards,
Blutch

---

### Post by Kubunteando on 2007-09-30
Hi,

have a try. You have to overwrite the files in:
v4l-dvb-pinnacle200e-28fd6b96660d/linux/drivers/media/dvb/pctv200e

And build again with "make".

Since there was an update on Feisty about 2 months ago, something changed in the kernel or in v4linux, and it does not compile work fine any more.

I have to check what has changed. Probably some function in v4linux have been replaced.

BR,
Kubunteando

---

### Post by blutch on 2007-10-12
Hello,

I tried, I can compile.
When I put the pctv 60e in USB plug that I have the following message in "dmesg" : 
usb 5-3: new high speed USB device using ehci_hcd and address 8
usb 5-3: device descriptor read/64, error -110

Do you have any idea ?

Regards

---

### Post by ritzzy79 on 2007-10-15
sorry but i am new in linux can u write an how to about install driver and configure kafeine.

i found drivers page but dont know hot to do..

tyvm
Eric

---

### Post by ritzzy79 on 2007-10-15
here the response 

~$ dmesg
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Sep 23 19:50:39 UTC 2007 (Ubuntu 2.6.20-16.32-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fef0000 end: 000000001fff0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001fff0000 size: 0000000000003000 end: 000000001fff3000 type: 4
[    0.000000] copy_e820_map() start: 000000001fff3000 size: 000000000000d000 end: 0000000020000000 type: 3
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000001000 end: 00000000fec01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffff0000 size: 0000000000010000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 131056) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131056
[    0.000000]   HighMem    131056 ->   131056
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131056
[    0.000000] On node 0 totalpages: 131056
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125969 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP (v000 KT400                                 ) @ 0x000f7780
[    0.000000] ACPI: RSDT (v001 KT400  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3000
[    0.000000] ACPI: FADT (v001 KT400  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3040
[    0.000000] ACPI: DSDT (v001 KT400  AWRDACPI 0x00001000 MSFT 0x0100000d) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] Detected 1794.925 MHz processor.
[   36.586833] Built 1 zonelists.  Total pages: 130033
[   36.586838] Kernel command line: root=UUID=9ca8b1a6-38ce-41e5-9b5b-e9f1854cb06b ro nmi_watchdog=0 quiet splash locale=it_IT
[   36.587044] Found and enabled local APIC!
[   36.587047] mapped APIC to ffffd000 (fee00000)
[   36.587052] Enabling fast FPU save and restore... done.
[   36.587055] Enabling unmasked SIMD FPU exception support... done.
[   36.587072] Initializing CPU#0
[   36.587175] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   36.588490] Console: colour VGA+ 80x25
[   36.589039] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   36.589465] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   36.609496] Memory: 508728k/524224k available (1993k kernel code, 14976k reserved, 900k data, 328k init, 0k highmem)
[   36.609508] virtual kernel memory layout:
[   36.609510]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   36.609511]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   36.609512]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   36.609514]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
[   36.609515]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   36.609517]       .data : 0xc02f2429 - 0xc03d36d4   ( 900 kB)
[   36.609518]       .text : 0xc0100000 - 0xc02f2429   (1993 kB)
[   36.609522] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   36.687098] Calibrating delay using timer specific routine.. 3593.33 BogoMIPS (lpj=7186679)
[   36.687156] Security Framework v1.0.0 initialized
[   36.687167] SELinux:  Disabled at boot.
[   36.687189] Mount-cache hash table entries: 512
[   36.687394] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[   36.687405] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   36.687408] CPU: L2 Cache: 256K (64 bytes/line)
[   36.687412] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000
[   36.687425] Compat vDSO mapped to ffffe000.
[   36.687432] Remapping vsyscall page to ffffe000
[   36.687445] Checking 'hlt' instruction... OK.
[   36.703258] SMP alternatives: switching to UP code
[   36.703622] Freeing SMP alternatives: 11k freed
[   36.703988] Early unpacking initramfs... done
[   37.054978] ACPI: Core revision 20060707
[   37.055638] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   37.057425] ACPI: setting ELCR to 0200 (from 0e20)
[   37.103256] CPU0: AMD Athlon(tm) XP 2200+ stepping 00
[   37.103269] SMP motherboard not detected.
[   37.210730] Brought up 1 CPUs
[   37.211056] Booting paravirtualized kernel on bare hardware
[   37.211171] Time: 18:26:06  Date: 09/15/107
[   37.211218] NET: Registered protocol family 16
[   37.211356] EISA bus registered
[   37.211362] ACPI: bus type pci registered
[   37.212361] PCI: PCI BIOS revision 2.10 entry at 0xfb3d0, last bus=1
[   37.212364] PCI: Using configuration type 1
[   37.212366] Setting up standard PCI resources
[   37.221923] ACPI: Interpreter enabled
[   37.221931] ACPI: Using PIC for interrupt routing
[   37.222684] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   37.222692] PCI: Probing PCI hardware (bus 00)
[   37.222791] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   37.223271] PCI quirk: region 4000-407f claimed by vt8235 PM
[   37.223275] PCI quirk: region 5000-500f claimed by vt8235 SMB
[   37.223505] Boot video device is 0000:01:00.0
[   37.223550] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   37.245424] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[   37.245767] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *9
[   37.246111] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
[   37.246453] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
[   37.246846] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0, disabled.
[   37.247211] ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0, disabled.
[   37.247600] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0, disabled.
[   37.247972] ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0, disabled.
[   37.251053] Linux Plug and Play Support v0.97 (c) Adam Belay
[   37.251074] pnp: PnP ACPI init
[   37.255362] pnp: PnP ACPI: found 14 devices
[   37.255369] PnPBIOS: Disabled by ACPI PNP
[   37.255462] PCI: Using ACPI for IRQ routing
[   37.255468] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   37.259109] spurious 8259A interrupt: IRQ7.
[   37.278433] NET: Registered protocol family 8
[   37.278436] NET: Registered protocol family 20
[   37.279198] PCI: Bridge: 0000:00:01.0
[   37.279202]   IO window: disabled.
[   37.279208]   MEM window: e4000000-e5ffffff
[   37.279212]   PREFETCH window: d0000000-dfffffff
[   37.279232] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   37.279270] NET: Registered protocol family 2
[   37.318704] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   37.318835] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   37.319126] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   37.319279] TCP: Hash tables configured (established 16384 bind 8192)
[   37.319283] TCP reno registered
[   37.330749] checking if image is initramfs... it is
[   37.986878] Freeing initrd memory: 6782k freed
[   37.987560] audit: initializing netlink socket (disabled)
[   37.987583] audit(1192472766.440:1): initialized
[   37.987737] VFS: Disk quotas dquot_6.5.1
[   37.987766] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   37.987840] io scheduler noop registered
[   37.987844] io scheduler anticipatory registered
[   37.987847] io scheduler deadline registered
[   37.987855] io scheduler cfq registered (default)
[   37.988199] isapnp: Scanning for PnP cards...
[   38.341848] isapnp: No Plug & Play device found
[   38.371539] Real Time Clock Driver v1.12ac
[   38.371613] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   38.371766] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   38.372021] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   38.372697] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   38.373083] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   38.373419] mice: PS/2 mouse device common for all mice
[   38.374230] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   38.374597] input: Macintosh mouse button emulation as /class/input/input0
[   38.374640] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   38.374645] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   38.374948] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   38.375334] serio: i8042 KBD port at 0x60,0x64 irq 1
[   38.375340] serio: i8042 AUX port at 0x60,0x64 irq 12
[   38.375501] EISA: Probing bus 0 at eisa.0
[   38.375528] Cannot allocate resource for EISA slot 4
[   38.375531] Cannot allocate resource for EISA slot 5
[   38.375546] EISA: Detected 0 cards.
[   38.405795] TCP cubic registered
[   38.405807] NET: Registered protocol family 1
[   38.405843] Using IPI No-Shortcut mode
[   38.405977] ACPI: (supports S0 S1 S4 S5)
[   38.406037]   Magic number: 11:435:443
[   38.406857] Freeing unused kernel memory: 328k freed
[   38.409662] Time: tsc clocksource has been installed.
[   38.425872] input: AT Translated Set 2 keyboard as /class/input/input1
[   39.688358] Capability LSM initialized
[   39.730796] ACPI: Fan [FAN] (on)
[   39.735681] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   39.735693] ACPI: Processor [CPU0] (supports 2 throttling states)
[   39.737752] ACPI: Thermal Zone [THRM] (52 C)
[   40.416672] ieee1394: Initialized config rom entry `ip1394'
[   40.418868] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[   40.418877] PCI: setting IRQ 10 as level-triggered
[   40.418882] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   40.471884] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[10]  MMIO=[e7000000-e70007ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[   40.503391] usbcore: registered new interface driver usbfs
[   40.503432] usbcore: registered new interface driver hub
[   40.503466] usbcore: registered new device driver usb
[   40.504725] USB Universal Host Controller Interface driver v3.0
[   40.505338] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   40.505343] PCI: setting IRQ 11 as level-triggered
[   40.505349] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   40.505366] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   40.505610] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   40.505644] uhci_hcd 0000:00:10.0: irq 11, io base 0x0000a800
[   40.505823] usb usb1: configuration #1 chosen from 1 choice
[   40.505858] hub 1-0:1.0: USB hub found
[   40.505871] hub 1-0:1.0: 2 ports detected
[   40.560612] SCSI subsystem initialized
[   40.566790] libata version 2.20 loaded.
[   40.608703] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[   40.608711] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   40.608719] PCI: VIA VLink IRQ fixup for 0000:00:10.1, from 9 to 11
[   40.608748] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   40.608781] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   40.608809] uhci_hcd 0000:00:10.1: irq 11, io base 0x0000ac00
[   40.608942] usb usb2: configuration #1 chosen from 1 choice
[   40.608975] hub 2-0:1.0: USB hub found
[   40.608988] hub 2-0:1.0: 2 ports detected
[   40.665907] via-rhine.c:v1.10-LK1.4.2 Sept-11-2006 Written by Donald Becker
[   40.712018] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   40.712039] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   40.712075] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   40.712105] uhci_hcd 0000:00:10.2: irq 10, io base 0x0000b000
[   40.712255] usb usb3: configuration #1 chosen from 1 choice
[   40.712289] hub 3-0:1.0: USB hub found
[   40.712304] hub 3-0:1.0: 2 ports detected
[   40.738869] FDC 0 is a post-1991 82077
[    4.088000] Time: acpi_pm clocksource has been installed.
[    4.088000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
[    4.088000] PCI: setting IRQ 5 as level-triggered
[    4.088000] ACPI: PCI Interrupt 0000:00:10.3[D] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[    4.088000] ehci_hcd 0000:00:10.3: EHCI Host Controller
[    4.088000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[    4.088000] ehci_hcd 0000:00:10.3: irq 5, io mem 0xe7001000
[    4.088000] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.088000] usb usb4: configuration #1 chosen from 1 choice
[    4.088000] hub 4-0:1.0: USB hub found
[    4.088000] hub 4-0:1.0: 6 ports detected
[    4.196000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[    4.196000] ACPI: PCI Interrupt 0000:00:11.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[    4.196000] PCI: VIA VLink IRQ fixup for 0000:00:11.1, from 255 to 11
[    4.196000] VP_IDE: chipset revision 6
[    4.196000] VP_IDE: not 100% native mode: will probe irqs later
[    4.196000] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[    4.196000]     ide0: BM-DMA at 0xb400-0xb407, BIOS settings: hda:DMA, hdb:DMA
[    4.196000]     ide1: BM-DMA at 0xb408-0xb40f, BIOS settings: hdc:DMA, hdd:pio
[    4.196000] Probing IDE interface ide0...
[    4.620000] hda: Maxtor 6E040L0, ATA DISK drive
[    4.920000] usb 4-4: new high speed USB device using ehci_hcd and address 2
[    5.028000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00110666455555c4]
[    5.052000] usb 4-4: configuration #1 chosen from 1 choice
[    5.080000] hdb: HL-DT-STDVD-ROM GDR8163B, ATAPI CD/DVD-ROM drive
[    5.136000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    5.824000] Probing IDE interface ide1...
[    6.248000] hdc: QUANTUM FIREBALLP LM20.5, ATA DISK drive
[    6.932000] ide1 at 0x170-0x177,0x376 on irq 15
[    6.936000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[    6.940000] eth0: VIA Rhine II at 0x1c000, 00:01:29:4e:1f:b6, IRQ 11.
[    6.944000] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
[    6.952000] hda: max request size: 128KiB
[    6.972000] hda: 80293248 sectors (41110 MB) w/2048KiB Cache, CHS=65535/16/63
[    6.972000] hda: cache flushes supported
[    6.972000]  hda: hda1 hda2 hda3 < hda5 >
[    7.000000] hdc: max request size: 128KiB
[    7.000000] hdc: 40132503 sectors (20547 MB) w/1900KiB Cache, CHS=39813/16/63, UDMA(33)
[    7.000000] hdc: cache flushes not supported
[    7.000000]  hdc:<6>hdb: ATAPI 52X DVD-ROM drive, 256kB Cache, UDMA(33)
[    7.004000] Uniform CD-ROM driver Revision: 3.20
[    7.004000]  hdc1
[    7.356000] Attempting manual resume
[    7.356000] swsusp: Resume From Partition 3:5
[    7.356000] PM: Checking swsusp image.
[    7.372000] PM: Resume from disk failed.
[    7.420000] kjournald starting.  Commit interval 5 seconds
[    7.420000] EXT3-fs: mounted filesystem with ordered data mode.
[   16.888000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   18.312000] NET: Registered protocol family 17
[   19.060000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   19.064000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.652000] Linux agpgart interface v0.102 (c) Dave Jones
[   19.684000] agpgart: Detected VIA KT400/KT400A/KT600 chipset
[   19.688000] agpgart: AGP aperture is 64M @ 0xe0000000
[   19.760000] irda_init()
[   19.760000] NET: Registered protocol family 23
[   19.948000] input: PC Speaker as /class/input/input2
[   19.992000] parport: PnPBIOS parport detected.
[   19.992000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   20.312000] nvidia: module license 'NVIDIA' taints kernel.
[   20.664000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   20.664000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[   21.096000] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   21.136000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   21.136000] PCI: VIA VLink IRQ fixup for 0000:00:11.5, from 5 to 10
[   21.136000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   21.872000] fuse init (API version 7.8)
[   21.912000] lp0: using parport0 (interrupt-driven).
[   22.012000] Adding 730916k swap on /dev/disk/by-uuid/221a6f75-36d5-4d99-a306-208828f65070.  Priority:-1 extents:1 across:730916k
[   22.132000] EXT3 FS on hda2, internal journal
[   22.360000] NET: Registered protocol family 10
[   22.360000] lo: Disabled Privacy Extensions
[   28.136000] No dock devices found.
[   28.212000] Using specific hotkey driver
[   28.336000] ibm_acpi: ec object not found
[   28.432000] input: Power Button (FF) as /class/input/input4
[   28.436000] ACPI: Power Button (FF) [PWRF]
[   28.480000] input: Power Button (CM) as /class/input/input5
[   28.488000] ACPI: Power Button (CM) [PWRB]
[   28.532000] input: Sleep Button (CM) as /class/input/input6
[   28.536000] ACPI: Sleep Button (CM) [SLPB]
[   28.560000] pcc_acpi: loading...
[   32.996000] eth0: no IPv6 routers present
[   34.420000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   34.420000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   34.420000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   35.544000] ppdev: user-space parallel port driver
[   36.428000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   36.428000] apm: overridden by ACPI.
[   39.012000] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   39.012000] vboxdrv: Successfully done.
[   39.384000] Bluetooth: Core ver 2.11
[   39.384000] NET: Registered protocol family 31
[   39.384000] Bluetooth: HCI device and connection manager initialized
[   39.384000] Bluetooth: HCI socket layer initialized
[   39.436000] Bluetooth: L2CAP ver 2.8
[   39.436000] Bluetooth: L2CAP socket layer initialized
[   39.620000] Bluetooth: RFCOMM socket layer initialized
[   39.620000] Bluetooth: RFCOMM TTY layer initialized
[   39.620000] Bluetooth: RFCOMM ver 1.8
[   50.548000] eth0: no IPv6 routers present
[   52.712000] ISO 9660 Extensions: Microsoft Joliet Level 3
[   52.984000] ISO 9660 Extensions: RRIP_1991A

but as u can see here the pc card is connect in usb>

lsusb
Bus 004 Device 002: ID 2304:020e Pinnacle Systems, Inc. [hex] 
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

I ve tried to install driver but didnt work.
anyone can help me?:confused:

---

### Post by maxter on 2007-10-18
hi..

[http://mcentral.de/hg/~mrec/v4l-dvb-pinnacle200e](http://mcentral.de/hg/~mrec/v4l-dvb-pinnacle200e)
does not seem available anymore

there is a [http://mcentral.de/hg/~mrec/v4l-dvb-experimental/](http://mcentral.de/hg/~mrec/v4l-dvb-experimental/) path

anyway there is no pctv200e directory to overwrite :(

any suggestions?

---

### Post by Lion06 on 2007-11-28
Kubunteando help us!!!!!
write something (for example a little guide) for compile and use your driver!!
so we can testing the driver :lolflag::lolflag:

---

### Post by Lion06 on 2007-11-28
is impossibile compile it!!!!!!!!!!!!!!!!!!!!!!!
i can't find dvb-usb.h and the other include file!! where are this file??:(:confused:

---

### Post by Lion06 on 2007-11-29
please, How can I create the file .fw?

---

### Post by Kubunteando on 2008-01-02
Yes, in the wiki the files seem to be missing.
I attach the updated files missing in the Wiki page (well, it seems the original linuxtv-tree link is also broken). This should be fixed as you need both to compile the driver.

Some hints to compile it:

this should be easy for those who downloaded the linuxtv tree with the PCTV 200e.

Just run in the folder you decompressed the linux-v4l (video for Linux) these commands :

make clean
make
make install

If you get no errors the driver is compiled and installed. So you are ready to plug the Pinnacle 200e into the USB port, and open for example Kaffeine. Just make a scan in the DVB dialog.

As I mentioned before I got compilation errors in Ubuntu Feisty 7.04 after the kernel update of the last September 2007. But know with Ubuntu Gutsy everything compiles and runs fine again.

To compile it you will need to have installed the kernel headers package.
So check that you have this package installed:

linux-headers-2.6.X.Y

I will check if any other kernel related package needs to be installed.

I will monitor when the links in the Wiki work again. Once those are working I will post it here.

For the Pinnalce 200e you don't need any firmware, so you don't need to create any .fw file.

---

### Post by Lion06 on 2008-01-03
I've downloaded linux4tv tree from [http://www.linuxtv.org/repo/](http://www.linuxtv.org/repo/)
i've copy pctv200e.c and pctv200e.h under /v4l/
after
make clean
make
make install

but don't work....maybe bacause it doesnt create file .o :(

---

### Post by Lion06 on 2008-01-03
the same under linux/drivers/media/video/

---

### Post by Lion06 on 2008-01-03
and under
linux/drivers/media/dvb/dvb-usb/

](*,)

---

### Post by Kubunteando on 2008-01-03
You need to download the video4linux tree prepared for the PCTV200e, the one in the Wiki which link is broken at this point. Since still the PCTV200e driver is not included in the main v4l tree. The compilation scripts are ready to generate the pctv200e driver in that one.

The tree file seems quite big to post it here, so I will try to find some temporary solution, although it will take a while, since I am on holidays until the 15th of January.

The issue is that the files need to be placed and the Make scripts need to be modified so they compile those. Once I have a proper Internet connection I will find the way to post the v4l tree I used and I will give a more detailed step-list to compile the thing right.

---

### Post by Lion06 on 2008-01-03
ok, thanks:popcorn:

---

### Post by Lion06 on 2008-01-04
now makefile and kconfig are ok...but
```

  .......
  LD [M]  /home/lion/Scrivania/0/v4l/dvb-usb-af9005.o
  LD [M]  /home/lion/Scrivania/0/v4l/dvb-usb-af9005-remote.o
  CC [M]  /home/lion/Scrivania/0/v4l/pctv200e.o
/home/lion/Scrivania/0/v4l/pctv200e.c:348: warning: 'struct dvb_int_frontend_parameters' declared inside parameter list
/home/lion/Scrivania/0/v4l/pctv200e.c:348: warning: its scope is only this definition or declaration, which is probably not what you want
/home/lion/Scrivania/0/v4l/pctv200e.c:348: warning: 'struct v4l_dvb_tuner_ops' declared inside parameter list
/home/lion/Scrivania/0/v4l/pctv200e.c: In function 'pctv200e_mt2060_tuner_set_params':
/home/lion/Scrivania/0/v4l/pctv200e.c:352: error: dereferencing pointer to incomplete type
/home/lion/Scrivania/0/v4l/pctv200e.c: In function 'pctv200e_frontend_attach':
/home/lion/Scrivania/0/v4l/pctv200e.c:372: error: 'dvb_usb_tuner_calc_regs' undeclared (first use in this function)
/home/lion/Scrivania/0/v4l/pctv200e.c:372: error: (Each undeclared identifier is reported only once
/home/lion/Scrivania/0/v4l/pctv200e.c:372: error: for each function it appears in.)
/home/lion/Scrivania/0/v4l/pctv200e.c: In function 'pctv200e_tuner_attach':
/home/lion/Scrivania/0/v4l/pctv200e.c:395: error: 'struct dvb_tuner_ops' has no member named 'fe'
/home/lion/Scrivania/0/v4l/pctv200e.c:398: warning: passing argument 1 of '__a' from incompatible pointer type
/home/lion/Scrivania/0/v4l/pctv200e.c:400: error: 'struct dvb_tuner_ops' has no member named 'fe'
/home/lion/Scrivania/0/v4l/pctv200e.c:402: error: 'struct dvb_usb_adapter' has no member named 'pll_addr'
/home/lion/Scrivania/0/v4l/pctv200e.c:403: error: 'struct dvb_usb_adapter' has no member named 'pll_desc'
/home/lion/Scrivania/0/v4l/pctv200e.c:403: error: 'dvb_pll_tded4' undeclared (first use in this function)
make[3]: *** [/home/lion/Scrivania/0/v4l/pctv200e.o] Error 1
make[2]: *** [_module_/home/lion/Scrivania/0/v4l] Error 2
make[1]: *** [default] Error 2
make: *** [all] Error 2

```

it isn't  my error now :P

Ps i've ubuntu 7.10

---

### Post by Kubunteando on 2008-01-15
I have uploaded the v4l_200e.zip file here:

[http://es.geocities.com/juanantonio_garcia_01/v4l_200e.zip](http://es.geocities.com/juanantonio_garcia_01/v4l_200e.zip)

I had to rename it because the site did not allow the original name,
So before trying to open it rename it as:

v4l-dvb-pinnacle200e-28fd6b96660d.tar.gz.tar

So you get a zipped tar file, which is the original format.

To compile the driver here you have the instructions:

1- Uncompress the above file in any of your folders

2- In the folder v4l-dvb-pinnacle200e-28fd6b96660d/linux/drivers/media/dvb/pctv200e, you will find the original pctv200e files. So overwrite those with the ones published in the Wiki. If they are not available in the Wiki, I have posted a .zip file in this same thread before New Year's Eve

3- Now you are good to compile and install the driver. So open a terminal (console), and go to the folder v4l-dvb-pinnacle200e-28fd6b96660d that it was created when you uncompressed the file in step 1), and run:

    make clean
    make
    sudo make install
    
If you did not get any compilation error you are ready to plug the PCTV200e.

Plug it and check which Kaffeine (or your favorite player) if you can open the DVB device.

It runs fine in Gutsy,

Good luck, although should be easy.

---

### Post by Lion06 on 2008-01-15
good!!!!!!!!!!!!!!!!!!
but the link don't work :P

---

### Post by Kubunteando on 2008-01-15
I have problems to publish the file.

I will try a different server and I will post the link, probably tomorrow.

---

### Post by Kubunteando on 2008-01-16
No way to put it in my web in yahoo.
For some reason, it adds an extra byte (the size of the file increases by one, and the file gets corrupted)

I am checking if there is any place I can publish it.

If you have any ideas, let me know those.

---

### Post by Lion06 on 2008-01-16
if the file is less than 10Mb you can send it into my mail, so i will be able do upload of the same file

> giovanni.biachi     at        gmail          .com

or you can send my through msn :lolflag:

---

### Post by Kubunteando on 2008-01-16
Just sent it to you.

If anybody has an idea how to put it on the Net for everybody to download, just write.

---

### Post by Lion06 on 2008-01-16
my email is empy
anyway you can use [http://rapidshare.com/](http://rapidshare.com/)  ;)

---

### Post by Kubunteando on 2008-01-17
Tried to send it twice to your address but both times I got:

<giovanni.biachi@gmail.com>:
64.233.183.27 failed after I sent the message.
Remote host said: 552 5.7.0 Illegal Attachment 7si1500815nfv.35

Probably because it is a tar file...

Now I uploaded to rapidshre, here it is the link:

[http://rapidshare.com/files/84549842/v4l-dvb-pinnacle200e-28fd6b96660d.tar.gz.tar.html](http://rapidshare.com/files/84549842/v4l-dvb-pinnacle200e-28fd6b96660d.tar.gz.tar.html)

I have downloaded and tested that I can open it and it works fine.

Let us know how the driver works for you.

---

### Post by Lion06 on 2008-01-17
with ubuntu 8.10 alpha 3 and kernel 2.6.22-14-generic.....
work!!!!!!!!!!!!!1
is incredible!!!!!

---

### Post by Lion06 on 2008-01-18
1) work, this driver should be integrated into linux tv kernel
2) you should edit che first post and re-write a new guide per newbie (like me) ^_^
3) with the kernel 2.6.24-rc5 don't work, it isn't a problem......for now :lolflag:

---

### Post by Chief677 on 2008-01-18
Hey,

I just tried to get my PCTV200e device working without a succees :-(

I did the following steps:

1) Downloaded the file "v4l-dvb-pinnacle200e-28fd6b96660d" from rapishare and extracted it
2) make && make install (compiling fine and without an error)
3) plugged the device in and got some sort of error:

```


Jan 18 23:16:13 ubuntu kernel: [  370.684000] usb 4-3: new high speed USB device using ehci_hcd and address 3
Jan 18 23:16:13 ubuntu NetworkManager: <debug> [1200694573.738147] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_2304_20e_0C22175D039B3516'). 
Jan 18 23:16:13 ubuntu kernel: [  370.816000] usb 4-3: configuration #1 chosen from 1 choice
Jan 18 23:16:13 ubuntu kernel: [  371.004000] dvb-usb: found a 'Pinnacle PCTV 200e DVB-T' in warm state.
Jan 18 23:16:13 ubuntu kernel: [  371.004000] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Jan 18 23:16:13 ubuntu kernel: [  371.008000] DVB: registering new adapter (Pinnacle PCTV 200e DVB-T)
Jan 18 23:16:13 ubuntu kernel: [  371.044000] pctv200e: crtl_msg() READ: 1 7f 0 0 0
Jan 18 23:16:13 ubuntu kernel: [  371.056000] pctv200e: pctv200e_i2c_xfer() called.
Jan 18 23:16:13 ubuntu kernel: [  371.056000] pctv200e: frontend_attach failed (mt352)
Jan 18 23:16:13 ubuntu kernel: [  371.056000] pctv200e: next: attaching tuner.
Jan 18 23:16:14 ubuntu udevd-event[6882]: run_program: '/sbin/modprobe' abnormal exit
Jan 18 23:16:14 ubuntu NetworkManager: <debug> [1200694574.019726] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_2304_20e_0C22175D039B3516_if0'). 
Jan 18 23:16:14 ubuntu kernel: [  371.088000] BUG: unable to handle kernel NULL pointer dereference at virtual address 00000114
Jan 18 23:16:14 ubuntu kernel: [  371.088000]  printing eip:
Jan 18 23:16:14 ubuntu kernel: [  371.088000] f908052d
Jan 18 23:16:14 ubuntu kernel: [  371.088000] *pde = 00000000
Jan 18 23:16:14 ubuntu kernel: [  371.088000] Oops: 0000 [#1]
Jan 18 23:16:14 ubuntu kernel: [  371.088000] SMP 
Jan 18 23:16:14 ubuntu kernel: [  371.088000] Modules linked in: mt2060 mt352 pctv200e dvb_usb dvb_core dvb_pll i2c_core af_packet binfmt_misc i915 drm rfcomm l2cap bluetooth i810fb vgastate ppdev autofs4 ipv6 speedstep_centrino cpufreq_ondemand cpufreq_powersave cpufreq_userspace cpufreq_conservative cpufreq_stats freq_table button battery sbs bay dock container ac video nsc_ircc aes_i586 dm_crypt dm_mod sbp2 lp snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event joydev pcmcia snd_seq snd_timer snd_seq_device ipw2100 irda crc_ccitt parport_pc parport ieee80211 snd soundcore yenta_socket rsrc_nonstatic pcmcia_core serio_raw ieee80211_crypt psmouse snd_page_alloc shpchp pci_hotplug iTCO_wdt iTCO_vendor_support intel_agp agpgart evdev ext3 jbd mbcache sg usb_storage ide_core libusual sr_mod cdrom sd_mod ata_piix ohci1394 ieee1394 b44 mii ata_generic libata scsi_mod ehci_hcd uhci_hcd usbcore thermal processor fan fuse apparmor
Jan 18 23:16:14 ubuntu kernel: commoncap vesafb fbcon tileblit font bitblit softcursor
Jan 18 23:16:14 ubuntu kernel: [  371.088000] CPU:    0
Jan 18 23:16:14 ubuntu kernel: [  371.088000] EIP:    0060:[<f908052d>]    Not tainted VLI
Jan 18 23:16:14 ubuntu kernel: [  371.088000] EFLAGS: 00010292   (2.6.22-14-generic #1)
Jan 18 23:16:14 ubuntu kernel: [  371.088000] EIP is at mt2060_attach+0x1d/0x360 [mt2060]
Jan 18 23:16:14 ubuntu kernel: [  371.088000] eax: 0000010c   ebx: dbf2c7e4   ecx: f9182bc0   edx: 000000d0
Jan 18 23:16:14 ubuntu kernel: [  371.088000] esi: 000004c4   edi: f9182bc0   ebp: dbf2c5d8   esp: dc1e9d58
Jan 18 23:16:14 ubuntu kernel: [  371.088000] ds: 007b   es: 007b   fs: 00d8  gs: 0033  ss: 0068
Jan 18 23:16:14 ubuntu kernel: [  371.088000] Process modprobe (pid: 6884, ti=dc1e8000 task=ddcec000 task.ti=dc1e8000)
Jan 18 23:16:14 ubuntu kernel: [  371.088000] Stack: f918181e 00000296 04c4c820 0000010c c014a114 00000001 dbf2c7e4 f9080510 
Jan 18 23:16:14 ubuntu kernel: [  371.088000]        dbf2c820 dbf2c7e0 f91813bd 000004c4 dbf2c7e4 00000000 f918b2b3 dbf2c7e4 
Jan 18 23:16:14 ubuntu kernel: [  371.088000]        00000000 dbf2c820 dbf2c7e4 f918a8ed f918c914 f9181846 dbf38440 dbf2c030 
Jan 18 23:16:14 ubuntu kernel: [  371.088000] Call Trace:
Jan 18 23:16:14 ubuntu kernel: [  371.088000]  [__symbol_get+100/112] __symbol_get+0x64/0x70
Jan 18 23:16:14 ubuntu kernel: [  371.088000]  [<f9080510>] mt2060_attach+0x0/0x360 [mt2060]
Jan 18 23:16:14 ubuntu kernel: [  371.088000]  [<f91813bd>] pctv200e_frontend_attach+0xcd/0x160 [pctv200e]
Jan 18 23:16:14 ubuntu kernel: [  371.088000]  [<f918b2b3>] dvb_usb_adapter_frontend_init+0x13/0x100 [dvb_usb]
Jan 18 23:16:14 ubuntu kernel: [  371.088000]  [<f918a8ed>] dvb_usb_device_init+0x3cd/0x610 [dvb_usb]
Jan 18 23:16:14 ubuntu kernel: [  371.088000]  [<f918105a>] pctv200e_probe+0x1a/0x30 [pctv200e]
Jan 18 23:16:14 ubuntu kernel: [  371.088000]  [<f8bb3f66>] usb_probe_interface+0x96/0xe0 [usbcore]
Jan 18 23:16:14 ubuntu kernel: [  371.088000]  [driver_probe_device+142/400] driver_probe_device+0x8e/0x190
Jan 18 23:16:14 ubuntu kernel: [  371.088000]  [__driver_attach+158/160] __driver_attach+0x9e/0xa0
Jan 18 23:16:14 ubuntu kernel: [  371.088000]  [bus_for_each_dev+59/96] bus_for_each_dev+0x3b/0x60
Jan 18 23:16:14 ubuntu kernel: [  371.088000]  [driver_attach+22/32] driver_attach+0x16/0x20
Jan 18 23:16:14 ubuntu kernel: [  371.088000]  [__driver_attach+0/160] __driver_attach+0x0/0xa0
Jan 18 23:16:14 ubuntu kernel: [  371.088000]  [bus_add_driver+138/432] bus_add_driver+0x8a/0x1b0
Jan 18 23:16:14 ubuntu kernel: [  371.088000]  [<f8bb39de>] usb_register_driver+0x8e/0x110 [usbcore]
Jan 18 23:16:14 ubuntu NetworkManager: <debug> [1200694574.072561] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_2304_20e_0C22175D039B3516_usbraw'). 
Jan 18 23:16:14 ubuntu kernel: [  371.088000]  [__link_module+0/32] __link_module+0x0/0x20
Jan 18 23:16:14 ubuntu NetworkManager: <debug> [1200694574.151454] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_2304_20e_0C22175D039B3516_dvb'). 
Jan 18 23:16:14 ubuntu kernel: [  371.088000]  [<f8ba9018>] pctv200e_module_init+0x18/0x48 [pctv200e]
Jan 18 23:16:14 ubuntu NetworkManager: <debug> [1200694574.153421] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_2304_20e_0C22175D039B3516_dvb_0'). 
Jan 18 23:16:14 ubuntu kernel: [  371.088000]  [blocking_notifier_call_chain+23/32] blocking_notifier_call_chain+0x17/0x20
Jan 18 23:16:14 ubuntu NetworkManager: <debug> [1200694574.154981] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_2304_20e_0C22175D039B3516_dvb_1'). 
Jan 18 23:16:14 ubuntu kernel: [  371.088000]  [sys_init_module+337/6656] sys_init_module+0x151/0x1a00
Jan 18 23:16:14 ubuntu kernel: [  371.088000]  [prio_tree_insert+31/592] prio_tree_insert+0x1f/0x250
Jan 18 23:16:14 ubuntu kernel: [  371.088000]  [sysenter_past_esp+107/169] sysenter_past_esp+0x6b/0xa9
Jan 18 23:16:14 ubuntu kernel: [  371.088000]  [clip_ioctl+1088/1296] clip_ioctl+0x440/0x510
Jan 18 23:16:14 ubuntu kernel: [  371.088000]  =======================
Jan 18 23:16:14 ubuntu kernel: [  371.088000] Code: e9 39 fd ff ff 89 f6 8d bc 27 00 00 00 00 55 89 d5 57 ba d0 00 00 00 56 89 cf 53 83 ec 18 8b 74 24 2c 89 44 24 0c 66 89 74 24 0a <8b> 40 08 c6 44 24 17 00 89 44 24 10 b8 70 9a 3d c0 e8 fd c2 0f 
Jan 18 23:16:14 ubuntu kernel: [  371.088000] EIP: [<f908052d>] mt2060_attach+0x1d/0x360 [mt2060] SS:ESP 0068:dc1e9d58


```

I'm running Gutsy 32 Bit
I assumed that the file is already patched with the new driver, hope so :-)

c,Ya

---

### Post by Chief677 on 2008-01-18
k, I was thinking the file from rapidshare is already patched, it wasn't so I patched it with the attached file from a previous post.
And it works fine :-) kaffeine detects the device, but I have no DVB-T signals here, so I have to test the real TV watching on another time but, it seems to work!

THX for this thread :-)

EDIT: I just connected the tv device to the antenna on the rooftop and it's working fine, i can watch all Channels which are available in my region without any problems; EPG and changing the audio track is working too :-D

c,Ya

---

### Post by Kubunteando on 2008-01-19
Try to schedule the recording of some program with Kaffeine, that is also working fine.
Even you can watch a different channel while recording another channel at the same time.

---

### Post by procart on 2008-01-20
Kubunteando - thank you for the fine job :guitar: 

it works prima with suse10.3-64bit (kernel 2.6.22.13-0.3-default) - here was just a small problem in compilation in script:
File not found: /lib/modules/2.6.22.13-0.3-default/build/include/linux/netdevice
.h at scripts/make_config_compat.pl line 15.

But it works also without "netdevice.h" :)

Do you have some ideas or plans about implementation of the remote-control support?

mfg

---

### Post by lukemack on 2008-01-21
Hi,

Has anyone tried this **successfully** with the pinnacle PCTV 60e (External USB card) or does anyone know of a working driver for the 60e?

Many thanks,

Luke.

---

### Post by Kubunteando on 2008-01-21
Good news.

The issue with the remote control is that I have to double check it, cause it seems mine it is not working, so I cannot do much about that...

The Pinnacle 60e I was told to be basically same as the 200e, but the driver has not been reported to be working other than the Pinnacle 200e, as far as I know. You may try it, but I don't have any means to support you, since I don't have that tuner. You may try it though, but the chances it works may be small.

If you know something about programming in C, you can have a look at the source code.

---

### Post by lukemack on 2008-01-21
Thanks. I went on #linuxtv on IRC and asked there. The consensus seemed to be that if the driver could be forced to recognise the 60e, it should work. Could you let me know which file would be the one to change in the source? Someone on IRC said there should be a table which can be altered and this should be a trivial change?

thanks

---

### Post by Kubunteando on 2008-01-22
The files having the source code are in the pctv200e folder, and they are: 
pctv200e.h 
pctv200e.c

Check the ones in the zip file in a previous post on this thread.
The ones in the v4l tar file are the original ones, so they need to be overwritten with the ones in the zip file. The location of those files in the v4l tar file is mentioned above.

What I don't see it clear (because I did not work in the driver since the beginning, and I am no expert) is what to change exactly.

I can tell it must be related to the codes that appear when you execute a "lsusb" in a Terminal.
But I cannot see those ones for the PCTV200e coded in the driver. Those codes should say which driver to load when you plug the device.

I can give you more hints once we clear up how to change those.

---

### Post by Kubunteando on 2008-01-22
Seems that the links to download the files are working again in the Wiki:

[http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_200e](http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_200e)

---

### Post by maxter on 2008-01-29
yes.. the link for patched files seems to work again, but  that to mrec mercurial repos doee not...

it should be useful to modify the linux-tv page, as already requested in other posts.
it should be useful also add a howto that should help novice linux user to compile the kernel modules with mercurial

anyway...
many thanks.. i will try to test a pctv dvb-t usb pro :)

many thanks :)

---

### Post by procart on 2008-02-01
> **Kubunteando said:**
> Good news.

The issue with the remote control is that I have to double check it, cause it seems mine it is not working, so I cannot do much about that...



have good news for pctv200e users:

i've installed usb-sniffer under windows and after some hours of tests found correct parameters and key-codes for pctv200e + remote contol (model: 
[http://lirc.sourceforge.net/remotes/pinnacle_systems/RC1144201_00](http://lirc.sourceforge.net/remotes/pinnacle_systems/RC1144201_00)).

it works with kaffeine ! only channels buttons at the moment but the main problem is solved ! 
i'm going to make some extra-tests and then can upload the modified pctv200e.c somewhere on rapidshare.

nice weekend

---

### Post by TomvE on 2008-02-06
He guys,

I'm currently playing around with this driver to make it work for the Pinnacle PCTV 60e (which has the same hardware as the 200e), but I'm a bit stuck here.
This is what I did so far:
- downloaded the earlier mentioned .tar and the modified pctv200e files.
- overwritten the original pctv200e files with the modified ones.
- added an extra line in dvb-usb-ids.h:
[INDENT]```
#define USB_PID_PCTV_60E 0x0216
``` (that is the product ID I can see for the 60e in the device manager)[/INDENT] 
- added an extra line in the pctv200e_table struct inside pctv200e.c:
[INDENT]```
{ USB_DEVICE(USB_VID_PINNACLE, USB_PID_PCTV_60E) },
```[/INDENT]
- then I did a make && make install

After I plug in the device I can see the following messages in dmesg:
```
usb 1-1: new full speed USB device using ohci hcd and address 2
pctv200e: usb_device_init successfull
usbcore: registered new interface driver dvb_usb_pctv200e
pctv200e: usb_register successfull
```

But that's it and in the device manager the device still shows up as DVB-T, rather than the full name.
I'm a newbie to this, but has anyone got any clues?

---

### Post by procart on 2008-02-09
hi
there is a link with modified (in part remote control support) pctv200e.c.
I tested it during last week with suse10.3/64bit + kde3 + lirc + kaffeine.
You get  lircd.conf in the archive too.

[http://rapidshare.com/files/90467895/pctv200e.tar.gz.html](http://rapidshare.com/files/90467895/pctv200e.tar.gz.html)

mfg

---

### Post by procart on 2008-02-09
> **TomvE said:**
> He guys,

I'm currently playing around with this driver to make it work for the Pinnacle PCTV 60e (which has the same hardware as the 200e), but I'm a bit stuck here.
This is what I did so far:
- downloaded the earlier mentioned .tar and the modified pctv200e files.
- overwritten the original pctv200e files with the modified ones.
- added an extra line in dvb-usb-ids.h:
[INDENT]```
#define USB_PID_PCTV_60E 0x0216
``` (that is the product ID I can see for the 60e in the device manager)[/INDENT] 
- added an extra line in the pctv200e_table struct inside pctv200e.c:
[INDENT]```
{ USB_DEVICE(USB_VID_PINNACLE, USB_PID_PCTV_60E) },
```[/INDENT]
- then I did a make && make install

After I plug in the device I can see the following messages in dmesg:
```
usb 1-1: new full speed USB device using ohci hcd and address 2
pctv200e: usb_device_init successfull
usbcore: registered new interface driver dvb_usb_pctv200e
pctv200e: usb_register successfull
```

But that's it and in the device manager the device still shows up as DVB-T, rather than the full name.
I'm a newbie to this, but has anyone got any clues?

hi.
are you sure that 60e uses same addresses/commands and command sequences like 200e ?
i've used a usb-sniffer program to get some details about rc-support and have to say -
it's not so easy...

imho - you have to check the basic things before to care the device-name problem...

---

### Post by TomvE on 2008-02-10
I'm pretty sure that it is the same device. All the documentation indicates this: [http://www.linuxtv.org/v4lwiki/index.php/Pinnacle/60e](http://www.linuxtv.org/v4lwiki/index.php/Pinnacle/60e)

And I'm not worried about the device name, but I just think that it has not loaded all the correct modules to recognize the device.
As far as I can see using lmod it has loaded the dvb-usb, mt352, mt2060 and pctv200e modules. Does it need any more specific dvb/v4l modules?

---

### Post by procart on 2008-02-11
hi. 
i'd like to help but i'm not linux-driver developer.

What does the "same device" mean ? - may be 60e has same tuner, modulator 
but what is with the "usb device contoller" (CYPRESS_FX2 in case 200e) ?

PS here is my lsmode - 

suse64home:~ # lsmod | grep dvb
dvb_usb                41484  1 pctv200e
dvb_core              102320  1 dvb_usb
firmware_class         27520  2 microcode,dvb_usb
dvb_pll                33540  2 pctv200e,dvb_usb
i2c_core               43648  7 w83627ehf,i2c_isa,mt2060,mt352,dvb_usb,dvb_pll,i2c_i801
usbcore               156456  7 usbhid,pctv200e,dvb_usb,usb_storage,ehci_hcd,uhci_hcd



PPS i've checked your url - it has the same CYPRESS_FX2 - 
have no idea. 
do you have a working windows configuration for this device ?
you could try to get some infos with usb-sniffers but this job makes no fun...
anyway good luck.

---

### Post by TomvE on 2008-02-12
I had a look in mine and apart from the firmware_class everything is about the same.

What I didn't mention before is that I'm running Ubuntu using VirtualBox with Windows Vista as the host OS. Should that make a difference in regards to the USB devices?

---

### Post by procart on 2008-02-13
i have nothing against vista+virtualbox ;)
 - really i'm used to work with vmware solutions for xp and sure that the virtualisation is the fine technology but in your case you can waste a lot of time to get through... 
imho - you have to try "pure" linux installation with the driver.

---

### Post by TomvE on 2008-02-13
Yes, I suppose you're right. To install Ubuntu as a dual boot with Vista will be my next step.
Thanks for your help anyway!

---

### Post by Lion06 on 2008-02-25
there is a little problem with Ubuntu 8.04 alpha-5

```

................
  LD [M]  /home/lion/dvb/v4l-dvb/v4l/dvb-usb-af9005-remote.o
  CC [M]  /home/lion/dvb/v4l-dvb/v4l/pluto2.o
  CC [M]  /home/lion/dvb/v4l-dvb/v4l/pctv200e.o
/home/lion/dvb/v4l-dvb/v4l/pctv200e.c:348: warning: 'struct dvb_int_frontend_parameters' declared inside parameter list
/home/lion/dvb/v4l-dvb/v4l/pctv200e.c:348: warning: its scope is only this definition or declaration, which is probably not what you want
/home/lion/dvb/v4l-dvb/v4l/pctv200e.c:348: warning: 'struct v4l_dvb_tuner_ops' declared inside parameter list
/home/lion/dvb/v4l-dvb/v4l/pctv200e.c: In function 'pctv200e_mt2060_tuner_set_params':
/home/lion/dvb/v4l-dvb/v4l/pctv200e.c:352: error: dereferencing pointer to incomplete type
/home/lion/dvb/v4l-dvb/v4l/pctv200e.c: In function 'pctv200e_frontend_attach':
/home/lion/dvb/v4l-dvb/v4l/pctv200e.c:372: error: 'dvb_usb_tuner_calc_regs' undeclared (first use in this function)
/home/lion/dvb/v4l-dvb/v4l/pctv200e.c:372: error: (Each undeclared identifier is reported only once
/home/lion/dvb/v4l-dvb/v4l/pctv200e.c:372: error: for each function it appears in.)
/home/lion/dvb/v4l-dvb/v4l/pctv200e.c: In function 'pctv200e_tuner_attach':
/home/lion/dvb/v4l-dvb/v4l/pctv200e.c:395: error: 'struct dvb_tuner_ops' has no member named 'fe'
/home/lion/dvb/v4l-dvb/v4l/pctv200e.c:398: warning: passing argument 1 of '__a' from incompatible pointer type
/home/lion/dvb/v4l-dvb/v4l/pctv200e.c:400: error: 'struct dvb_tuner_ops' has no member named 'fe'
/home/lion/dvb/v4l-dvb/v4l/pctv200e.c:402: error: 'struct dvb_usb_adapter' has no member named 'pll_addr'
/home/lion/dvb/v4l-dvb/v4l/pctv200e.c:403: error: 'struct dvb_usb_adapter' has no member named 'pll_desc'
/home/lion/dvb/v4l-dvb/v4l/pctv200e.c:403: error: 'dvb_pll_tded4' undeclared (first use in this function)
make[3]: *** [/home/lion/dvb/v4l-dvb/v4l/pctv200e.o] Error 1
make[2]: *** [_module_/home/lion/dvb/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-8-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/lion/dvb/v4l-dvb/v4l'
make: *** [all] Error 2
lion@lion-desktop:~/dvb/v4l-dvb$ 

```

i'm afraid that it is a problem of the file .c...isn't it?

---

### Post by procart on 2008-02-26
/home/lion/dvb/v4l-dvb/v4l/pctv200e.c:348: warning: 'struct dvb_int_frontend_parameters' declared inside parameter list


You've got a wrong version of dvb_frontend.h somewhere... can it  be ?

Do you use :

[http://rapidshare.com/files/84549842/v4l-dvb-pinnacle200e-28fd6b96660d.tar.gz.tar.html](http://rapidshare.com/files/84549842/v4l-dvb-pinnacle200e-28fd6b96660d.tar.gz.tar.html)

posted by Kubunteando ?

---

### Post by Lion06 on 2008-02-26
with "original" pack of Kubunteando into Ubuntu 8.04 the driver can't compile (if you want a will post the error)

so i have tryed with the new file from svn :lolflag:

---

### Post by Lion06 on 2008-02-26
with ubuntu 7.10 and original step all ok
with ubuntu 8.04-alpha5 and originale step:

```

lion@lion-desktop:~/Scrivania/v4l-dvb-pinnacle200e-28fd6b96660d$ make
make -C /home/lion/Scrivania/v4l-dvb-pinnacle200e-28fd6b96660d/v4l 
make[1]: Entering directory `/home/lion/Scrivania/v4l-dvb-pinnacle200e-28fd6b96660d/v4l'
perl scripts/make_config_compat.pl /lib/modules/2.6.24-8-generic/build ./.myconfig ./config-compat.h
creating symbolic links...
make -C /lib/modules/2.6.24-8-generic/build SUBDIRS=/home/lion/Scrivania/v4l-dvb-pinnacle200e-28fd6b96660d/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-8-generic'
  CC [M]  /home/lion/Scrivania/v4l-dvb-pinnacle200e-28fd6b96660d/v4l/flexcop-pci.o
In file included from /home/lion/Scrivania/v4l-dvb-pinnacle200e-28fd6b96660d/v4l/flexcop-common.h:23,
                 from /home/lion/Scrivania/v4l-dvb-pinnacle200e-28fd6b96660d/v4l/flexcop-pci.c:10:
/home/lion/Scrivania/v4l-dvb-pinnacle200e-28fd6b96660d/v4l/dvb_frontend.h:42:33: error: media/v4l_dvb_tuner.h: No such file or directory
In file included from /home/lion/Scrivania/v4l-dvb-pinnacle200e-28fd6b96660d/v4l/flexcop-common.h:23,
                 from /home/lion/Scrivania/v4l-dvb-pinnacle200e-28fd6b96660d/v4l/flexcop-pci.c:10:
/home/lion/Scrivania/v4l-dvb-pinnacle200e-28fd6b96660d/v4l/dvb_frontend.h:165: error: field 'tuner_ops' has incomplete type
make[3]: *** [/home/lion/Scrivania/v4l-dvb-pinnacle200e-28fd6b96660d/v4l/flexcop-pci.o] Error 1
make[2]: *** [_module_/home/lion/Scrivania/v4l-dvb-pinnacle200e-28fd6b96660d/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-8-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/lion/Scrivania/v4l-dvb-pinnacle200e-28fd6b96660d/v4l'
make: *** [all] Error 2
lion@lion-desktop:~/Scrivania/v4l-dvb-pinnacle200e-28fd6b96660d$ 

```

---

### Post by TomvE on 2008-02-26
I finally got round to installing Xubuntu and I can report that I got the PCTV 60e fully working!

The thing that I missed from the previous steps of editing the PCTV200e.c file was that I needed to add an extra array entry in the .devices property inside the struct pctv200e_properties:

[INDENT].num_device_descs = 2,
	.devices = {
		{   "Pinnacle PCTV 200e DVB-T",
			{ &pctv200e_table[0], NULL },
			{ NULL },
		},
		{   "Pinnacle PCTV 60e DVB-T",
			{ &pctv200e_table[1], NULL },
			{ NULL },
		},
		{ NULL },
	}[/INDENT]

After that change (and a full make & install of course) the device is recognized instantly and I have been happily watching TV (Freeview UK) using Me-TV.

One thing that I didn't manage to do yet is to get the remote working. Procart, which modules did you select when you installed lirc? mceusb, mceusb2 or something else?

---

### Post by procart on 2008-02-29
> **TomvE said:**
> I finally got round to installing Xubuntu and I can report that I got the PCTV 60e fully working!

.....................
.....................

One thing that I didn't manage to do yet is to get the remote working. Procart, which modules did you select when you installed lirc? mceusb, mceusb2 or something else?

Congratulations! 

i tried different modules but (!) it work better with default settings ;) let say-   i have in etc/sysconfig/lirc just: 

LIRCD_DRIVER=""
#
LIRCD_DEVICE=""
#
LIRC_MODULE=""

do you use my version of pctv200.c (i included in tar lircd.conf too) ? there are some important changes in remote-control part...
can you get some rc-input in irrecord (from lirc package)?

it works good with kaffeine (kde3.5.7+IRKick).
have problems only with few buttons like "mute", "a,b,c,?" and can't start kaffeine    directly in DVB-player-mode but hope to get  a right solution soon...
i can post my event-mapping-file (./kde/share/config/kickerrc) for IRKick+kaffeine.

nice weekend.

---

### Post by procart on 2008-02-29
> **Lion06 said:**
> with ubuntu 7.10 and original step all ok
with ubuntu 8.04-alpha5 and originale step:
................................................


i think that the problem is the 2.6.24-kernel...
there are global changes in usb-driver architecture and solutions for 2.6.22 and older versions will not work anymore :(

---

### Post by atlas95 on 2008-03-08
Same problem :( 
I can't compil the module :(

---

### Post by Lion06 on 2008-03-08
> **procart said:**
> i think that the problem is the 2.6.24-kernel...
there are global changes in usb-driver architecture and solutions for 2.6.22 and older versions will not work anymore :(


we can only wait the magic Kubunteando  :guitar:

---

### Post by TomvE on 2008-03-08
Procart, could you just confirm with me which of these two pictured remotes you have:

[IMG]http://www.linuxtv.org/v4lwiki/images/4/4d/Pinnacle_50or110_i_remote.jpg[/IMG]

---

### Post by FeeWiewwy on 2008-03-19
Hi!

First of all, many thanks to those people who spend their time in developing this driver!
:-D

I like this card, but I'm tired to use the inefficient Pinnacle mediacenter. Instead I prefer free software and linux.

Following this thread, I have tried to get my 200e working on my kubuntu 7.10 box. I downloaded 
v4l-dvb-pinnacle200e-28fd6b96660d.tar.gz tree as well as the pctv200e.tar.gz and replaced the corresponding files. Compiling, installing the module and searching channels in kaffeine and mythtv worked.

But I am only able to hear the audio in kaffeine, video only consists of a picture of pink artifacts. Nevertheless the aspect ratio seems to be set up correctly.
In mythtv I cannot get a lock when changing channels.

Is there someone who can help me to get my card work?

Thanks!

--Markus

---

### Post by FeeWiewwy on 2008-03-23
Wow, I solved the problem myself. Had to fix my some video drivers and cleanup of the kernel modules.

Now, I'd like to get the rest of the buttons of my remote control working like channel+/-. At this point, only play/stop, volume setting up/down/r/l/ok and the digits work.. Any idea were to get a better lircd.conf?

bye
--Markus

---

### Post by gfabio86 on 2008-03-25
thanks now i have a PCTV 60e fully functional in linux mint...
:popcorn:

---

### Post by TomvE on 2008-03-25
gfabio86, did you manage to get the remote control working as well?

---

### Post by arroba3 on 2008-04-27
What a surprise when I upgraded to Ubuntu 8.04 and I see I can't compile the v4l version that Kubunteando made. The thing is that I have been able to change the newest v4l version so it started to create the pctv200e.o archive, but I had this error:

[[img]http://s248.photobucket.com/albums/gg197/arroba3/Otras/th_v4l-error.jpg[/img]](http://s248.photobucket.com/albums/gg197/arroba3/Otras/v4l-error.jpg)

I think that the problem is now with the pctv200e drivers... I don't know what else to do...

---

### Post by Kubunteando on 2008-04-28
Now Hardy is officially out.
I haven't tried myself, but I gather that the driver does not compile any more from your comments.

I will join you and try to see if we make it to compile again. This was the first driver I wrote, so I am not an expert. But I will give it a try around 1st of May and/or next weekend.

If you have any ideas on what is wrong, let me know. Also if you have any results from your own research on getting the appropriate v4l sources for Hardy's kernel. That would help.

Great to hear the 60e is working now.

---

### Post by arroba3 on 2008-04-28
Here, I have been able to compile and install it but my PCTV 200e wouldn't work.

[http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

I hope there's any solution soon. Thanks!

Arroba3

---

### Post by Kubunteando on 2008-05-01
I just was today having a look at this, and here you have something to try what seems to work.
Same procedure to compile it as before.

[http://rapidshare.com/files/111810479/v4l-dvb-hardy-2daeefda69fe.zip.html](http://rapidshare.com/files/111810479/v4l-dvb-hardy-2daeefda69fe.zip.html)

There were some changes to made since Video4Linux made some modifications. Once more I am no expert, so I went through the examples, and after quite a few tries it seems to work fine.

I have included the changes TomvE made for the Pinnacle 60e. So have a try.

I have noticed 1 problem though: if you disconnect the tuner from the USB, it is unregistered fine, but if you plug it back it will not register again correctly. You have to run this before plugging it back: "sudo rmmod pctv200e". I don't know why this happens now...

I will try to get this into the main tree of Vide4Linux, and update the wiki in [www.linuxtv.org](www.linuxtv.org). I did send a couple of emails last year with no much result but I will try again.

Let me know if the Pinnacle 60e works fine, so I can tell we have 2 devices working with this driver!

---

### Post by arroba3 on 2008-05-01
O yeah! It works perfectly Kubuntero! The problem of unplugging the usb also happened to me with the other driver in Ubuntu 7.10, but is not a big deal for me.

Thank you very much!

Bye!

---

### Post by lukemack on 2008-05-02
Hi,

Can someone please upload this to somewhere other than rapidshare? I am not able to download from there.

Thanks,

lukemack.

---

### Post by arroba3 on 2008-05-02
Here, you have, I uploaded it to **Megaupload**:

[http://www.megaupload.com/?d=MV1FGE5Y](http://www.megaupload.com/?d=MV1FGE5Y)

I hope it works now.

Bye!

---

### Post by TomvE on 2008-05-02
Kubunteando, I'll have a play with it this weekend and will let you know if it all works with the 60e.

Yes, it would be great if we can get this driver into the main tree, so hopefully someone is going to reply to your emails this time.

---

### Post by TomvE on 2008-05-03
Tested it on a fresh Hardy installation, and all works fine for the 60e. Great job!

---

### Post by TomvE on 2008-05-04
Kubunteando, have you been playing around with the remote control settings? I see you made some changes (cleanup I suppose) to procart's initial code, and that you commented out some lines in pctv200e_properties.
Does your remote work?

(I have found out that the 200e remote is a different one from the 60e, so I will need to make modifications to add support for the 60e remote)

---

### Post by Kubunteando on 2008-05-04
Not really done anything with the remote, mine seems to be broken...

I just tried to enable the code for the remote (still commented out) and I got some strange behavior, so I commented it back. But I did not spend much time on it, I commented it back, so those issues could be due to other reasons.

Give it a try, I think most code is copied from digitv.c, which I followed as an example. If it works for the 60e, I think we can still make the driver recognize both remote controls somehow.

---

### Post by TomvE on 2008-05-06
Ahhh, this remote is doing my head in!
I can see the button presses in the syslog, but LIRC for some reason does not recognize the remote, whatever setting I throw at it.

Someone with a 200e or 60e around here who wants to share their settings (hardware.conf) with us?

---

### Post by funo on 2008-05-07
Hello, I'm a beginner linux-user and I can compile and install the original v4l but it does not work with my pinnacle pctv 260e.

I'm trying to compile the driver from kubunteando but i get this error:

file not found /lib/modules/2.6.24-16-generic/build/include/linux/netdevice.h

I'm an OpenSUSE user, maybe I just need to switch to ubuntu? :D

Hope someone has solved same error
Thank you for your support

---

### Post by Kubunteando on 2008-05-07
I don't know much about OpenSUSE, I just tried it once, but I found this:

it seems
          that now you must copy the file /usr/src/linux/include/linux/netdevice.h 
          to  /lib/modules/2.6.24-16-generic/build/include/linux/netdevice.h 
          to get the make to complete successfully.

This is from some other page I found in the Internet,so give it a try.

I don't think you need to try to switch to Ubuntu if the above works, only if you like it more. If you could mention about the driver in the OpenSUSE forums it would be great. Maybe it will be of help to somebody else.

---

### Post by funo on 2008-05-07
It was just a matter of build cache, I sent this command:

make distclean

and then make worked.

Now it's still compiling, I'll let you know if I arrive to the end of the story :)

---

### Post by funo on 2008-05-07
nothing to do... successly compiled & installed, rebooted but it seems like make has compiled everything but the pctv driver (cannot find .ko files)


very strange

I'll continue trying and report

thanks

---

### Post by Kubunteando on 2008-05-07
If the pctv200e.ko was created successfully during the compilation, it should be in the compilation main folder and from there in:

v4l/pctv200e.ko

So you can check whether it was created or not, so if it was created then what fails is the installation ("make install"). Maybe there are different folders for the drivers in SUSE?

In Ubuntu Hardy it is installed in:
/lib/modules/2.6.24-16-generic/kernel/drivers/media/dvb/pctv200e/pctv200e.ko

---

### Post by lukemack on 2008-05-07
Hi,

I have installed the version posted above for the 60e. How do I tune the card in VLC to actually see something? I need steps from file -> open capture device.

All I have done so far is make and make install.

thanks!

lukemack.

---

### Post by lukemack on 2008-05-07
cancel that. I followed the post here [http://davidwinter.me.uk/articles/2008/02/08/watching-freeview-dvb-t-tv-with-vlc-player-on-ubuntu/](http://davidwinter.me.uk/articles/2008/02/08/watching-freeview-dvb-t-tv-with-vlc-player-on-ubuntu/)

However, I am getting choppy Audio. Anyone know of a fix / tweak for that?

---

### Post by TomvE on 2008-05-07
Have you tried other TV viewing apps to see if the sound is choppy there as well? It might just be a VLC-specific problem, but you need to narrow it down first.

[Me-TV]("https://launchpad.net/me-tv") is a nice app and very easy to setup for a quick test.

---

### Post by lukemack on 2008-05-08
Hi.

Thanks for the reply. The solution was to change the audio output module in VLC to ALSA mixer. So I now have a PCTV60e working under Ubuntu 8.04 desktop. 

Thanks!

lukemack.

---

### Post by mercy on 2008-05-08
Hello
just wanted to let you know that your driver works on a [Buffalo]("http://www.buffalotech.com/products/network-storage/linkstation/linkstation-live/") [Linkstation Live]("http://buffalo.nas-central.org/index.php/Category:LSLive")  with a 2.6.25.1 kernel.
Great work. Hope it get's back into the v4l-dvb souce.

Regards,
mercy

---

### Post by TomvE on 2008-05-09
Wow, we made a NAS able to work as a TV card! How good are we? ;)

(I suppose you have a Pinnacle card connected to the NAS which is running Ubuntu).

---

### Post by mercy on 2008-05-09
> Wow, we made a NAS able to work as a TV card! How good are we? ;)

Hehe... would be great if you could do that :lolflag:

> 
(I suppose you have a Pinnacle card connected to the NAS which is running Ubuntu).

Right, but it's not ubuntu it's debian testing.

Cheers
Mercy

---

### Post by funo on 2008-05-13
My problem it's that after make I can find all the drivers compiled but pctv driver,

it does not get compiled, I just find pctv200e.h and pctv200e.c

very strange

---

### Post by funo on 2008-05-13
> **Kubunteando said:**
> If the pctv200e.ko was created successfully during the compilation, it should be in the compilation main folder and from there in:

v4l/pctv200e.ko

So you can check whether it was created or not, so if it was created then what fails is the installation ("make install"). Maybe there are different folders for the drivers in SUSE?

In Ubuntu Hardy it is installed in:
/lib/modules/2.6.24-16-generic/kernel/drivers/media/dvb/pctv200e/pctv200e.ko


could it be a problem caused by kernel configuration?
it does not create pctv200e files...

---

### Post by TomvE on 2008-05-14
> **funo said:**
> could it be a problem caused by kernel configuration?
it does not create pctv200e files...

Are you using Kubunteando's files? Or did you get the latest V4L source and tried to add pctv200e to it? Because the latter won't work as the pctv200e files are not in the MAKEFILE config.

So make sure you got Kubunteando's files (he mentioned the link on one of the previous pages) and compile from there.

---

### Post by funo on 2008-05-14
> **TomvE said:**
> Are you using Kubunteando's files? Or did you get the latest V4L source and tried to add pctv200e to it? Because the latter won't work as the pctv200e files are not in the MAKEFILE config.

So make sure you got Kubunteando's files (he mentioned the link on one of the previous pages) and compile from there.

Yes, I'm using Kubunteando's files and I've checked inside the makefile, I can see pctv220e specified. I'll try installing hardy and compile from there. Maybe we can try adding manually compiled files?

---

### Post by dcihlar on 2008-06-26
I am using Kubunteando's archive, yet I don't get the PCTV 260e's module compiled. I tried looking in the v4l/.config file, and there's no mention of 260e there. Same when I did make config. Can someone post EXACT instructions on how to enable PCTV?

I do have DVB_CORE, I2C and PCI enabled in the kernel. I2C is a module, and DVB_CORE is being enabled along with v4l.

Thank you!

---

### Post by TomvE on 2008-06-30
Good news for the folks using a PCTV 60e: I managed to get the remote control fully working!

Go here for the modified pctv200e.c file (based on Kubunteando's last effort): [http://www.mediafire.com/?gzmixs1m1no](http://www.mediafire.com/?gzmixs1m1no)
And here you can find the .conf file for LIRC (just setup LIRC to use the Linux Input Layer and point it to the right input event): [http://www.mediafire.com/?m1mtuxkhkld](http://www.mediafire.com/?m1mtuxkhkld)

It would be great if people with a 200e (or others like the 260e) could give this a go as well. Maybe we need to modify the key codes for different remote controls, but I'm willing to make those changes.
And once that is done we should really try to get these into the main v4l tree.

---

### Post by Holliefant on 2008-07-04
Can you by any chance put that together in one file, so youre patched pctv in the v4l branch so that we have one package to compile :)

And since the change to 2.6.24-19-generic i have several problems with compiling,
main problem is that the includes like media/frontend_dv.h cant be found.
But maybe I am just stupid again :) Wouldn't be suprising to me.

---

### Post by TomvE on 2008-07-04
Sure, here you go: [http://www.mediafire.com/?nvfpjz9yxtz](http://www.mediafire.com/?nvfpjz9yxtz)

Let me know if you have any trouble compiling it.

---

### Post by Holliefant on 2008-07-05
Thx a lot :)
Works like a charm :)

But now I am stuck, once again :)

I have the Lirc config file, and dmesg shows that a lirc device:

[ 9400.956704] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb5/5-1/input/input15

and in /proc/bus/input/devices is this one:

I: Bus=0003 Vendor=2304 Product=0216 Version=0000
N: Name="IR-receiver inside an USB DVB receiver"
P: Phys=usb-0000:00:1d.7-1/ir0
S: Sysfs=/devices/pci0000:00/0000:00:1d.7/usb5/5-1/input/input15
U: Uniq=
H: Handlers=kbd event10
B: EV=3
B: KEY=c0110 2002000 0 0 0 0 18000 1a8 801 9e1680 0 15042 12800ffc

Ok that sound good, but how to get it working :):)
I am very sry, this is my first Lirc device and I only find help for serial devices and i dont know how to connect to this device. There is no /dev/ device I am aware of :)

---

### Post by TomvE on 2008-07-05
Ok, first you edit /etc/lirc/hardware.conf.
Make sure the bit about the remote control contains these lines:

```
REMOTE="Linux input layer (/dev/input/eventX)"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event10"
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""
```

Then you copy the contents of the pctv60e.conf to /etc/lirc/lircd.conf

And finally you start LIRC: sudo lircd

When you know open a terminal window and start pressing the number buttons you should see those appear on the command line. If not, have a look in the system logs (dmesg) and see if there are any pctv200e key messages there.

---

### Post by Holliefant on 2008-07-05
Thx a lot :)

Working and I am happy now :)

---

### Post by TomvE on 2008-07-06
Just to check: are you using the 60e or the 200e?

---

### Post by Holliefant on 2008-07-06
60e :)
Sry that i didn't mention :)

Is there any posibility that this driver gets into the v4l tree?

---

### Post by enjung on 2008-07-06
First of all I want to thank everybody for working on the driver. Finally I I got it working, too. It was really hard for me, because I'm a newbie in the field of self-compiled modules.

At first I tried to compile the files on Ubuntu 2.6.24-19-386 and got an error message beacause of missing files. I think the tree was made on 2.6.24-16-generic. With "make distclean" this problem was solved, but the pctv200e.ko file was not generated. So I "downgraded" to version 2.6.24-16-generic and compiled everything succesfully and it works fine with my 60e now.

Did anybody get the driver working with 2.6.24-19? I hope this question is not too silly for you guys...

---

### Post by Holliefant on 2008-07-06
I had same problem, or i think so :)
So here is what I did:

The make process did search for a build directory in the directory
/lib/modules/2.6.24-16-generic but there is none, because i use the 19 Kernel.
so since i wont use the 16 Kernle again, i removed that directory and made a symbolic
link to the 19 dir:

/lib/modules# sudo ln -s 2.6.24-19-generic 2.6.24-16-generic

I dont know if that is really really stupid, but it doesnt matter much to me :)
Im just to happy that it works now :)

---

### Post by enjung on 2008-07-07
Thx for your reply :). This is a really stupid but great way to solve the problem. I'll maybe try out this evening. At the moment I'm absolutely happy even with the 2.6.24-16-generic kernel. I tried watching and recording with Me-Tv and it works great :-D.

---

### Post by TomvE on 2008-07-07
Great guys! Good to hear that more people managed to get it to work.

Now, if some 200e owners could test it as well, so we can verify that their remote control works, then that would be a big step towards getting this into the main tree.

---

### Post by enjung on 2008-07-08
Good news for you guys. I managed compiling with the symbolic link mentioned above. My 60e works fine now with kernel 2.6.24-19-generic. :) Next I tried to get the remote working, too. I can control shells with it (up, down, enter etc. work fine), but I can't control Me-Tv or VLC with it. Are there any options to choose inside Me-Tv to get the remote working?!? Hopefully it's just my fault... :) Apart from that I think it would be great to include the driver into the v4l tree...

EDIT: I think I can control some Ubuntu specific functions, like mute, volume +/-, fullscreen etc. and even shutdown with the "off" button. This is nice, but switching the channels with the remote would even be nicer... :)

---

### Post by TomvE on 2008-07-08
Me-TV does not have support for LIRC, but you can control it using [irxevent]("http://www.lirc.org/html/irxevent.html").

Edit /home/<username>/.lircrc and add the following lines:
```
begin
        prog = irxevent
        button = epg    
        config = Key e Me
end
begin
        prog = irxevent
        button = fullscreen    
        config = Key f Me
end
begin
        prog = irxevent
        button = off    
        config = Key ctrl-q Me
end
```
You can of course add more keys, like channel up and down (ch+ -> Key Up, ch- -> Key Down).
The 'Me' in this case is the begin of the window name ('Me TV').

Once saved, start irxevent: irxevent -d /home/<username>/.lircrc
And now your button presses will be handled as key presses in Me TV.

---

