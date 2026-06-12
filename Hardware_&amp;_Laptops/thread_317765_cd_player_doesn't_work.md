---
title: "cd player doesn't work"
date: 2006-12-12
forum: Hardware &amp; Laptops
---

### Post by Nopposan on 2006-12-12
I have this problem with the cdrom.  I can't access it properly.

Details: I'm running Xubuntu 6.06 (after switching from 6.10 as per taurus' advice) on the Compaq Armada 7750MT with 166MHz pentium processor and 128MB RAM.  This machine was doing a good job running Xfce over SuSE 10.0, but I decided to give Xubuntu a try since SuSE 10.0 just didn't provide the same level of software choice for the slower computer, because SuSE 10.1 and 10.2 have buggy issues with installation, and 'cause I tried Kubuntu on another machine and liked it.

Anyway, here's the message I get when I try to mount the cdrom:
nopposan@supertux:/media$ sudo mount cdrom
mount: block device /dev/hdb is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdb,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


And here's my dmesg > bootmessages.txt (I added some options to the boot kernel command; noapic nolapic acpi=off):

[17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e801: 0000000000000000 - 000000000009f000 (usable)
[17179569.184000]  BIOS-e801: 0000000000100000 - 0000000009000000 (usable)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 144MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 36864
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 32768 pages, LIFO batch:7
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI not present.
[17179569.184000] Allocating PCI resources starting at 10000000 (gap: 09000000:f7000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash noapic noalapic acpi=off pnpbios=off
[17179569.184000] No local APIC present or hardware disabled
[17179569.184000] mapped APIC to ffffd000 (01121000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[    0.000000] Detected 166.606 MHz processor.
[ 2383.459042] Using tsc for high-res timesource
[ 2383.461115] Console: colour VGA+ 80x25
[ 2383.465734] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 2383.469409] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[ 2383.524001] Memory: 135660k/147456k available (1976k kernel code, 11268k reserved, 606k data, 288k init, 0k highmem)
[ 2383.524061] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[ 2383.603665] Calibrating delay using timer specific routine.. 333.64 BogoMIPS (lpj=667292)
[ 2383.604113] Security Framework v1.0.0 initialized
[ 2383.604190] SELinux:  Disabled at boot.
[ 2383.604356] Mount-cache hash table entries: 512
[ 2383.605839] CPU: After generic identify, caps: 008001bf 00000000 00000000 00000000 00000000 00000000 00000000
[ 2383.605937] CPU: After vendor identify, caps: 008001bf 00000000 00000000 00000000 00000000 00000000 00000000
[ 2383.606020] Intel Pentium with F0 0F bug - workaround enabled.
[ 2383.606063] CPU: After all inits, caps: 008001bf 00000000 00000000 00000000 00000000 00000000 00000000
[ 2383.606305] mtrr: v2.0 (20020519)
[ 2383.606328] CPU: Intel Pentium MMX stepping 03
[ 2383.606378] Checking 'hlt' instruction... OK.
[ 2383.621242] checking if image is initramfs... it is
[ 2392.691748] Freeing initrd memory: 6616k freed
[ 2392.906970] NET: Registered protocol family 16
[ 2392.907483] EISA bus registered
[ 2392.922087] PCI: PCI BIOS revision 2.10 entry at 0xf740d, last bus=0
[ 2392.922158] PCI: Using configuration type 1
[ 2392.925832] ACPI: Subsystem revision 20051216
[ 2392.925869] ACPI: Interpreter disabled.
[ 2392.925906] Linux Plug and Play Support v0.97 (c) Adam Belay
[ 2392.926163] pnp: PnP ACPI: disabled
[ 2392.926194] PnPBIOS: Disabled
[ 2392.926351] PCI: Probing PCI hardware
[ 2392.926389] PCI: Probing PCI hardware (bus 00)
[ 2392.927246] PCI: device 0000:00:00.0 has unknown header type 7f, ignoring.
[ 2392.927680] Boot video device is 0000:00:0d.0
[ 2392.927909] PCI: Ignoring BAR0-3 of IDE controller 0000:00:0e.1
[ 2392.966527] PCI: Bus 1, cardbus bridge: 0000:00:0c.0
[ 2392.966574]   IO window: 00001000-000010ff
[ 2392.966616]   IO window: 00001400-000014ff
[ 2392.966653]   PREFETCH window: 10000000-11ffffff
[ 2392.966693]   MEM window: 12000000-13ffffff
[ 2392.966727] PCI: Bus 5, cardbus bridge: 0000:00:0c.1
[ 2392.966800]   IO window: 00001800-000018ff
[ 2392.966836]   IO window: 00001c00-00001cff
[ 2392.966873]   PREFETCH window: 14000000-15ffffff
[ 2392.966913]   MEM window: 16000000-17ffffff
[ 2392.974435] audit: initializing netlink socket (disabled)
[ 2392.974558] audit(1166280512.565:1): initialized
[ 2392.976000] VFS: Disk quotas dquot_6.5.1
[ 2392.976306] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 2392.977049] Initializing Cryptographic API
[ 2392.977119] io scheduler noop registered
[ 2392.977186] io scheduler anticipatory registered
[ 2392.977262] io scheduler deadline registered
[ 2392.977371] io scheduler cfq registered
[ 2392.979676] isapnp: Scanning for PnP cards...
[ 2393.333512] isapnp: No Plug & Play device found
[ 2393.619441] PNP: No PS/2 controller found. Probing ports directly.
[ 2393.624705] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 2393.625528] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 2393.626221] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[ 2393.627261] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 2393.628199] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[ 2393.629002] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[ 2393.667391] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[ 2393.668119] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[ 2393.668177] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[ 2393.670146] mice: PS/2 mouse device common for all mice
[ 2393.672445] EISA: Probing bus 0 at eisa.0
[ 2393.672519] Cannot allocate resource for EISA slot 1
[ 2393.672672] EISA: Detected 0 cards.
[ 2393.673206] NET: Registered protocol family 2
[ 2393.709908] input: AT Translated Set 2 keyboard as /class/input/input0
[ 2393.711434] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[ 2393.713493] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[ 2393.714420] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[ 2393.715410] TCP: Hash tables configured (established 8192 bind 8192)
[ 2393.715452] TCP reno registered
[ 2393.716582] TCP bic registered
[ 2393.716665] NET: Registered protocol family 1
[ 2393.716745] NET: Registered protocol family 8
[ 2393.716778] NET: Registered protocol family 20
[ 2393.717014] Using IPI Shortcut mode
[ 2393.717492] Freeing unused kernel memory: 288k freed
[ 2394.466265] vga16fb: initializing
[ 2394.466340] vga16fb: mapped to 0xc00a0000
[ 2394.604238] Console: switching to colour frame buffer device 80x25
[ 2394.604339] fb0: VGA16 VGA frame buffer device
[ 2396.019761] Capability LSM initialized
[ 2403.053721] TRIFLEX: IDE controller at PCI slot 0000:00:0e.1
[ 2403.053931] TRIFLEX: chipset revision 3
[ 2403.053963] TRIFLEX: not 100% native mode: will probe irqs later
[ 2403.054036]     ide0: BM-DMA at 0xb140-0xb147, BIOS settings: hda:DMA, hdb:DMA
[ 2403.054180] Probing IDE interface ide0...
[ 2403.469933] hda: FUJITSU MHK2048AT, ATA DISK drive
[ 2403.917867] hdb: COMPAQ CRD-S311, ATAPI CD/DVD-ROM drive
[ 2403.975895] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[ 2404.062330] hda: max request size: 128KiB
[ 2404.149595] hda: 9514260 sectors (4871 MB) w/512KiB Cache, CHS=10068/15/63, (U)DMA
[ 2404.149716] hda: cache flushes not supported
[ 2404.151502]  hda: hda1 hda2 < hda5 >
[ 2404.266734] hdb: ATAPI 8X CD-ROM drive, 256kB Cache, DMA
[ 2404.266817] Uniform CD-ROM driver Revision: 3.20
[ 2405.273364] Probing IDE interface ide1...
[ 2406.133345] Attempting manual resume
[ 2406.361976] EXT3-fs: mounted filesystem with ordered data mode.
[ 2406.385713] kjournald starting.  Commit interval 5 seconds
[ 2441.828374] Yenta: CardBus bridge found at 0000:00:0c.0 [0e11:b046]
[ 2441.954884] Yenta: ISA IRQ mask 0x0698, PCI irq 11
[ 2441.954933] Socket status: 30000059
[ 2441.957412] Yenta: CardBus bridge found at 0000:00:0c.1 [0e11:b046]
[ 2442.082903] Yenta: ISA IRQ mask 0x0698, PCI irq 11
[ 2442.082951] Socket status: 30000019
[ 2442.589920] pccard: PCMCIA card inserted into slot 0
[ 2442.917890] pccard: PCMCIA card inserted into slot 1
[ 2444.528268] cs: IO port probe 0x100-0x3af: excluding 0x100-0x107 0x220-0x22f 0x250-0x257 0x270-0x277 0x330-0x337 0x378-0x37f 0x388-0x38f
[ 2444.532029] cs: IO port probe 0x3e0-0x4ff: excluding 0x408-0x40f 0x4d0-0x4d7
[ 2444.533983] cs: IO port probe 0x820-0x8ff: excluding 0x820-0x83f 0x850-0x87f
[ 2444.535424] cs: IO port probe 0xc00-0xcf7: excluding 0xc48-0xc4f 0xc68-0xc6f
[ 2444.538687] cs: IO port probe 0xa00-0xaff: clean.
[ 2444.540415] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[ 2444.548937] pcmcia: registering new device pcmcia0.0
[ 2446.005375] cs: IO port probe 0x100-0x3af: excluding 0x100-0x107 0x220-0x22f 0x250-0x257 0x270-0x277 0x330-0x337 0x378-0x37f 0x388-0x38f
[ 2446.008958] cs: IO port probe 0x3e0-0x4ff: excluding 0x408-0x40f 0x4d0-0x4d7
[ 2446.010785] cs: IO port probe 0x820-0x8ff: excluding 0x820-0x83f 0x850-0x87f
[ 2446.012196] cs: IO port probe 0xc00-0xcf7: excluding 0xc48-0xc4f 0xc68-0xc6f
[ 2446.015449] cs: IO port probe 0xa00-0xaff: clean.
[ 2446.017182] cs: memory probe 0xa0000000-0xa0ffffff: excluding 0xa0000000-0xa00fffff
[ 2446.023112] pcmcia: registering new device pcmcia1.0
[ 2446.543947] input: PS/2 Generic Mouse as /class/input/input1
[ 2446.835659] Probing IDE interface ide1...
[ 2447.121720] hdc: 5in1 Adapter, CFA DISK drive
[ 2447.576844] ts: Compaq touchscreen protocol output
[ 2450.553350] ide1 at 0x110-0x117,0x11e on irq 3
[ 2450.555337] hdc: max request size: 128KiB
[ 2450.555391] hdc: 29120 sectors (14 MB) w/1KiB Cache, CHS=455/2/32
[ 2450.555445] hdc: cache flushes not supported
[ 2450.556812]  hdc: hdc1
[ 2450.568620] ide-cs: hdc: Vcc = 3.3, Vpp = 0.0
[ 2450.637723] eth0: NE2000 (DL10022 rev 30): io 0x300, irq 4, hw_addr 00:05:5D:27:97:6B
[ 2453.012636] NET: Registered protocol family 17
[ 2453.794589] parport0: PC-style at 0x378 [PCSPP,TRISTATE,EPP]
[ 2453.809461] eth0: found link beat
[ 2453.809520] eth0: autonegotiation complete: 100baseT-FD selected
[ 2453.899087] lp0: using parport0 (polling).
[ 2454.680546] Adding 232900k swap on /dev/hda5.  Priority:-1 extents:1 across:232900k
[ 2455.198050] EXT3 FS on hda1, internal journal
[ 2456.700051] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[ 2456.700104] md: bitmap version 4.39
[ 2460.126778] NET: Registered protocol family 10
[ 2460.128648] lo: Disabled Privacy Extensions
[ 2460.130932] IPv6 over IPv4 tunneling driver
[ 2460.458426] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[ 2462.397197] cdrom: open failed.
[ 2470.523180] eth0: no IPv6 routers present
[ 2503.037856] ppdev: user-space parallel port driver
[ 2505.160069] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[ 2519.380778] hdb: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[ 2519.380853] hdb: drive_cmd: error=0x04 { AbortedCommand }
[ 2519.380892] ide: failed opcode was: 0xec
[ 2948.643714] hdb: packet command error: status=0x51 { DriveReady SeekComplete Error }
DELETED REPEATED ERRORS
[ 2972.067520] hdb: packet command error: status=0x51 { DriveReady SeekComplete Error }
[ 2972.067602] hdb: packet command error: error=0x50 { LastFailedSense=0x05 }
[ 2972.067648] ide: failed opcode was: unknown

