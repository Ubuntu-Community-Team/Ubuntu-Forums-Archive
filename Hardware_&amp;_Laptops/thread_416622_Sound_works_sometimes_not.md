---
title: "Sound works sometimes not"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by Senti on 2007-04-21
Hello
i have a notebook with a ess pci sound card and ubuntu dapper installed on it.
After booting it happen sometimes that i cannot hear any sound, most times it disappear after reboot. Whats wrong?
Thanks

---

### Post by sudo_nym on 2007-04-28
> **Senti said:**
> Hello
i have a notebook with a ess pci sound card and ubuntu dapper installed on it.
After booting it happen sometimes that i cannot hear any sound, most times it disappear after reboot. Whats wrong?
Thanks

I wasn't getting any sound at all, until I added *snd-es1688* to my /etc/modules file.  But I have a different sound card, so 1688 might not work for you.

Here's what my modules file looks like;```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
snd-es1688
#libusual
```

I found these modules;
snd-es1938.ko
snd-es1968.ko
in /lib/modules/2.6.17-10-generic/kernel/sound/pci/ , so one of those might work for you.  They seems most likely, because they were in the ./pci/ directory and have `es' in the name.  Have a look in your modules directory [especially the ./sound/pci/ subdirectory, but change the numbers in that path to your kernel version first].

At the terminal, you can type; *sudo nano /etc/modules* and then add the module name, without the `.ko' at the end, and save your changes.  You can use any text editor, not just nano, but I don't know what you have installed.  Change the command to *sudo gedit /etc/modules* if you want -- mousepad, leafpad, gtkedit, whatever.  Then reboot and see if it worked.

I don't know which will work.  You might have to try a few before you get it right, but only one at a time.



Good luck,

Patrick.

---

### Post by sudo_nym on 2007-04-28
What kind of notebook, by the way?

---

### Post by Senti on 2007-04-28
its a medion md9580-f [http://0pointer.de/lennart/aldi/](http://0pointer.de/lennart/aldi/)

okay i will try it
old modules
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
lp
psmouse

```


new modules
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
lp
psmouse
lp
snd-maestro3.ko

```

But the problem that i have is that it works sometimes that points more to a hardwareproblem or a bug as far i know. It works all 4 starts not (!), and why should the modules three times be loadet if a file is wrong... But i thing i will see if it works after the next 20 starts ;)

thanks for the help
Senti

---

### Post by sudo_nym on 2007-04-29
> **Senti said:**
> [...]

new modules
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
lp
psmouse
lp
snd-maestro3.ko

```

But the problem that i have is that it works sometimes that points more to a hardwareproblem or a bug as far i know. It works all 4 starts not (!), and why should the modules three times be loadet if a file is wrong... But i thing i will see if it works after the next 20 starts ;)

That might be your problem right there; kernel modules only need to be loaded once.  So why are they written twice?  Three times?  Maybe during an upgrade those entries were added automatically, without first checking if they were already there.  Well, maybe.  I don't know.

But about double-loaded modules; I tried adding `libusual' [a USB controller] to my modules file, but had problems soon after.  When resuming from hibernation, the `libusual' module would load *before* reading and restoring the previously suspended session.  I think the module assigned mount-points and addresses to USB peripherals, so that when the system resumed, paths and addresses it had previously set up didn't work anymore [probably the same addresses, mount points or whatever, but they could only be assigned once].

To put it simply; after hibernation the USB stick wouldn't mount, and the mouse wouldn't squeak.  :-\  I think it was because the system was trying to set variables that had already been set, eg; double-loading.

By the way, was sound failing after reboot, but not after fully shutting down?  That was my original problem with USB devices.  It *looked* random, until I noticed the difference between rebooting, and shutting down completely.

A lot of peripherals run off their USB connections, without any other power source, and rebooting may fail to reset them because power is not interrupted [or not interrupted long enough].  That's why shutting down completely before booting-up again fixed it.  I don't know if sound cards ever have that problem.
> thanks for the help
Senti
I don't know if this will help.  Hope it does though.  I'm just guessing really, and since no one had answered you for a week...



Good luck,

Patrick.

---

### Post by Senti on 2007-04-29
i corrected the double entry now. But i had the problem alredy before the update. How can i check if the soundcard is found? It looks like that the soundcard is not found when i start the pc the first time and when its cold. Maybe the soundcard works only when its warm enough ^^
However the new entry in the modules did not help i have now at this moment no sound...

---

### Post by sudo_nym on 2007-04-29
> **Senti said:**
> i corrected the double entry now. But i had the problem alredy before the update. How can i check if the soundcard is found? It looks like that the soundcard is not found when i start the pc the first time and when its cold. Maybe the soundcard works only when its warm enough ^^
However the new entry in the modules did not help i have now at this moment no sound...

Typing *dmesg* in the terminal might give you some useful answers.  It logs almost everything that happens from power-on to shutdown, but doesn't seem to hold this information from one boot to the next.

Might be especially useful to check dmesg when sound loads *properly*, then see if you can make the same thing happen every time.  I guess you'd want to look out for entries about ALSA, ESS, which modules loaded at boot time, in what order, errors and so on.

I still don't know if this will help any, but hope it does.



Good luck,

Patrick.

---

### Post by Senti on 2007-04-30
i will try it, but that can take one two days till the sound do not work again

---