I'm sure the problem has something to do with all those repeated "failed opcode was: unknown" messages.  'Could it have something to do with the 
"[ 2392.927246] PCI: device 0000:00:00.0 has unknown header type 7f, ignoring."?

BTW, the drive bay my cdrom is in can also take a floppy drive instead. I've got the cdrom installed though, and that's how I installed Xubuntu; I mean I installed from the cdrom, hdb.

Thanks for any help you can give; 'don't really know whether that last bit is relevant.  For what it's worth, I believe this problem is solvable 'cause SuSE 10.0 recognized and ran the cdrom without a hitch.

Please help.  What should I do?  I really don't want to switch distros and reinstall again but I'm more than willing to tweak and tweak.

Thanks.

---

### Post by Nopposan on 2006-12-12
Deleted self-reply.

---

### Post by Nopposan on 2006-12-15
Deleted self-reply.

---

### Post by Nopposan on 2006-12-17
O.K., I'm a little embarrassed but I guess I can access the cdrom, I just can't access and play audio cd's.  I'll look for answers elsewhere in the multimedia forum.

'Sorry.

---

### Post by Nopposan on 2006-12-18
Well, after installing all kinds of multimedia software I'm able to play my audio cd's with XMMS.  'Not sure which package did the trick.  Oh well.  Hooray!  I can play audio cd's!

I'll post which packages I've installed.  Maybe that'll help someone in a similar situation.

---

### Post by clubsoda on 2006-12-21
Thanks, this helped me.

Gxine wouldn't play CDs at all with my LG CD-RW drive.  From the menu, File->CD said:-```
Autoplay input plugin ‘CD’ failed
Check engine output for further details.
```Using File->Open and steering it to /dev/hdc I got another error:-```
The xine engine failed to start.
No demuxer found - stream format not recognised.
```

With alsaplayer I got:-```
CDDA: read TOC ioctl failed
```

After seeing this thread I installed xmms and **xmms-cdread**, which worked.

Then I discovered that my /dev/cdrom link was pointing at hdd (the DVD drive) instead of hdc.  *Mystery*  Having fixed that, I can now play CDs with all of the above applications.  Notice how useless the error messages are in cases like this.

CD-RW burning is still broken, though.

---

### Post by clubsoda on 2007-01-06
Briefly, for anyone else who may find this thread, it seems "File->Open MRL" is not the correct way to steer gxine to a CD device. #-o 

Try this instead:-
File->Configure->Preferences
Click gui tab
Click the blank tab to the left of the post_plugins tab (the tab with no name :))
Set the experience_level to anything other than "Beginner"
Click media tab
Click audio_cd tab on the second line (Note: this tab doesn't appear in "Beginner" mode)
Enter the desired device path in the "device" field, eg: /dev/hdc for the primary device on the secondary IDE channel.

After that you should be able to play audio CDs by selecting File->CD.

The above procedure would not be necessary if the default path (i.e. /dev/cdrom) already pointed to your preferred CD device (but if that were the case you probably wouldn't be reading this ;)).  Fixing the symlink requires some expertise with udev.  [This thread](http://www.ubuntuforums.org/showthread.php?t=323742) may help with that.

Good luck.

---

### Post by Nopposan on 2007-01-06
Thanks for all of the information.  I've been neglecting this thread, I apologize.  If I knew a way to print all of my multimedia related applications and libraries I've installed to a file then I'd post them.  'Sorry, but I haven't learned that yet.

Anyway, I'm glad my rantings have been a springboard for someone's solving their problems.

Cheers.

---