### Post by Senti on 2007-05-01
Deleted

---

### Post by Senti on 2007-05-02
the sound driver is maestro3.o
its a pci soundcard in the notebook the chip is a ES1988-Chip from ESS-technology

I do not find the problem myself :(

dmesg when sound is working :

```

[17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Fri Sep 8 19:55:17 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e9400 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000000fff0000 - 000000000ffffc00 (ACPI data)
[17179569.184000]  BIOS-e820: 000000000ffffc00 - 0000000010000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 255MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 65520
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 61424 pages, LIFO batch:15
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 FIC                                   ) @ 0x000f6bc0
[17179569.184000] ACPI: RSDT (v001 FIC    ND000030 0x00000001 FIC  0x00000000) @ 0x0fffb152
[17179569.184000] ACPI: FADT (v001 FIC    ND000030 0x00000001 FACP 0x000f4240) @ 0x0ffffb64
[17179569.184000] ACPI: BOOT (v001 FIC    ND000030 0x00000001 FIC  0x00000001) @ 0x0ffffbd8
[17179569.184000] ACPI: DSDT (v001    FIC ND000030 0x00000001 MSFT 0x0100000b) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 10000000:eff80000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda4
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01201000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[17179569.184000] Detected 699.647 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.700000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.700000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179569.728000] Memory: 249140k/262080k available (1976k kernel code, 12356k reserved, 606k data, 288k init, 0k highmem)
[17179569.728000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.808000] Calibrating delay using timer specific routine.. 1400.32 BogoMIPS (lpj=2800659)
[17179569.808000] Security Framework v1.0.0 initialized
[17179569.808000] SELinux:  Disabled at boot.
[17179569.808000] Mount-cache hash table entries: 512
[17179569.808000] CPU: After generic identify, caps: 0387f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179569.808000] CPU: After vendor identify, caps: 0387f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179569.808000] CPU: L1 I cache: 16K, L1 D cache: 16K
[17179569.808000] CPU: L2 cache: 256K
[17179569.808000] CPU serial number disabled.
[17179569.808000] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[17179569.808000] mtrr: v2.0 (20020519)
[17179569.808000] CPU: Intel Pentium III (Coppermine) stepping 0a
[17179569.808000] Enabling fast FPU save and restore... done.
[17179569.808000] Enabling unmasked SIMD FPU exception support... done.
[17179569.808000] Checking 'hlt' instruction... OK.
[17179569.824000] checking if image is initramfs... it is
[17179571.972000] Freeing initrd memory: 6616k freed
[17179572.012000] ACPI: Looking for DSDT ... not found!
[17179572.016000] ACPI: setting ELCR to 0200 (from 0020)
[17179572.024000] NET: Registered protocol family 16
[17179572.024000] EISA bus registered
[17179572.024000] ACPI: bus type pci registered
[17179572.028000] PCI: PCI BIOS revision 2.10 entry at 0xfd9ae, last bus=1
[17179572.028000] PCI: Using configuration type 1
[17179572.028000] ACPI: Subsystem revision 20051216
[17179572.036000] ACPI: Interpreter enabled
[17179572.036000] ACPI: Using PIC for interrupt routing
[17179572.040000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179572.040000] PCI: Probing PCI hardware (bus 00)
[17179572.044000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179572.048000] PCI quirk: region 1000-103f claimed by PIIX4 ACPI
[17179572.048000] PCI quirk: region 1040-104f claimed by PIIX4 SMB
[17179572.048000] PIIX4 devres C PIO at 0068-006f
[17179572.048000] Boot video device is 0000:01:00.0
[17179572.052000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179572.056000] ACPI: PCI Interrupt Link [LNKA] (IRQs 10) *0, disabled.
[17179572.056000] ACPI: PCI Interrupt Link [LNKB] (IRQs 10) *0, disabled.
[17179572.056000] ACPI: PCI Interrupt Link [LNKC] (IRQs *5)
[17179572.060000] ACPI: PCI Interrupt Link [LNKD] (IRQs 5) *0, disabled.
[17179572.064000] ACPI: Power Resource [PUSB] (off)
[17179572.064000] ACPI: Power Resource [PFAN] (on)
[17179572.064000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179572.064000] pnp: PnP ACPI init
[17179572.076000] pnp: PnP ACPI: found 12 devices
[17179572.076000] PnPBIOS: Disabled by ACPI PNP
[17179572.076000] PCI: Using ACPI for IRQ routing
[17179572.076000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179572.076000] pnp: 00:04: ioport range 0x1000-0x104f could not be reserved
[17179572.076000] pnp: 00:04: ioport range 0xfe00-0xfe01 has been reserved
[17179572.080000] PCI: Bridge: 0000:00:01.0
[17179572.080000]   IO window: 2000-2fff
[17179572.080000]   MEM window: fc100000-fdffffff
[17179572.080000]   PREFETCH window: 28000000-280fffff
[17179572.080000] PCI: Bus 2, cardbus bridge: 0000:00:0c.0
[17179572.080000]   IO window: 00003000-000030ff
[17179572.080000]   IO window: 00003400-000034ff
[17179572.080000]   PREFETCH window: 20000000-21ffffff
[17179572.080000]   MEM window: 22000000-23ffffff
[17179572.080000] PCI: Bus 6, cardbus bridge: 0000:00:0c.1
[17179572.080000]   IO window: 00003800-000038ff
[17179572.080000]   IO window: 00003c00-00003cff
[17179572.080000]   PREFETCH window: 24000000-25ffffff
[17179572.080000]   MEM window: 26000000-27ffffff
[17179572.080000] **** SET: Misaligned resource pointer: ce9f75e2 Type 07 Len 0
[17179572.080000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[17179572.080000] PCI: setting IRQ 10 as level-triggered
[17179572.080000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[17179572.080000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[17179572.080000] ACPI: PCI Interrupt 0000:00:0c.1[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[17179572.080000] PCI: Setting latency timer of device 0000:00:0c.1 to 64
[17179572.080000] Simple Boot Flag at 0x38 set to 0x1
[17179572.080000] audit: initializing netlink socket (disabled)
[17179572.080000] audit(1177934373.080:1): initialized
[17179572.080000] VFS: Disk quotas dquot_6.5.1
[17179572.080000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.080000] Initializing Cryptographic API
[17179572.080000] io scheduler noop registered
[17179572.080000] io scheduler anticipatory registered
[17179572.080000] io scheduler deadline registered
[17179572.084000] io scheduler cfq registered
[17179572.084000] Limiting direct PCI/PCI transfers.
[17179572.084000] isapnp: Scanning for PnP cards...
[17179572.436000] isapnp: No Plug & Play device found
[17179572.480000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUS] at 0x60,0x64 irq 1,12
[17179572.480000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179572.480000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179572.480000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179572.480000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179572.480000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179572.480000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179572.480000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179572.484000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.484000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179572.488000] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.488000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179572.488000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179572.488000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179572.492000] mice: PS/2 mouse device common for all mice
[17179572.492000] EISA: Probing bus 0 at eisa.0
[17179572.492000] Cannot allocate resource for EISA slot 1
[17179572.492000] Cannot allocate resource for EISA slot 2
[17179572.492000] Cannot allocate resource for EISA slot 3
[17179572.492000] EISA: Detected 0 cards.
[17179572.492000] NET: Registered protocol family 2
[17179572.528000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179572.528000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[17179572.528000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[17179572.528000] TCP: Hash tables configured (established 16384 bind 16384)
[17179572.528000] TCP reno registered
[17179572.528000] TCP bic registered
[17179572.528000] NET: Registered protocol family 1
[17179572.528000] NET: Registered protocol family 8
[17179572.528000] NET: Registered protocol family 20
[17179572.528000] Using IPI Shortcut mode
[17179572.528000] ACPI wakeup devices: 
[17179572.528000]  LID COM1 MPC1 MPC2 
[17179572.528000] ACPI: (supports S0 S3 S4 S5)
[17179572.528000] Freeing unused kernel memory: 288k freed
[17179572.660000] Capability LSM initialized
[17179572.748000] ACPI: Fan [FAN] (on)
[17179572.756000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179572.756000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179572.764000] ACPI: Thermal Zone [THRM] (30 C)
[17179573.100000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.884000] PIIX4: IDE controller at PCI slot 0000:00:07.1
[17179573.884000] PIIX4: chipset revision 1
[17179573.884000] PIIX4: not 100% native mode: will probe irqs later
[17179573.884000]     ide0: BM-DMA at 0x1050-0x1057, BIOS settings: hda:DMA, hdb:pio
[17179573.884000]     ide1: BM-DMA at 0x1058-0x105f, BIOS settings: hdc:pio, hdd:pio
[17179573.884000] Probing IDE interface ide0...
[17179574.172000] hda: HITACHI_DK23CA-20, ATA DISK drive
[17179574.844000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.844000] Probing IDE interface ide1...
[17179575.584000] hdc: QSI DVD-ROM SDR-081, ATAPI CD/DVD-ROM drive
[17179576.256000] ide1 at 0x170-0x177,0x376 on irq 15
[17179576.272000] hda: max request size: 128KiB
[17179576.296000] hda: 39070080 sectors (20003 MB) w/2048KiB Cache, CHS=38760/16/63, UDMA(33)
[17179576.296000] hda: cache flushes not supported
[17179576.296000]  hda: hda1 hda2 hda3 hda4
[17179576.340000] hdc: ATAPI 61X DVD-ROM drive, 512kB Cache, DMA
[17179576.340000] Uniform CD-ROM driver Revision: 3.20
[17179580.516000] usbcore: registered new driver usbfs
[17179580.516000] usbcore: registered new driver hub
[17179580.524000] USB Universal Host Controller Interface driver v2.3
[17179580.524000] PCI: Enabling device 0000:00:07.2 (0000 -> 0001)
[17179580.524000] **** SET: Misaligned resource pointer: cfd4d7e2 Type 07 Len 0
[17179580.524000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
[17179580.524000] PCI: setting IRQ 5 as level-triggered
[17179580.524000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[17179580.528000] uhci_hcd 0000:00:07.2: UHCI Host Controller
[17179580.528000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[17179580.528000] uhci_hcd 0000:00:07.2: irq 5, io base 0x00001060
[17179580.528000] hub 1-0:1.0: USB hub found
[17179580.528000] hub 1-0:1.0: 2 ports detected
[17179580.780000] Attempting manual resume
[17179580.836000] EXT3-fs: mounted filesystem with ordered data mode.
[17179580.864000] kjournald starting.  Commit interval 5 seconds
[17179581.376000] usb 1-2: new full speed USB device using uhci_hcd and address 3
[17179604.684000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[17179604.684000] Yenta: CardBus bridge found at 0000:00:0c.0 [1509:1760]
[17179604.684000] Yenta: Enabling burst memory read transactions
[17179604.684000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179604.684000] Yenta: Routing CardBus interrupts to PCI
[17179604.684000] Yenta TI: socket 0000:00:0c.0, mfunc 0x010c1022, devctl 0x64
[17179604.808000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179604.920000] Yenta: ISA IRQ mask 0x0898, PCI irq 10
[17179604.920000] Socket status: 30000006
[17179604.980000] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[17179604.996000] 8139too Fast Ethernet driver 0.9.27
[17179604.996000] PCI: Enabling device 0000:00:09.0 (0000 -> 0003)
[17179604.996000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[17179604.996000] eth0: RealTek RTL8139 at 0xd08e4000, 00:30:54:00:2f:41, IRQ 10
[17179604.996000] eth0:  Identified 8139 chip type 'RTL-8139C'
[17179605.008000] ACPI: PCI Interrupt 0000:00:0c.1[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[17179605.008000] Yenta: CardBus bridge found at 0000:00:0c.1 [1509:1760]
[17179605.012000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179605.012000] Yenta: Routing CardBus interrupts to PCI
[17179605.012000] Yenta TI: socket 0000:00:0c.1, mfunc 0x010c1022, devctl 0x64
[17179605.252000] Yenta: ISA IRQ mask 0x0898, PCI irq 10
[17179605.252000] Socket status: 30000006
[17179605.272000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179605.344000] **** SET: Misaligned resource pointer: ce949522 Type 07 Len 0
[17179605.348000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
[17179605.348000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[17179605.348000] maestro3: enabled hack for 'LEGEND ZhaoYang 3100CF'
[17179605.392000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179605.536000] Linux agpgart interface v0.101 (c) Dave Jones
[17179605.544000] agpgart: Detected an Intel 440BX Chipset.
[17179605.548000] agpgart: AGP aperture is 64M @ 0xf8000000
[17179606.128000] irda_init()
[17179606.128000] NET: Registered protocol family 23
[17179606.580000] parport: PnPBIOS parport detected.
[17179606.580000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[17179606.728000] Synaptics Touchpad, model: 1, fw: 5.6, id: 0x9244b1, caps: 0x80471b/0x0
[17179606.764000] input: SynPS/2 Synaptics TouchPad as /class/input/input1
[17179606.764000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17179607.096000] input: PC Speaker as /class/input/input2
[17179607.184000] Real Time Clock Driver v1.12
[17179607.224000] Floppy drive(s): fd0 is 1.44M
[17179607.240000] FDC 0 is a post-1991 82077
[17179607.492000] eth1: register 'cdc_ether' at usb-0000:00:07.2-2, CDC Ethernet Device, 00:15:0c:3b:b6:32
[17179607.492000] usbcore: registered new driver cdc_ether
[17179607.740000] ts: Compaq touchscreen protocol output
[17179607.984000] cs: IO port probe 0x100-0x3af: excluding 0x200-0x207
[17179607.988000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179607.988000] cs: IO port probe 0x820-0x8ff: clean.
[17179607.988000] cs: IO port probe 0xc00-0xcf7: clean.
[17179607.992000] cs: IO port probe 0xa00-0xaff: clean.
[17179607.992000] cs: IO port probe 0x100-0x3af: excluding 0x200-0x207
[17179607.996000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179607.996000] cs: IO port probe 0x820-0x8ff: clean.
[17179607.996000] cs: IO port probe 0xc00-0xcf7: clean.
[17179608.000000] cs: IO port probe 0xa00-0xaff: clean.
[17179608.964000] lp0: using parport0 (interrupt-driven).
[17179609.200000] Adding 1007992k swap on /dev/disk/by-uuid/da8270ba-b9bd-4ce5-bdbc-c1dfde05e69e.  Priority:-1 extents:1 across:1007992k
[17179609.328000] EXT3 FS on hda4, internal journal
[17179609.744000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179610.896000] cdrom: open failed.
[17179668.832000] kjournald starting.  Commit interval 5 seconds
[17179668.832000] EXT3 FS on hda1, internal journal
[17179668.832000] EXT3-fs: mounted filesystem with ordered data mode.
[17179668.884000] kjournald starting.  Commit interval 5 seconds
[17179668.884000] EXT3 FS on hda2, internal journal
[17179668.884000] EXT3-fs: mounted filesystem with ordered data mode.
[17179671.532000] ACPI: AC Adapter [ACAD] (off-line)
[17179671.568000] ACPI: Battery Slot [BAT0] (battery present)
[17179671.764000] ACPI: Power Button (FF) [PWRF]
[17179671.764000] ACPI: Lid Switch [LID]
[17179671.764000] ACPI: Power Button (CM) [PWRB]
[17179672.000000] ibm_acpi: ec object not found
[17179672.064000] pcc_acpi: loading...
[17179672.828000] cpufreq: change failed with new_state 2 and result 0
[17179672.828000] cpufreq: change failed with new_state 2 and result 0
[17179682.860000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179682.860000] apm: overridden by ACPI.
[17179694.784000] Bluetooth: Core ver 2.8
[17179694.784000] NET: Registered protocol family 31
[17179694.784000] Bluetooth: HCI device and connection manager initialized
[17179694.784000] Bluetooth: HCI socket layer initialized
[17179694.812000] Bluetooth: L2CAP ver 2.8
[17179694.812000] Bluetooth: L2CAP socket layer initialized
[17179694.904000] Bluetooth: HIDP (Human Interface Emulation) ver 1.1-mh1
[17179694.996000] Bluetooth: RFCOMM socket layer initialized
[17179694.996000] Bluetooth: RFCOMM TTY layer initialized
[17179694.996000] Bluetooth: RFCOMM ver 1.7
[17179698.088000] NET: Registered protocol family 17
[17179704.128000] NET: Registered protocol family 10
[17179704.128000] lo: Disabled Privacy Extensions
[17179704.128000] IPv6 over IPv4 tunneling driver
[17179714.640000] eth1: no IPv6 routers present
[17179730.576000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.

```

dmesg when sound is not working:
```

[17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Fri Sep 8 19:55:17 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e9400 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000000fff0000 - 000000000ffffc00 (ACPI data)
[17179569.184000]  BIOS-e820: 000000000ffffc00 - 0000000010000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 255MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 65520
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 61424 pages, LIFO batch:15
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 FIC                                   ) @ 0x000f6bc0
[17179569.184000] ACPI: RSDT (v001 FIC    ND000030 0x00000001 FIC  0x00000000) @ 0x0fffb152
[17179569.184000] ACPI: FADT (v001 FIC    ND000030 0x00000001 FACP 0x000f4240) @ 0x0ffffb64
[17179569.184000] ACPI: BOOT (v001 FIC    ND000030 0x00000001 FIC  0x00000001) @ 0x0ffffbd8
[17179569.184000] ACPI: DSDT (v001    FIC ND000030 0x00000001 MSFT 0x0100000b) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 10000000:eff80000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda4
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01201000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[17179569.184000] Detected 699.648 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.668000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.668000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179569.696000] Memory: 249140k/262080k available (1976k kernel code, 12356k reserved, 606k data, 288k init, 0k highmem)
[17179569.696000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.776000] Calibrating delay using timer specific routine.. 1400.37 BogoMIPS (lpj=2800745)
[17179569.776000] Security Framework v1.0.0 initialized
[17179569.776000] SELinux:  Disabled at boot.
[17179569.776000] Mount-cache hash table entries: 512
[17179569.776000] CPU: After generic identify, caps: 0387f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179569.776000] CPU: After vendor identify, caps: 0387f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179569.776000] CPU: L1 I cache: 16K, L1 D cache: 16K
[17179569.776000] CPU: L2 cache: 256K
[17179569.776000] CPU serial number disabled.
[17179569.776000] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[17179569.776000] mtrr: v2.0 (20020519)
[17179569.776000] CPU: Intel Pentium III (Coppermine) stepping 0a
[17179569.776000] Enabling fast FPU save and restore... done.
[17179569.776000] Enabling unmasked SIMD FPU exception support... done.
[17179569.776000] Checking 'hlt' instruction... OK.
[17179569.792000] checking if image is initramfs... it is
[17179571.940000] Freeing initrd memory: 6616k freed
[17179571.980000] ACPI: Looking for DSDT ... not found!
[17179571.984000] ACPI: setting ELCR to 0200 (from 0020)
[17179571.992000] NET: Registered protocol family 16
[17179571.992000] EISA bus registered
[17179571.992000] ACPI: bus type pci registered
[17179571.996000] PCI: PCI BIOS revision 2.10 entry at 0xfd9ae, last bus=1
[17179571.996000] PCI: Using configuration type 1
[17179571.996000] ACPI: Subsystem revision 20051216
[17179572.004000] ACPI: Interpreter enabled
[17179572.004000] ACPI: Using PIC for interrupt routing
[17179572.008000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179572.008000] PCI: Probing PCI hardware (bus 00)
[17179572.012000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179572.016000] PCI quirk: region 1000-103f claimed by PIIX4 ACPI
[17179572.016000] PCI quirk: region 1040-104f claimed by PIIX4 SMB
[17179572.016000] PIIX4 devres C PIO at 0068-006f
[17179572.020000] Boot video device is 0000:01:00.0
[17179572.020000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179572.024000] ACPI: PCI Interrupt Link [LNKA] (IRQs 10) *0, disabled.
[17179572.024000] ACPI: PCI Interrupt Link [LNKB] (IRQs 10) *0, disabled.
[17179572.028000] ACPI: PCI Interrupt Link [LNKC] (IRQs *5)
[17179572.028000] ACPI: PCI Interrupt Link [LNKD] (IRQs 5) *0, disabled.
[17179572.032000] ACPI: Power Resource [PUSB] (off)
[17179572.032000] ACPI: Power Resource [PFAN] (on)
[17179572.032000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179572.032000] pnp: PnP ACPI init
[17179572.044000] pnp: PnP ACPI: found 12 devices
[17179572.044000] PnPBIOS: Disabled by ACPI PNP
[17179572.044000] PCI: Using ACPI for IRQ routing
[17179572.044000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179572.044000] pnp: 00:04: ioport range 0x1000-0x104f could not be reserved
[17179572.044000] pnp: 00:04: ioport range 0xfe00-0xfe01 has been reserved
[17179572.048000] PCI: Bridge: 0000:00:01.0
[17179572.048000]   IO window: 2000-2fff
[17179572.048000]   MEM window: fc100000-fdffffff
[17179572.048000]   PREFETCH window: 28000000-280fffff
[17179572.048000] PCI: Bus 2, cardbus bridge: 0000:00:0c.0
[17179572.048000]   IO window: 00003000-000030ff
[17179572.048000]   IO window: 00003400-000034ff
[17179572.048000]   PREFETCH window: 20000000-21ffffff
[17179572.048000]   MEM window: 22000000-23ffffff
[17179572.048000] PCI: Bus 6, cardbus bridge: 0000:00:0c.1
[17179572.048000]   IO window: 00003800-000038ff
[17179572.048000]   IO window: 00003c00-00003cff
[17179572.048000]   PREFETCH window: 24000000-25ffffff
[17179572.048000]   MEM window: 26000000-27ffffff
[17179572.048000] **** SET: Misaligned resource pointer: ce9f75e2 Type 07 Len 0
[17179572.048000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[17179572.048000] PCI: setting IRQ 10 as level-triggered
[17179572.048000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[17179572.048000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[17179572.048000] ACPI: PCI Interrupt 0000:00:0c.1[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[17179572.048000] PCI: Setting latency timer of device 0000:00:0c.1 to 64
[17179572.048000] Simple Boot Flag at 0x38 set to 0x1
[17179572.048000] audit: initializing netlink socket (disabled)
[17179572.048000] audit(1178117554.048:1): initialized
[17179572.048000] VFS: Disk quotas dquot_6.5.1
[17179572.048000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.048000] Initializing Cryptographic API
[17179572.048000] io scheduler noop registered
[17179572.048000] io scheduler anticipatory registered
[17179572.048000] io scheduler deadline registered
[17179572.048000] io scheduler cfq registered
[17179572.052000] Limiting direct PCI/PCI transfers.
[17179572.052000] isapnp: Scanning for PnP cards...
[17179572.404000] isapnp: No Plug & Play device found
[17179572.448000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUS] at 0x60,0x64 irq 1,12
[17179572.448000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179572.448000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179572.448000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179572.448000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179572.448000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179572.448000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179572.448000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179572.448000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.452000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179572.456000] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.456000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179572.456000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179572.456000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179572.460000] mice: PS/2 mouse device common for all mice
[17179572.460000] EISA: Probing bus 0 at eisa.0
[17179572.460000] Cannot allocate resource for EISA slot 1
[17179572.460000] Cannot allocate resource for EISA slot 2
[17179572.460000] Cannot allocate resource for EISA slot 3
[17179572.460000] EISA: Detected 0 cards.
[17179572.460000] NET: Registered protocol family 2
[17179572.496000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179572.496000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[17179572.496000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[17179572.496000] TCP: Hash tables configured (established 16384 bind 16384)
[17179572.496000] TCP reno registered
[17179572.496000] TCP bic registered
[17179572.496000] NET: Registered protocol family 1
[17179572.496000] NET: Registered protocol family 8
[17179572.496000] NET: Registered protocol family 20
[17179572.496000] Using IPI Shortcut mode
[17179572.496000] ACPI wakeup devices: 
[17179572.496000]  LID COM1 MPC1 MPC2 
[17179572.496000] ACPI: (supports S0 S3 S4 S5)
[17179572.496000] Freeing unused kernel memory: 288k freed
[17179572.628000] Capability LSM initialized
[17179572.716000] ACPI: Fan [FAN] (on)
[17179572.724000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179572.724000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179572.732000] ACPI: Thermal Zone [THRM] (30 C)
[17179573.068000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.868000] PIIX4: IDE controller at PCI slot 0000:00:07.1
[17179573.868000] PIIX4: chipset revision 1
[17179573.868000] PIIX4: not 100% native mode: will probe irqs later
[17179573.868000]     ide0: BM-DMA at 0x1050-0x1057, BIOS settings: hda:DMA, hdb:pio
[17179573.868000]     ide1: BM-DMA at 0x1058-0x105f, BIOS settings: hdc:pio, hdd:pio
[17179573.868000] Probing IDE interface ide0...
[17179574.156000] hda: HITACHI_DK23CA-20, ATA DISK drive
[17179574.828000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.828000] Probing IDE interface ide1...
[17179575.568000] hdc: QSI DVD-ROM SDR-081, ATAPI CD/DVD-ROM drive
[17179576.240000] ide1 at 0x170-0x177,0x376 on irq 15
[17179576.256000] hda: max request size: 128KiB
[17179576.280000] hda: 39070080 sectors (20003 MB) w/2048KiB Cache, CHS=38760/16/63, UDMA(33)
[17179576.280000] hda: cache flushes not supported
[17179576.280000]  hda: hda1 hda2 hda3 hda4
[17179576.316000] hdc: ATAPI 24X DVD-ROM drive, 512kB Cache, DMA
[17179576.316000] Uniform CD-ROM driver Revision: 3.20
[17179576.756000] usbcore: registered new driver usbfs
[17179576.756000] usbcore: registered new driver hub
[17179576.764000] USB Universal Host Controller Interface driver v2.3
[17179576.764000] PCI: Enabling device 0000:00:07.2 (0000 -> 0001)
[17179576.764000] **** SET: Misaligned resource pointer: cfd2b7e2 Type 07 Len 0
[17179576.764000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
[17179576.764000] PCI: setting IRQ 5 as level-triggered
[17179576.764000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[17179576.764000] uhci_hcd 0000:00:07.2: UHCI Host Controller
[17179576.764000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[17179576.768000] uhci_hcd 0000:00:07.2: irq 5, io base 0x00001060
[17179576.768000] hub 1-0:1.0: USB hub found
[17179576.768000] hub 1-0:1.0: 2 ports detected
[17179577.012000] Attempting manual resume
[17179577.064000] EXT3-fs: mounted filesystem with ordered data mode.
[17179577.092000] kjournald starting.  Commit interval 5 seconds
[17179577.112000] usb 1-2: new full speed USB device using uhci_hcd and address 2
[17179600.612000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179600.620000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179600.656000] Linux agpgart interface v0.101 (c) Dave Jones
[17179600.664000] agpgart: Detected an Intel 440BX Chipset.
[17179600.668000] agpgart: AGP aperture is 64M @ 0xf8000000
[17179600.688000] 8139too Fast Ethernet driver 0.9.27
[17179600.688000] PCI: Enabling device 0000:00:09.0 (0000 -> 0003)
[17179600.688000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[17179600.688000] eth0: RealTek RTL8139 at 0xd0892000, 00:30:54:00:2f:41, IRQ 10
[17179600.688000] eth0:  Identified 8139 chip type 'RTL-8139C'
[17179600.732000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179601.468000] Real Time Clock Driver v1.12
[17179601.964000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[17179601.964000] Yenta: CardBus bridge found at 0000:00:0c.0 [1509:1760]
[17179601.964000] Yenta: Enabling burst memory read transactions
[17179601.964000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179601.964000] Yenta: Routing CardBus interrupts to PCI
[17179601.964000] Yenta TI: socket 0000:00:0c.0, mfunc 0x010c1022, devctl 0x64
[17179602.284000] Yenta: ISA IRQ mask 0x0898, PCI irq 10
[17179602.284000] Socket status: 30000006
[17179602.572000] ACPI: PCI Interrupt 0000:00:0c.1[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[17179602.572000] Yenta: CardBus bridge found at 0000:00:0c.1 [1509:1760]
[17179602.572000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179602.572000] Yenta: Routing CardBus interrupts to PCI
[17179602.572000] Yenta TI: socket 0000:00:0c.1, mfunc 0x010c1022, devctl 0x64
[17179602.656000] irda_init()
[17179602.656000] NET: Registered protocol family 23
[17179602.828000] Yenta: ISA IRQ mask 0x0898, PCI irq 10
[17179602.828000] Socket status: 30000006
[17179602.916000] **** SET: Misaligned resource pointer: ca113c22 Type 07 Len 0
[17179602.916000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
[17179602.916000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[17179602.916000] maestro3: enabled hack for 'LEGEND ZhaoYang 3100CF'
[17179603.140000] Floppy drive(s): fd0 is 1.44M
[17179603.156000] FDC 0 is a post-1991 82077
[17179603.460000] input: PC Speaker as /class/input/input1
[17179603.548000] Synaptics Touchpad, model: 1, fw: 5.6, id: 0x9244b1, caps: 0x80471b/0x0
[17179603.584000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[17179603.584000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17179603.888000] parport: PnPBIOS parport detected.
[17179603.888000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[17179603.964000] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[17179604.160000] ts: Compaq touchscreen protocol output
[17179604.316000] eth1: register 'cdc_ether' at usb-0000:00:07.2-2, CDC Ethernet Device, 00:15:0c:3b:b6:32
[17179604.316000] usbcore: registered new driver cdc_ether
[17179604.504000] cs: IO port probe 0x100-0x3af: excluding 0x200-0x207
[17179604.508000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179604.508000] cs: IO port probe 0x820-0x8ff: clean.
[17179604.512000] cs: IO port probe 0xc00-0xcf7: clean.
[17179604.512000] cs: IO port probe 0xa00-0xaff: clean.
[17179604.736000] cs: IO port probe 0x100-0x3af: excluding 0x200-0x207
[17179604.740000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179604.740000] cs: IO port probe 0x820-0x8ff: clean.
[17179604.740000] cs: IO port probe 0xc00-0xcf7: clean.
[17179604.744000] cs: IO port probe 0xa00-0xaff: clean.
[17179605.252000] lp0: using parport0 (interrupt-driven).
[17179605.488000] Adding 1007992k swap on /dev/disk/by-uuid/da8270ba-b9bd-4ce5-bdbc-c1dfde05e69e.  Priority:-1 extents:1 across:1007992k
[17179605.616000] EXT3 FS on hda4, internal journal
[17179606.048000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179607.212000] cdrom: open failed.
[17179607.824000] kjournald starting.  Commit interval 5 seconds
[17179607.824000] EXT3 FS on hda1, internal journal
[17179607.824000] EXT3-fs: mounted filesystem with ordered data mode.
[17179607.876000] kjournald starting.  Commit interval 5 seconds
[17179607.876000] EXT3 FS on hda2, internal journal
[17179607.876000] EXT3-fs: mounted filesystem with ordered data mode.
[17179610.628000] ACPI: AC Adapter [ACAD] (on-line)
[17179610.856000] ACPI: Battery Slot [BAT0] (battery present)
[17179611.220000] ACPI: Power Button (FF) [PWRF]
[17179611.220000] ACPI: Lid Switch [LID]
[17179611.220000] ACPI: Power Button (CM) [PWRB]
[17179611.456000] ibm_acpi: ec object not found
[17179611.520000] pcc_acpi: loading...
[17179612.292000] cpufreq: change failed with new_state 2 and result 0
[17179612.292000] cpufreq: change failed with new_state 2 and result 0
[17179622.108000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179622.108000] apm: overridden by ACPI.
[17179634.216000] Bluetooth: Core ver 2.8
[17179634.216000] NET: Registered protocol family 31
[17179634.216000] Bluetooth: HCI device and connection manager initialized
[17179634.216000] Bluetooth: HCI socket layer initialized
[17179634.244000] Bluetooth: L2CAP ver 2.8
[17179634.244000] Bluetooth: L2CAP socket layer initialized
[17179634.336000] Bluetooth: HIDP (Human Interface Emulation) ver 1.1-mh1
[17179634.428000] Bluetooth: RFCOMM socket layer initialized
[17179634.428000] Bluetooth: RFCOMM TTY layer initialized
[17179634.428000] Bluetooth: RFCOMM ver 1.7
[17179638.336000] NET: Registered protocol family 17
[17179638.864000] NET: Registered protocol family 10
[17179638.864000] lo: Disabled Privacy Extensions
[17179638.864000] IPv6 over IPv4 tunneling driver
[17179649.792000] eth1: no IPv6 routers present
[17179666.980000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[17188932.984000] usb 1-1: new full speed USB device using uhci_hcd and address 3
[17188934.924000] SCSI subsystem initialized
[17188935.036000] Initializing USB Mass Storage driver...
[17188935.036000] scsi0 : SCSI emulation for USB Mass Storage devices
[17188935.036000] usb-storage: device found at 3
[17188935.040000] usb-storage: waiting for device to settle before scanning
[17188935.040000] usbcore: registered new driver usb-storage
[17188935.040000] USB Mass Storage support registered.
[17188943.444000]   Vendor: HDT72252  Model: 5DLAT80           Rev: V44O
[17188943.444000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17188943.456000] usb-storage: device scan complete
[17188943.628000] Driver 'sd' needs updating - please use bus_type methods
[17188943.636000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[17188943.636000] sda: assuming drive cache: write through
[17188943.640000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[17188943.640000] sda: assuming drive cache: write through
[17188943.640000]  sda: sda1 sda2 sda3 < sda5 >
[17188943.712000] sd 0:0:0:0: Attached scsi disk sda
[17188943.740000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17188948.108000] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[17188948.108000] kjournald starting.  Commit interval 5 seconds
[17188948.116000] EXT3 FS on sda2, internal journal
[17188948.116000] EXT3-fs: mounted filesystem with ordered data mode.
[17188949.500000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17189038.940000] cdrom: open failed.
[17189038.980000] cdrom: open failed.

```

---

### Post by sudo_nym on 2007-05-02
Weird...  I notice it loads the maestro3 module even when sound fails, so why is it not reaching your speakers sometimes?

I've never seen those `Misaligned resource pointer' warnings before either, wonder what they're about...

Sorry.  I'd like to be more helpful.

Just wondered; do you have XMMS installed?  [That's the X Multi-Media System, by the way; an MP3 player.]  I only ask because if sound is disabled, XMMS will refuse to start, and I do wonder if your system *thinks* the sound-card's working properly, even when it's not.

But that's only a question, and probably not a helpful one.  I just wonderd.



Still wish you luck though,

Patrick.

---

### Post by Senti on 2007-05-04
xmms said something like:
could not open Audio
Please check that:
the soundcard is proper configured, the correct audio-plugin is choosed and no other Programm the soundcard blocks.

I could imagine that something (programm maybe) is simply bloking the soundcard, how can i check that?

---

### Post by sudo_nym on 2007-05-04
> **Senti said:**
> xmms said something like:
could not open Audio
Please check that:
the soundcard is proper configured, the correct audio-plugin is choosed and no other Programm the soundcard blocks.

I could imagine that something (programm maybe) is simply bloking the soundcard, how can i check that?

I think it just means the sound-card isn't working, and your system *knows* it's not working.  If XMMS happily processed an audio file, without actually making any sound that would be different.

I only asked out of curiosity.  Hope you didn't install it just to find that out.  It's a nice little audio player, but maybe you already have one you like better.

It would mention other applications as a possible cause, because only one program can use the sound-card at any given time [some mixers might handle this better, but that's been my experience].  For example, I have to stop XMMS playback before viewing an MPG with sound in Xfmedia, or editing a .wav in Audacity.  [Actually, I think Audacity would allow editing, I just wouldn't be able to hear the results until later.]

Sorry, but the best suggestion I can offer right now is, if sound fails on one boot, try a reboot.  Yes, I know that's what you were doing before, but it does work most of the time, right?

It might not be that bad either.  I usually go for several days between reboots, and favour hibernation over shutdown when I need to take the machine with me somewhere.



Good luck though,

Patrick.

---

### Post by Senti on 2007-05-22
okay there is something new:
when i have no wsound and turn the master volume on mute i have suddently sound the volume is very low, but i hear something.

---

